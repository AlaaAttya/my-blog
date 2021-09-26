---
id: 59
title: Famous phpmyadmin error (this is not a number)
date: 2012-08-21T07:14:11+00:00
author: alaa
layout: article
guid: 59
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:8:"30373923";s:7:"blog_id";s:8:"30897336";s:9:"mod_stamp";s:19:"2012-08-21 07:14:11";}'
categories:
  - Database
tags:
  - mysql
  - phpmyadmin
key: famous-phpmyadmin-error-59
---
hey guys hope you have a good day,

Today a was developing a web app. which a mysql database. I used the famous tool phpmyadmin for that task.

while creating a table in my database i have got an error &#8220;this is not a number&#8221;. I have search on the web for it and a few people had the right solution.

The solution is to set the length field for nvarchar type and every thing will getting well 😉

so don&#8217;t forget to set the length field to get away from that fool error 😀