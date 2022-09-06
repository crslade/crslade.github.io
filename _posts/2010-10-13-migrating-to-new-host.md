---
layout: post
title: Migrating to a New Host
date: '2010-10-13T01:24:00.000-10:00'
author: Christopher Slade
description: So you probably have already noticed, I am not updating my blog very often.  Trying to teach 3-4 classes a semester, doing a dissertation, and trying to be a good husband and father keeps me really busy.  Although my previous host(bluehost) has been great, I decided to go with a cheaper hosting option.  That meant that I had to migrate my blog to a new server.  If you visit my site, you should notice a new, cleaner look.  I hope you like it.  (Although I am probably just writing this to myself since I don't really have any followers.)  What follows are some of the features and choices I made to make this blog look the way it does.  If you are interested in the technical details, then read on.
tags:
- web hosting
- miscellaneous
- wordpress plugins
- technology
modified_time: '2011-10-21T10:53:50.586-10:00'
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-6662245312328552130
blogger_orig_url: https://www.christopherslade.com/2010/10/migrating-to-new-host.html
redirect_from: /2010/10/migrating-to-new-host.html
---

So you probably have already noticed, I am not updating my blog very often.  Trying to teach 3-4 classes a semester, doing a dissertation, and trying to be a good husband and father keeps me really busy.  Although my previous [host](http://bluehost.com/) has been great, I decided to go with a cheaper hosting option.  That meant that I had to migrate my blog to a new server.  If you visit my site, you should notice a new, cleaner look.  I hope you like it.  (Although I am probably just writing this to myself since I don't really have any followers.)  What follows are some of the features and choices I made to make this blog look the way it does.  If you are interested in the technical details, then read on.

First, I decided to transfer my domain name to godaddy.com.  They had a better price than my old host.  It was fun learning about the domain name transfer process.  I started by just transferring the domain, and I kept using my old host's nameservers so that it would continue to point to my old site.  Once I got my new blog up and running, I parked the domain at godaddy, and pointed it to my new host.  I use [openDNS](http://www.opendns.com/) (maybe I will write about that in a future post), and I was surprised at how fast they picked up the change.  It only took them 30 minutes to notice the change and update the entries.  The nameservers at BYU-Hawaii took a couple of days to pick up the change.

Second, I decided to stay with the [Wordpress](http://www.wordpress.org/) blog engine.  I was a little hesitant to stick with wordpress because it takes a lot of resources and runs slow.  My new host doesn't have as many resources.  This meant that my blog loaded really slow (3 seconds per page).  I explored other options.  I even installed [Movabletype](http://www.movabletype.org/).  Movabletype definitely loads much faster, because it saves static html pages on your site after you publish.  However, there are not as many extensions and it seemed much more complicated to setup.

Then I stumbled up the [WP Super Cache plugin](http://ocaoimh.ie/wp-super-cache/?r=supercache).  What it does is create static copies of all of my pages.  Most visitor will get the static copy.  When I create a new post, or when someone comments, the cache is automatically regenerated with the new content.  Now, my pages load in less than a second (except for the Facebook like buttons, but that is Facebook's fault not my server's).  This does mean that my twitter feed will be out of date, but I hope to fix that in the future.

I also decided to use the [Disqus](http://disqus.com/) commenting system.  This lets people log in with their Facebook or Twitter accounts, and then they can post comments.  They also can post their comments to their Facebook wall.  I tried [IntenseDebate](http://intensedebate.com/) which does the same thing.  However, they tied my profile to a Wordpress.com account.  Then to get comment notifications, I had to publish my email address in a Wordpress press profile and in [Gravatar](http://gravatar.com/). IntenseDebate did load faster and that is why I tried it out.  However, after I installed the caching plugin, disqus started to load fast too.  Another good feature of Disqus, is their android app.  Now I can view and moderate my comments on my phone.

I also added the Facebook like buttons so that people with Facebook accounts can like my posts and comment on them in Facebook.  Using an add-to-any button, I also added many ways people can share my posts.

Anyway, I hope you like the new look and features.  Now I just need to get some good content here, and some readers.  Maybe posting more than just once or twice a year will help.  If you are reading this, let me know what you think!