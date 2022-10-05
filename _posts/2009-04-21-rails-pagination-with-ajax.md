---
layout: post
title: Rails Pagination with AJAX
date: '2009-04-21T05:04:00.000-10:00'
author: Christopher Slade
description: When I upgraded to Rails 2.0, I quickly found out that pagination was removed from the rails code base.  In order to get it you have to install a plugin.  After searching on the web I found two possible plugins classic pagination, and will_paginate.  I choose will_paginate because it is more efficient and works directly with the model.
tags:
- rails
- ajax
- pagination
- technology
modified_time: '2011-10-21T10:53:50.517-10:00'
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-2457107915285653078
blogger_orig_url: https://www.christopherslade.com/2009/04/rails-pagination-with-ajax.html
redirect_from: /2009/04/rails-pagination-with-ajax.html
---

When I upgraded to Rails 2.0, I quickly found out that pagination was removed from the rails code base.  In order to get it you have to install a plugin.  After searching on the web I found two possible plugins: classic pagination, and [will_paginate](http://wiki.github.com/mislav/will_paginate).  I choose will_paginate because it is more efficient and works directly with the model.

However, the author suggests not using link_to_remote to implement an "AJAXified" pagination.  Instead, he gives some pretty ugly javascript code that does it.  Since I am using a lot of javascript in other areas of my application, I was really hesitant to go down that path and possibly break my javascript functions.  I see his point, in that not everyone uses the prototype library, but I do.  So I came across [Redline's blog](http://weblog.redlinesoftware.com/2008/1/30/willpaginate-and-remote-links) to change my links to link_to_remote links.  But this violates the other reason the will_paginate's author gives for not using link_to_remote - non-javascript browser support and search engine support.

After looking at the link_to_remote documentation, I found that you can replace the default anchor link location (href="#") with the same URL the ajax call goes to.  This allows non-javascript-enabled browsers and search engines to follow the links.  I just modified Redline's render to add one extra option to set the href.  This is my renderer module in app/helpers/remote_link_renderer.rb:

    class RemoteLinkRenderer < WillPaginate::LinkRenderer
      def prepare(collection, options, template)
        @remote = options.delete(:remote) || {}
        super
      end

    protected
      def page_link(page, text, attributes = {})
        @template.link_to_remote(text, {:url => url_for(page),
              :method => :get}.merge(@remote), :href => url_for(page))
      end
    end

With that, javascript-enabled browsers will use make and use the AJAX calls, and non-javascript-enabled browsers and search engines will use the normal links.  This seems like the cleanest and most DRY way to get pagination with AJAX.