---
layout: post
title: Migrating from Wordpress to Blogger
date: '2011-10-25T00:04:00.001-10:00'
author: Christopher Slade
description: Here are some detailed instructions on how I moved my blog from Wordpress to Blogger, including how to get my old Wordpress links to redirect to my new blogger style links.  After the switch, I also learned that Google+ will integrate with Blogger, so that is even more of an incentive.
tags:
- wordpress
- web hosting
- blogger
- technology
modified_time: '2012-04-16T10:10:21.549-10:00'
thumbnail: http://2.bp.blogspot.com/-i0Qp6z9oCBc/TqKihn5DD6I/AAAAAAAACp4/0zmld8hSQ9M/s72-c/download.jpeg
blogger_id: tag:blogger.com,1999:blog-2721499664417059501.post-7919171787478655080
blogger_orig_url: https://www.christopherslade.com/2011/10/migrating-from-wordpress-to-blogger.html
redirect_from: /2011/10/migrating-from-wordpress-to-blogger.html
---

Here are some detailed instructions on how I moved my blog from WordPress to Blogger, including how to get my old WordPress links to redirect to my new blogger-style links.  After the switch, I also learned that Google+ will integrate with Blogger, so that is even more of an incentive.

This should work with a self-hosted WordPress blog and a Wordpress.com blog.  If you don't have your own domain, you can transfer your blog to Blogger, but you will not be able to preserve and redirect your old links.

