---
layout: post
title: Amazon Friend Feedback
date: '2010-12-05T12:20:00.000-10:00'
author: Christopher Slade
description: Have you ever searched for a product on Amazon, read the reviews and got mixed feelings about weather you should buy it or not.  Did you want to ask your friends opinion?  Well, now you can ask your Facebook friends without ever leaving Amazon.
tags:
- amazon
- dacebook
- kynetx
- technology
- web augmentation
modified_time: '2011-10-21T21:44:36.646-10:00'
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-4871867676715592364
blogger_orig_url: https://www.christopherslade.com/2010/12/amazon-friend-feedback.html
redirect_from: /2010/12/amazon-friend-feedback.html
---

Have you ever searched for a product on Amazon, read the reviews and got mixed feelings about whether you should buy it or not?  Did you want to ask your friend's opinion?  Well, now you can ask your Facebook friends without ever leaving Amazon.

For Kynetx's web augmentation contest, I decided to add a Get Friend Feedback button on every product on Amazon.com.  It shows up right above the customer reviews.  To get feedback from your friends, you can press the button, and it will let you type in a message that you can post to your Facebook wall, with a link to the product you are viewing.  When you visit the product again, it will display the comments and likes count that your friends have posted.

If I ever find the time, I would like to add an option to Tweet the product to get feedback on Twitter. I would like to get the friend comments to show up in the shopping cart, and put the button on other shopping sites like Google Products.

If you want to try it out, just install the browser plugin for your browser.  You will be prompted to go to Facebook and give my application permission to post things to your wall.  You can also get the app from Kynetx's marketplace.


[Firefox Extension](http://www.christopherslade.com/ProductFriendFeedback.xpi)
[Chrome Extension](http://www.christopherslade.com/ProductFriendFeedback.crx)
[Internet Explorer Extension](http://www.christopherslade.com/ProductFriendFeedback_Setup.exe)

So here are the technical details on how I accomplished it with Kynetx.  The place_button rule grabs the Amazon product id from the URL and the product name from the title and places a button on the page above the customer reviews. Under all of my tests, Amazon uses two different URLs so this rule responds to both of them.

The place_form rule gets launched when the user clicks on the button, created in the previous rule.  It pops up a notify box with a textbox to enter your question.

The request_posted rule gets launched when the user submits the question, and it posts the query to the user's Facebook wall.

The recent_post rule is fired automatically after the last rule fires.  The facebook:post function doesn't return anything, so I needed a way to get the Facebook post id so I can display the post when the users return to see the product.  I had to query the User's feed and get the last post.  I ran out of time to check to make sure it is the post I posted.  So sometimes it might grab the wrong post to display on Amazon.  Hopefully, Kyntex will update the facebook:post to provide a post id when it returns.  I store the Amazon product id with the Facebook post id by using [trails](http://docs.kynetx.com/docs/Trails).

Then, when the user visits a product on Amazon, I search through the trail in the need_discussion rule.  This rule uses a for-each loop to loop through the trail.  If the page's product id matches a product id in the trail, it launches the place discussion rule.

The place_discussion rule gets the like count and comment count from Facebook and places them on the page below the "Get Friend Feedback" button.  It then launches the place comments rule.

The place_comments rule loops through all of the comments and places each one on the Amazon page.

Here is the full Kynetx code:

<script src="https://gist.github.com/crslade/1305748.js"></script>
