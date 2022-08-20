---
layout: post
title: Getting delayed_job to Work with Rbenv and Mongoid
date: '2011-11-04T09:13:00.004-10:00'
author: Christopher Slade
description: Rbenv is another option that we can use besides RVM to be able to manage different Ruby versions.
tags:
- Rails
- Technology
modified_time: '2011-11-04T09:13:39.555-10:00'
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-8951350656185964873
blogger_orig_url: https://www.christopherslade.com/2011/11/getting-delayedjob-to-work-with-rbenv.html
redirect_from: /2011/11/getting-delayedjob-to-work-with-rbenv.html
---

[Rbenv](https://github.com/sstephenson/rbenv) is another option that we can use besides [RVM](http://beginrescueend.com/) to be able to manage different Ruby versions.  I have always struggled getting RVM to manage everything right, from gemsets to bundles. Since [Bundler](http://gembundler.com/) manages your gems and dependencies for you, gemsets are just an extra layer that caused me a bunch of problems.  So I switched to Rbenv for my production environment.  All went well except [delayed_job](http://blog.leetsoft.com/delayed_job/). It would work just fine with rake jobs:work, but script/delayed_job start would start just fine, but wouldn't pull anything from the database. I am using [Mongoid](http://mongoid.org/), so I assumed that the script was defaulting to the sqlite database.


Well, I looked at the script and noticed that their was a shebang at the top mentioning ruby (#!/usr/bin/env ruby). I just changed it from ruby to ruby-local-exec and it started working again! This made the script run in the bundled environment and pick up on that fact that I am using Mongoid instead of sqlite. Hope this helps someone.
