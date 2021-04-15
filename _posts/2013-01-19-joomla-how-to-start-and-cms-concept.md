---
id: 86
title: Joomla how to start with the CMS concept
date: 2013-01-19T22:09:23+00:00
author: alaa
layout: post
guid: http://alaaattya.wordpress.com/?p=86
permalink: /?p=86
publicize_twitter_user:
  - AlaaAttya
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1094482;i:126;}s:2:"wp";a:1:{i:0;i:5;}}'
categories:
  - Joomla
tags:
  - CMS
  - jooma
  - joomla how to start
  - web development
---
All of us heard about joomla. So my friends has asked me to write a blog about how to start with Joomla.

Actually joomla is one of the most famous CMSs in the web development world. So here we got the concept of a CMS which is the acronym for Content Management System. CMS is more different from Framework. CMS is a complete system that simplifies the process of changing and editing large contents.  
For developers it centralizes the processing and makes their codes more portable. It also enhances re-usability of code.

so let&#8217;s talk more about joomla. 

Joomla have four main concepts:

-Templates.  
-Modules.  
-plugins  
-libraries.  
-components.

-Template is something like a theme for your website.  
-Modules is the heart of your website. you can have a login module, registration module&#8230;etc. Any Joomla website contains of many modules. Developers can develop any module and you can add it to any joomla website if it&#8217;s compatible with your joomla version. It provides code compatibility.

-plugins are some functions which are associated with specific triggers. when an event is fired all function with the same type associated with that plugin are executed.

-Libraries are some codes (or you can say packages) the extends the framework functionality. Libraries are considered the lowest level components specially for developers 😉

-Components are something that is considered a small app.s. To get it, imagine Joomla as a system and components as application running on that system. Components work with the MVC pattern. 

Each of the previous will associated with a XML file that describes and identifies it.

In this post it&#8217;ll talk only about how to start authoring a Joomla Module.

First of all you must know the structure of a basic module 

-The name of your folder must have &#8220;mod_&#8221; as the prefix of your module name  
-a XML file that will hold some meta-data about your module like author name, module name &#8230;etc.

it consists of an extension tag which have 3 main attributes

1-method: install  
2-version: the version of your Joomla  
3-type : module

Then you&#8217;ll have some tags that will hold the details like 

which is the name of your module  
the name of the author (it is supposed to be your name :D)  
Your copyright  
and many other tags that is so easy to understand.

Then the most important tag is the  
which holds any file associated with your module (even the php files)

like that 

[code]  
<files>  
<filename module="mod\_testmodule">mod\_testmodule.php</filename>  
<filename>index.html</filename>  
<filename>mod_testmodule.xml</filename>  
</files>  
[/code]

-a PHP file that will do all the processing.  
The name of this file must also have the prefix &#8220;mod_&#8221; followed by your module name or it will not be accessible.  
This must include that line as the first line before any code is written 

[code]  
defined( &#8216;_JEXEC&#8217; ) or die;  
[/code]

which means that no one can execute this file through the URL.

-empty index.html file for indexing issues.  
-You may have a tmpl folder that will collect the data and generate html code to view the result.

Any basic Joomla module must have at least these requirements.

and here&#8217;s a demo module  
http://www.mediafire.com/?5e7pop62p1w20h1

To install any module package the folder as a .zip file  
login as admin. &#8220;URL&#8230;/administrator/index.php&#8221;  
Then choose extension tab->new Then browse and add the .zip file  
Then you are done !

Hope you enjoyed ! 

Thanks 🙂