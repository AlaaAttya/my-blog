---
id: 70
title: WAMP server problem solution for windows 8
date: 2012-11-07T19:06:30+00:00
author: alaa
layout: post
guid: http://alaaattya.wordpress.com/?p=70
permalink: /?p=70
publicize_twitter_user:
  - AlaaAttya
twitter_cards_summary_img_size:
  - 'a:6:{i:0;i:421;i:1;i:475;i:2;i:3;i:3;s:24:"width="421" height="475"";s:4:"bits";i:8;s:4:"mime";s:9:"image/png";}'
categories:
  - server administration
tags:
  - server adminsteration
  - wamp
  - web developing
  - win 8 problems
---
Hi guys hope you are having a good day.

Most of us have tried the latest Microsoft OS (windows 8). It&#8217;s really brilliant OS.  
As a web developer you have installed one of the local web servers like WAMP.  
If you have tried to get WAMP online on windows 8 it will fail. I guessed that other server is listening to port 80 and i was right 😀  
To know who is listening on port 80 just run WAMP and have a left click on the tray icon choose Apache->service->Test port 80 the command prompt window will appear and you will know who is listening on port 80.

For windows 8 IIS 8 server is installed automatically and runs also automatically on windows start up. All you&#8217;ll need to do is ti disable it from running on start up and here is the solution

launch control panel-> Administrative tools->services from the services search for a service called (World Wide Web Publishing Service) double click on it then set the start up type to disables then press apply the ok, restart your windows, run your WAMP server and every thing will be OK 🙂  
![Word Wide Web Publishing Service](http://alaa.ninja/wp-content/uploads/2012/11/untitled.png) 

Hope you enjoyed  
Thanks 🙂