Before you begin, you might want to use [OpenDNS](https://opendns.com/) for your DNS on your local machine. You can refresh the DNS cache at any time, so you can see your changes immediately instead of waiting up to 2 days for the DNS cache to expire. Plus using OpenDNS [has many benefits](http://portfolio.christopherslade.com/internet-running-slow-try-opendns.html). 

Also, if you want to redirect your old Wordpress style URL's to your new Blogger style URL's you will need a server somewhere that will handle the redirections.  If you don't have one, you can use [Heroku](https://heroku.com/) for free.  I will show you how to set it up, but you will need Git, and Ruby installed on your machine.  Mac users already have ruby installed (they might need to install x-code from the app-store), and they can get git from here.  I also recommend installing RVM to install Ruby version 1.9.2. Windows users can get Ruby and Git (and a lot of extras) from railsinstaller.org. You only need Ruby, Git, and Bundler, so you don't have to install all of the packages. I don't have a Windows machine to try it out, so this is just my best guess.

We will be doing the following steps to make the transfer from Wordpress to Blogger:
1. exporting the posts and data out of Wordpress and importing them into Blogger.
2. Configure Blogger to meet our needs.
3. Set up a redirection server that will redirect Wordpress style links to Blogger style links.
4. Transfer the domain from Wordpress to Blogger.
5. Install Disqus comments (if you want to use it) on Blogger and migrate all of the discussions.

I organized the steps to reduce the amount of downtime your blog will face. You should be able to keep the blog up the full time, but your readers might not be able to comment until the DNS changes have fully propagated. Also, you will lose all of your Facebook likes and +1's, except on your main domain.  Facebook/Google will not follow your redirections and combine the old Likes/+1's with your new ones.  If this is unacceptable, then you will need to stay with WordPress.

# Exporting your posts from WordPress and importing them into Blogger.

To export your Wordpress post and import them into Blogger just follow [these instructions](http://wordpress2blogger.appspot.com). My blog was less than 1MB, but if you have a bigger blog, you will have to download the converters and run them manually. More details on that process can be found here.

You should create a new Blogger blog, and don't worry about the blogspot.com URL if you have your own domain. Once it is up you can change the URL to the right domain. After you import your Blogger file, you should see all of your posts and comments. They will all be drafts, and you can select them all and publish them.

There are a few things that might be a lot of work after you complete this step. First of all, all the pictures will work, but only until you move your domain to Blogger. They are pointing to your WordPress blog, so once your domain is moved over, they will stop working. You will need to get them off of your old blog and upload them to Blogger, or somehow host them on your redirection server. I didn't have many pictures, so I just uploaded them to Blogger, but I will describe how you can host them on the redirection server. Also, on Blogger, your urls will be missing words like "the", "a", and "with". This will create a little bit more work down the road, but I'm not sure if you can do anything about that.

# Configure Blogger

You can look at all of the settings.  I wouldn't set your domain until after you have the redirections in place. You can also take the time to edit the layout and add widgets to the side.  Make sure you're happy with how it looks, so you will know if you want to continue or not. Your WordPress blog should still be up. You can also add the Facebook like buttons I described in the previous post.  Don't install Disqus until after you have your redirections in place either.

Now is also a good time to follow these instructions to get your author's picture in your search results.  You can also see Google's instructions as well.  What I did was create an About page and link to it with a text widget (not the page's widget) that is included on all pages in my blog. I edited the HTML to include the link with rel="author" in it. On the About page, I have a picture, short bio, and a link to my Google+ profile with rel="me". Make sure the Google+ link begins or ends with a +, or is a profile button, with rel="me" in the anchor tag (not rel="author").

# Set up your redirections

To redirect your WordPress style URL's to your new Blogger blog, you will need a server to handle the redirections. If you have an Apache server, you can use the rewrite mod to create the redirections. Below is a sample .htaccess file that I used to redirect my links.  You will need to customize it for your domain.  The redirection server needs to be a sub-domain of your domain. So if you host your blog at www.example.com or blog.example.com, your redirection server needs to be something.example.com (I used old.christopherslade.com).

Here is the [.htaccess](https://gist.github.com/crslade/1311803) file I used before I thought about using Heroku.

<script src="https://gist.github.com/crslade/1311803.js"></script>

The .htaccess file includes redirections for my author page, about page, categories, tags, the feed, and the posts.  In Blogger, there are just labels, so both categories and tags redirect to the label pages. I also had to add in some rules to redirect posts where Blogger didn't include words like "the" and "a" in the URL.  You will need to search for these and add in those redirections as well.

If you don't have a server to host the redirections (I migrated to ditch the server), you can use Heroku for free.  When I was trying out different blog solutions, I ran across toto and learned a little about Rack.  Since I develop in Rails, I really wanted to make toto work, but I couldn't easily migrate my posts. But I did learn enough to know that I could use Rack to redirect URL's. I created a simple Rack app that would redirect the URL's, and even host some static assets. You can use this app to redirect your URL's and even host your pictures from WordPress.

I uploaded my app onto Github.  If you want to use it, just clone it and change the config.ru file. Again, you will need Git, Ruby, and Bundler installed on your machine. You can then use Heroku to host your redirection server.  Here is my config.ru file that you will need to change:

<script src="https://gist.github.com/crslade/1311852.js"></script>

You should change the root to your domain, and then change the author page. You can remove my specific post redirections and add in your own.

To pull the code to your machine, in the terminal or commad prompt type:

    git clone https://github.com/crslade/wp2blogger-redirector.git


 Then you should have a wp2blogger-redirector directory.  Change into the directory and edit the config.ru file.  You can test it by typing in the terminal or command prompt: rackup.  This will start the server on your local machine.  Then in a browser goto http://localhost:9292. You should see "Nothing Here". You can then type the Wordpress URL after the :9292 (like http://localhost:9292/2011/09/blog-post/) and you should be redirected to the right URL (http://www.youdomain.com/2011/09/blog-post.html).  As you fix things, remember that your browser will cache the redirections, so you need to clear the browser cache if something goes wrong and you want to retest it.  Also, every time you make a change to config.ru, you will have to kill the server and start it up again (Control-C, and then type rackup again), or install the shotgun gem ("gem install shotgun").  Then you can launch the server by typing: shotgun.  It will start the server on 9393 instead of 9292, and you shouldn't need to restart it after changing the config.ru file (but if things aren't working you might want to try restarting it before you pull all your hair out).


You can also add in your old pictures by copying the /wp-content/uploads directory into the public directory. You will also need to add in the /wp-content to be served statically. To do this change line 3 in the config.ru file to be:

    use Rack::Static, :urls => ['/index.html', '/favicon.ico', '/wp-content'], :root => 'public'


You can also test to make sure the server serves your old pictures. Heroku will only let you use 100MB in disk space.  So you might need to delete some pictures. Wordpress does store several sizes of pictures, and you can remove all of the sizes you don't use on your blog.


After you get the redirection server working locally, you can push it to Heroku.


To commit the changes locally, type:
    git add -A
    git commit -m "some message"


Then create an account on Heroku. You can follow these instructions to launch your server on Heroku.  Don't worry about bootstrapping your database, you don't have one. In summary, type the following:
heroku create
git push heroku master


If everything worked your redirection server should be live. Test it by typing Heroku open, and you should see it in your browser. Remember the URL, because you will need it when changing your DNS.


# Migrate your domain to blogger

Now you are ready to migrate your domain.  First, create a CNAME record in your DNS to point old.domainname.com to Heroku, and follow these instructions for adding the subdomain to your Heroku app (you are probably not on the Cedar stack).  You only need to add one subdomain, not your full site.    While you are at it, you can now point your main domain (or a subdomain) to your new blog and edit your new blog's settings to add your domain.  It's under Settings -> Basic. You will also want to add a missing files host, and put in "old" (if you used old.domainname.com) for the name of the host.  Blogger has a link with instructions on how to set your domain name to point to Blogger that should appear as your change your settings.


If you are using OpenDNS, you can go here, and check their cache. After you check, you can request a cache refresh and it will update the DNS settings from your registrar. (It might take a couple of hours for your registrar to update its DNS servers.) You will also have to refresh your local DNS cache by rebooting your machine.  Your domain should be pointing to your new blog. Remember, it takes a couple of days for the DNS changes to propagate to everyone, but with OpenDNS you can try it a lot faster.  You should leave your old blog up for at least a few days, so if your readers haven't gotten the DNS update, they will still see your old blog.  You might want to disable comments because they will not migrate over to your new blog.


# Migrate Disqus comments

You can now install Disqus on your Blogger blog, by going to disqus.com, logging in, clicking on your blog, and then clicking the install tab.  Click on blogger, and it will install it to your blog. You will then need to edit your layout in Blogger, to add the widget (preferably on the bottom). You should see Disqus take over for your comments, but all of your old comments will be gone.  Now, back in Disqus, go to tools, and migrate threads.  You can try the redirect crawler if your redirects are all set up. You can also upload a URL map.  Once done, your comments should re-appear.


Unfortunately, your likes and +1's will be reset. You should now be up and ready to go. Hopefully, Google+ integration and a free hosting solution will make all the work worth it. If you have any questions, just leave them in the comments.

