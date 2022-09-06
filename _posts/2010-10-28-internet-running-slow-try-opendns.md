---
layout: post
title: Internet Running Slow? Try OpenDNS
date: '2010-10-28T13:40:00.000-10:00'
author: Christopher Slade
description: I know that technically oriented readers will probably already know this, but for any readers that don't know, there is a way that you could possibly speed up your Internet connection.
tags:
- dns
- technology
modified_time: '2011-10-21T21:46:17.058-10:00'
thumbnail: http://3.bp.blogspot.com/-XoL1oHmHoio/TqJ0ubDl5JI/AAAAAAAACo8/drZodkCt5Dg/s72-c/opendns_logo1.jpg
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-4543802491383058493
blogger_orig_url: https://www.christopherslade.com/2010/10/internet-running-slow-try-opendns.html
redirect_from: /2010/10/internet-running-slow-try-opendns.html
---

I know that technically oriented readers will probably already know this, but for any readers that don't know, there is a way that you could possibly speed up your Internet connection.

If you have a page that is loading slow (say like Facebook.com or any other page) one of the problems might be a slow DNS server. If you look at the status bar in your browser you will see two messages as a page loads. The first message will say "looking up ...url..." or it will say "waiting for ...url..."  Of course this message will probably vary based on which browser you are using.  But if your waiting for a page and it seems like you are spending a lot of time looking up site names, then switching your DNS server will probably help.

A lot of pages you see on the Internet actually come from multiple servers around the world.  CNN.com, FoxNews.com, and even Facebook.com have you load content from a lot of different servers.  And for each server you visit you need to look up its address.  Every computer on the Internet has a unique address, so that messages can find their way across the Internet to that specific computer.  This address is called an IP address and looks something like this:  128.224.123.25.  DNS, which is short for domain name system, is the phone book of the Internet.  It translates addresses like www.facebook.com into ip address so your page request can reach the web server.

Whenever you connect to the Internet, your computer is usually are told which DNS servers to use by your Internet service provider.  However, these servers are often slow, and many times have to ask several other servers to find the sites that you want.  This is why it might take a while to find all of the different sites that make up the site you are trying to visit.  Well [OpenDNS](http://www.opendns.com/) will provide you with a fast DNS server to use.  It is free, and they even have [video tutorials](http://www.opendns.com/support/videos/) to show you how to setup your computer or wireless router to use their DNS servers.  As an added bonus, they can provide web filtering and protect you from [phishing scams](http://en.wikipedia.org/wiki/Phishing).

So if you are seeing a lot of "looking up" messages while you wait for pages to load, it might be worth it to give OpenDNS a try.  Google offers a [similar service](http://code.google.com/speed/public-dns/) as well.