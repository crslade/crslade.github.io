---
layout: post
title: Getting Rails
date: '2011-09-15T15:04:00.000-10:00'
author: Christopher Slade
description: I am teaching a new class this semester called advanced web application development. The main topic is Ruby on Rails.  A lot of students who have either graduated or couldn't take the course for some other reason wanted to me to make videos for them.  I won't have time for videos, but I will post all the material I use here.
tags:
- rails
- teaching
- technology
modified_time: '2011-10-21T10:53:50.531-10:00'
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-3831917563840438774
blogger_orig_url: https://www.christopherslade.com/2011/09/getting-rails.html
redirect_from: /2011/09/getting-rails.html
---

I am teaching a new class this semester called advanced web application development. The main topic is [Ruby on Rails](http://rubyonrails.org).  A lot of students who have either graduated or couldn't take the course for some other reason wanted to me to make videos for them.  I won't have time for videos, but I will post all the material I use here.

The first step is getting Rails installed.  Most of my students have Windows machines, so the best place to get Rails for Windows would be [RailsInstaller.org](http://railsinstaller.org) (I haven't really searched too long, but this seem sufficient).  I wouldn't worry about installing the SQL Server stuff unless you know you are going to use it.  For now, just stick with SQL lite.  You will want Git.  The only downside to all of this is that there isn't [RVM](http://beginrescueend.com/), which allows you to switch between Ruby versions and create gemsets.  During the semester, all my student will be using Ruby version 1.9.2, so it won't be necessary for the class.

The next step is to create your first application.  The video on RailsInstaller.org walks you through your first application.  I plan on doing a similar demo in class also using the scaffolding.  After, I will walk students through the code, starting at the routes.rb, then going to the controller, and then the model and view.
