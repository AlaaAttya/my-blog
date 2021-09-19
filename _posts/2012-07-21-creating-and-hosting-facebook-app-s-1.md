---
id: 47
title: Creating and hosting Facebook app.s (1)
date: 2012-07-21T11:48:13+00:00
author: alaa
layout: article
guid: http://alaaattya.wordpress.com/?p=47
permalink: /?p=47
tagazine-media:
  - 'a:7:{s:7:"primary";s:66:"http://alaaattya.files.wordpress.com/2012/07/canavas-view-page.png";s:6:"images";a:9:{s:57:"http://alaaattya.files.wordpress.com/2012/07/apps-tab.png";a:6:{s:8:"file_url";s:57:"http://alaaattya.files.wordpress.com/2012/07/apps-tab.png";s:5:"width";s:3:"979";s:6:"height";s:2:"35";s:4:"type";s:5:"image";s:4:"area";s:5:"34265";s:9:"file_path";s:0:"";}s:58:"http://alaaattya.files.wordpress.com/2012/07/fb-create.png";a:6:{s:8:"file_url";s:58:"http://alaaattya.files.wordpress.com/2012/07/fb-create.png";s:5:"width";s:3:"356";s:6:"height";s:3:"109";s:4:"type";s:5:"image";s:4:"area";s:5:"38804";s:9:"file_path";s:0:"";}s:62:"http://alaaattya.files.wordpress.com/2012/07/fb-create-pop.png";a:6:{s:8:"file_url";s:62:"http://alaaattya.files.wordpress.com/2012/07/fb-create-pop.png";s:5:"width";s:3:"638";s:6:"height";s:3:"194";s:4:"type";s:5:"image";s:4:"area";s:6:"123772";s:9:"file_path";s:0:"";}s:56:"http://alaaattya.files.wordpress.com/2012/07/hosting.png";a:6:{s:8:"file_url";s:56:"http://alaaattya.files.wordpress.com/2012/07/hosting.png";s:5:"width";s:3:"488";s:6:"height";s:3:"210";s:4:"type";s:5:"image";s:4:"area";s:6:"102480";s:9:"file_path";s:0:"";}s:59:"http://alaaattya.files.wordpress.com/2012/07/app-screen.png";a:6:{s:8:"file_url";s:59:"http://alaaattya.files.wordpress.com/2012/07/app-screen.png";s:5:"width";s:3:"713";s:6:"height";s:3:"415";s:4:"type";s:5:"image";s:4:"area";s:6:"295895";s:9:"file_path";s:0:"";}s:70:"http://alaaattya.files.wordpress.com/2012/07/graph_api_interaction.gif";a:6:{s:8:"file_url";s:70:"http://alaaattya.files.wordpress.com/2012/07/graph_api_interaction.gif";s:5:"width";s:3:"783";s:6:"height";s:3:"600";s:4:"type";s:5:"image";s:4:"area";s:6:"469800";s:9:"file_path";s:0:"";}s:56:"http://alaaattya.files.wordpress.com/2012/07/canavas.png";a:6:{s:8:"file_url";s:56:"http://alaaattya.files.wordpress.com/2012/07/canavas.png";s:5:"width";s:3:"700";s:6:"height";s:3:"175";s:4:"type";s:5:"image";s:4:"area";s:6:"122500";s:9:"file_path";s:0:"";}s:61:"http://alaaattya.files.wordpress.com/2012/07/canavas-page.png";a:6:{s:8:"file_url";s:61:"http://alaaattya.files.wordpress.com/2012/07/canavas-page.png";s:5:"width";s:3:"772";s:6:"height";s:3:"274";s:4:"type";s:5:"image";s:4:"area";s:6:"211528";s:9:"file_path";s:0:"";}s:66:"http://alaaattya.files.wordpress.com/2012/07/canavas-view-page.png";a:6:{s:8:"file_url";s:66:"http://alaaattya.files.wordpress.com/2012/07/canavas-view-page.png";s:5:"width";s:4:"1327";s:6:"height";s:3:"457";s:4:"type";s:5:"image";s:4:"area";s:6:"606439";s:9:"file_path";s:0:"";}}s:6:"videos";a:0:{}s:11:"image_count";s:1:"9";s:6:"author";s:8:"30373923";s:7:"blog_id";s:8:"30897336";s:9:"mod_stamp";s:19:"2012-07-21 11:48:13";}'
categories:
  - Facebook
tags:
  - facebook app.
  - web
---
Hi all,  
Though points of view may differ from one person to another we should agree that Facebook is the largest and leading social network ever. Because they always care about users and what is the new for them, they also pay much care for the developers and their different web programming languages. So they have many sdks js, PHP, python &#8230;..etc.  
Today we&#8217;ll have a look about creating free facebook app.s using the latest PHP sdk which they call it GRAPH.

First of all you need to have a facebook developer account and it&#8217;s easy and free. You can get a free one through that link <a href="http://developers.facebook.com/" title="facebook developer account" target="_blank" rel="noopener">facebook developer account</a> and they will send you the activation code for your account as an sms (actually it&#8217;s more secure to do so :D).

Then go to your developer account through the previous link. The you click on the app.s tab at the top like that

![Create a facebook app.](http://alaa.ninja/wp-content/uploads/2012/07/apps-tab.png) 

The click at the create button at the top

![create button](http://alaa.ninja/wp-content/uploads/2012/07/fb-create.png) 

The you&#8217;ll have the following screen where you can specify your app. name and hosting options.

![create screen](http://alaa.ninja/wp-content/uploads/2012/07/fb-create-pop.png) 

as you can see the check box for the <a href="https://heroku.com/" title="Heroku" target="_blank" rel="noopener">Heroku</a> free hosting (which i&#8217;ll show you how to deal with in the following post).

The you&#8217;ll enter the captcha security key which will appear for you.

The you&#8217;ll have the following screen to enter your email to send you the hosting configurations.

![hosting config](http://alaa.ninja/wp-content/uploads/2012/07/hosting.png) 

Then you&#8217;ll have your app. screen like that

![app screen](http://alaa.ninja/wp-content/uploads/2012/07/app-screen.png) 

if you&#8217;ll intend to have heroku free hosting so leave the app. domains blank, the click save you&#8217;ll have an error

so remove the text that has been written in the app domains, then every thing will be alright 😀 .

There another thing which you should know, all facebook app.s can be seen as a part of facebook so why we want to have hosting domain for them

THE ANSWER IS, facebook don&#8217;t host app.s but can suggest you free hosting domains like Heroku and then facebook app. has some property called CANAVAs which can view the app. as a part of facebook 

Here&#8217;s a picture the may help you to understand how every thing is doing right

![api interaction](http://alaa.ninja/wp-content/uploads/2012/07/graph_api_interaction.gif) 

Then how will you configure it?!

At the bottom of the page you have a tab called App on Facebook which you&#8217;ll specify the url of your app

such as the following picture

![canvas config](http://alaa.ninja/wp-content/uploads/2012/07/canavas.png) 

Then don&#8217;t forget to click the &#8220;Save Changes&#8221; button when yo finish.

Here we are finished and you can get you canavas url as follows

choose the app name from the left tabs on the page and then you&#8217;ll find your canavas app. url as follows

![canavas page](http://alaa.ninja/wp-content/uploads/2012/07/canavas-page.png) 

Then you&#8217;ll see the app canvas page as the following picture

![canavas view page](http://alaa.ninja/wp-content/uploads/2012/07/canavas-view-page.png) 

And finally we are done, and wait for the next blog i&#8217;ll show you how to get started with Facebook Graph PHP sdk.

Hope you enjoyed 🙂