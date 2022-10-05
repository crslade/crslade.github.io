---
layout: post
title: My Facebook News Feed
date: '2011-01-22T13:58:00.000-10:00'
author: Christopher Slade
description: Take control over your Facebook news feed. Facebook uses a secret formula to decide who makes it into your news feed. Unfortunately, this formula prefers very active Facebook users over less active ones. (Look at the link for some other tips and trick to get you on more of your friends' news feeds.) Anyway, this always bugged me a little bit, so I decided to fix it for the next Kynetx developer contest.
tags:
- facebook
- kynetx
- technology
modified_time: '2011-10-21T20:51:57.661-10:00'
thumbnail: http://3.bp.blogspot.com/-u9A2He3FXsA/TqJn9AqT_UI/AAAAAAAACok/MRRghXLlDnc/s72-c/MyFeedSS1.png
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-1077735555217262305
blogger_orig_url: https://www.christopherslade.com/2011/01/my-facebook-news-feed.html
redirect_from: /2011/01/my-facebook-news-feed.html
---

Take control over your Facebook news feed. Facebook uses a [secret formula](http://http//www.businessinsider.com/how-facebook-decides-what-to-put-in-your-news-feed--these-10-secrets-reveal-all-2010-10) to decide who makes it into your news feed. Unfortunately, this formula prefers very active Facebook users over less active ones. (Look at the link for some other tips and trick to get you on more of your friends' news feeds.) Anyway, this always bugged me a little bit, so I decided to fix it for the next [Kynetx](http://www.kynetx.com/) developer [contest](http://code.kynetx.com/2011/01/10/developer-contest-scratch-that-it-ends-jan-24th/).

| ![My Facebook News Feed](/assets/img/MyFeedSS1.png) |
|:--:|
| **Faces and names blacked out for privacy.** |

There are a few friends that I would like to know about and these friends are not the most avid Facebook users. Therefore, they don't show up on my news feed very often. When I look at their profile, I realized I missed some big news. To make sure I don't miss their posts, I wrote a Kynetx app to display the most recent post from everyone on a Friend List. It will display it above your regular news feed. You can change the list it displays by selecting a different list at the top.

If you don't know, you can organize your friends into lists. Just click on friends on the left, then click the edit friends button. You might want to keep this list private, or your friends might find it and realize that you are not as interested in them as they think you should be.

I suggest that you keep your list to about 5 to 10 people, or else it will take a long time to load. Hopefully, I can find a way to speed it up. If you want a longer list, just read your "filtered" news feed for a little bit, and it should show up after about a minute or two. If you have too big of a list then it might time out and never return the results. If this happens, delete your cookies from kobj.net. It is still a little rough around the edges especially since I have only spent one evening on it. I hope to improve it as I find the time. Here are the browser extensions you can download and install to use the app.  You need to accept cookies (even 3rd party cookies) from kobj.net or you cannot authorize the app with Facebook.

[Firefox](http://www.christopherslade.com/MyNewsFeed.xpi), [Chrome](http://www.christopherslade.com/MyNewsFeed.crx), [Internet Explorer](http://www.christopherslade.com/MyNewsFeed_Setup.exe)

If you don't want to install an extension, you can use this bookmarklet. Drag the link below to your bookmark toolbar and click on it when you want your personalized news feed to appear. When it says to refresh the page, you will have to click the bookmarklet again after you refresh the page.

Here is a list of currently known bugs. I will try to fix them as I have time.

* Some posts don't display correctly, especially your friends who don't permit you to see their news feed. (I can't ever show you them, but I need to display a message that you can't see them.)
* It won't show up on every news feed. There are a lot of different URLs that display your news feed, and I haven't found them all. If it doesn't show up, type http://www.facebook.com into your URL, and it should show up there.