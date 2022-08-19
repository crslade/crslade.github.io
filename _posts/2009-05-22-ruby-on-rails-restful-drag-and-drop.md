---
layout: post
title: Ruby on Rails - RESTful Drag and Drop
date: '2009-05-22T16:33:00.000-10:00'
author: Christopher Slade
tags:
- Drag and Drop
- Rails
- AJAX
- RESTful
- Technology
modified_time: '2011-10-21T10:53:50.526-10:00'
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-3313248225068621469
blogger_orig_url: https://www.christopherslade.com/2009/05/ruby-on-rails-restful-drag-and-drop.html
redirect_from: /2009/05/ruby-on-rails-restful-drag-and-drop.html
---

Ruby on Rails and the script.acul.ous library make drag and drop really easy.  Just by adding one line of code, and you can make anything in your page draggable.  With another line of code, you can make anything receive a draggable element.

However, I struggled in making my drag and drop interface [RESTful](http://en.wikipedia.org/wiki/Representational_State_Transfer), and I also struggled in sending the new coordinates to the server to update the model.  I will first address how I made my drag and drop RESTful and then how I managed to get the right coordinates of the drop.

So here is the setup:  I have list of element on the web page, and then a div tag into which the user can drag one of the listed elements.  Then the user can drag the element around the div as well as drag the element off of the div to remove it.  I want the server to remember what elements have been placed on the div and where they are.  That way the user can re-visit the page and see it like he left it.  These three actions easily fit into RESTful actions:  Dragging an element on will call the create action,  Moving an element will call the update action, and dragging an element off will call the destroy action.

So the problem comes when droppable (or the receiving element) receives the draggable.  You need to know the url of the RESTful action before anything has been dropped.  This isn't a problem for the create action, it is a POST to /draggable_elements (where draggable_element is the model that stores the elements that have been placed on the map with their X and Y coordinates).  However update and delete's url is a PUT or DELETE to /draggable_elements/id respectively.  However you don't know the id until the element has been dropped, and once an element is dropped, an AJAX request is immediatly sent to the specified action with one parameter: the DOM id of the element that is dropped.  You cannot specify the correct action because you don't know the element's id until after it is dropped, and you probably don't want your DOM id's to be just the numerical id of draggable_element.  Also, the AJAX request doesn't contain any information about where the drop occurred.

I first tried to solve this problem with the :with option in the drop_receiving_element call.  This allowed me to add additional parameters like the X and Y, but it didn't allow me to change the action of the AJAX request.  Here is my code in the view using the :with option:

     <%= drop_receiving_element :droppable, :accept => "draggable", :hoverclass  => "hover", :url => draggable_elements_path, :method => :post, :with => "'element_id='+encodeURIComponent(element.id.split('_').last()) +
    '&x='+ encodeURIComponent(Element.getStyle(element,'left')) +  '&y='+ encodeURIComponent(Element.getStyle(element,'top')) ">

I called split('_').last() on the element.id to get the actual id number out of my DOM id of the element that was dragged in.  I set the DOM ids of the draggable elements to item_id where the id is the database id of that element.  split and encodeURIComponent are both javascript methods.

I almost gave up on being RESTful, but then looked into the onDrop option.  With this option I can get the drop_receiving_element to call a javascript function instead of sending an AJAX request when it receives a draggable.  I then created hidden forms on my page, one for create, and an update and delete form for each element already dragged in. This worked out great because I could use the remote_form_for helper methods and just pass them instances of the draggable_elements (with a blank one for the create form).  Now, each form will have the correct action coded into it.  The javascript method just has to tell the right form to submit after updating the values.

(If you want the form to send an AJAX request you need to call form.onsubmit() not form.submit().  form.submit() will send an http request.)

The big payoff to all of this is that it really simplifies the controller code.  In fact, I think the only change from the scaffolding code that you would need to make is to delete the new and edit actions, since you won't be using them. (I didn't use the scaffolding so I am not sure about this.)

I also wanted to send the new X and Y coordinates of the drop.  In the code above, I am sending the element left and top for X and Y.  The problem with that is that the positions are relative to where the draggable element is on the page.  Therefore if the user scrolls the page down, zooms in, etc. the coordinate positions will change.  After searching for a solution, I found out that in order to find the absolute position, you have to recurse through all the parents object and find the offset of each parent item and add them up.  Put it all together, and you have a RESTful drag and drop that stores the absolute coordinates of the draggable elements.

Here is my code:

For enabling the draggable elements:

    <% @items.each do |item| -%>
          <%= draggable_element "item_#{item.id}", :revert => true, :ghosting => true%>
    <% end -%>

My droppable:

    <%= drop_receiving_element :dropDiv, :accept => "draggable", :hoverclass => "hover", :onDrop  => "itemDropped"%>


And my javascript:

    function itemDropped (draggableElement, droppableElement, event){
      form = document.getElementById("new_item");
      form.elements["draggable_element[element_id]"].value = draggableElement.id.split('_').last();
      dropDiv = document.getElementById("dropDiv");
      dropPosition = getPosition(dropDiv);
      draggablePosition = getPosition(draggableElement);
      form.elements["draggable_element[x]"].value = draggablePosition[0] - cmapPosition[0];
      form.elements["draggable_element[y]"].value = draggablePosition[1] - cmapPosition[1];
      form.onsubmit();
    }

    function getPosition (obj){
      var curLeft = 0;
      var curTop = 0;
      do {
        curLeft += obj.offsetLeft;
        curTop += obj.offsetTop;
      } while (obj = obj.offsetParent);
      return [curLeft,curTop]
    }

Notice that the get position adds up all of the parents offsets. This isn't my complete code, it only sends the create form, but hopefully it is enough to get you started.