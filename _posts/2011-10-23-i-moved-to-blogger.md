---
layout: post
title: I Moved to Blogger
date: '2011-10-23T01:44:00.000-10:00'
author: Christopher Slade
description: Since it has been another year, it was time for me to reanalyze how I am hosting this blog. A little while ago, I read a blog post by Jesse Stay about switching to Blogger. What I remembered the most was that he has able to host his blog on Blogger for free. Since I don't use this blog much, I don't feel like it is worth it to pay too much for hosting.
tags:
- wordpress
- web hosting
- blogger
- technology
modified_time: '2011-10-23T21:09:24.408-10:00'
thumbnail: http://2.bp.blogspot.com/-i0Qp6z9oCBc/TqKihn5DD6I/AAAAAAAACp4/0zmld8hSQ9M/s72-c/download.jpeg
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-1052398323566366468
blogger_orig_url: https://www.christopherslade.com/2011/10/i-moved-to-blogger.html
redirect_from: /2011/10/i-moved-to-blogger.html
---

Since it has been another year, it was time for me to reanalyze how I am hosting this blog. A little while ago, I read a [blog post](http://www.staynalive.com/2011/05/why-as-developer-i-switched-to.html) by [Jesse Stay](http://staynalive.com/) about switching to Blogger. What I remembered the most was that he has able to host his blog on Blogger for free. Since I don't use this blog much, I don't feel like it is worth it to pay too much for hosting.  I have been hosting it with a self-hosted WordPress install, and as Jesse points out, it was too time-consuming to keep it up to date and running smoothly.  Without the super cache plugin set up and configured correctly, I was getting up to 3 seconds per page load which would never survive a high-traffic day. Even with the cache setup correctly, I still even doubted that my blog would withstand a heavy traffic day.

I could have moved my blog to Wordpress.com, but that comes with ads and additional fees that Jesse details in his blog post. Some other options I looked at were using [Github pages](http://pages.github.com/) and using [toto](https://github.com/cloudhead/toto) hosted by [Heroku](http://heroku.com/). I like the idea of having a git repository being the source for my blog, but I couldn't format my old posts in the markdown, and none of the scripts translated things over correctly. It ended up being too much effort to transfer my old blog posts over so decided to try blogger. (I was hoping to edit my posts with a plain old text editor too.)

In less than 5 minutes, I had all of my posts and comments transferred over to Blogger, so I was sold. It did take a little while to configure things the way I wanted, and then I had to redirect my old WordPress-style links to my new blogger links. I plan on doing a post in the near future describing the process of transferring my WordPress blog to Blogger (including how to redirect your links), so stay tuned.

I do want to explain how I set up some features (usually supplied by a plugin) that I had on WordPress on Blogger.  First of all, I have been using [Disqus](http://disqus.com/) as my comment engine on my WordPress blog.  As you post comments on a lot of different sites, there isn't a way to aggregate all of your comments together.  Disqus lets your readers create a single profile they can use to comment on every site that uses Disqus, that way all of your users' comments can be aggregated together. It also allows users to use their Facebook or Twitter accounts to comment.  Lots of sites are using it.

Disqus installation is easy. Create an account on Disqus, then add a new site. Fill in your url and look through all the settings to make sure it's setup the way you want. Import your current comments by going to Tools -> Import/Export. Then click on the install tab and click on Blogger. It will ask you to select your blog. Once you finished with that, you will have a Disqus widget. Add it to your layout (preferably on the bottom part).  You should see Disqus take over for your comments.

The next feature is [Feedburner](http://feedburner.com/), which will optimize your feed for each of your subscribers.  Your feed is what Google Reader and other news/feed readers use to know when your blog has been updated. Since FeedBurner is owned by Google, installation is easy. Go to Feedburner.com and create an account. Then burn your feed by putting in your URL (make sure you select your posts' feed and not your comments' feeds).  It will also let you assign your feed a URL. Then, go to your Blogger settings, under other.  You will see a "Post Feed Redirect URL" setting. Paste in your Feedburner feed URL. Now your subscribers should be getting their feeds from Feedburner.  To test it go to http://yourblog.blogspot.com/feeds/posts/default (or  http://yourblogaddress.com/feeds/posts/default if you have your own domain).  You should be redirected to Feedburner and see your posts.

Finally, I wanted to add a Facebook like button to my posts. By default, I already had the +1 button (Google+) and a Twitter button but no Facebook button. To get a Facebook like button follow [these instructions](http://www.bloggerplugins.org/2010/04/facebook-like-button-for-blogger.html). Some old instructions don't work for the current layouts so be careful.  If your like count is strangely high (around 16,000 likes), then your readers will be liking some page called post.url instead of your post!

I hope the information is helpful.
