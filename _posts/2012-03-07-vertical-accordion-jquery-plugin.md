---
id: 42
title: Vertical Accordion jQuery plugin
date: 2012-03-07T15:26:02+00:00
author: alaa
layout: post
guid: http://alaaattya.wordpress.com/?p=42
permalink: /?p=42
publicize_results:
  - 'a:1:{s:7:"twitter";a:1:{i:248646703;a:2:{s:7:"user_id";s:9:"AlaaAttya";s:7:"post_id";s:18:"177414815755677697";}}}'
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:8:"30373923";s:7:"blog_id";s:8:"30897336";s:9:"mod_stamp";s:19:"2012-03-07 15:26:02";}'
categories:
  - JavaScript
  - jQuery
tags:
  - Web design
  - web developing
---
while developing a website i face a problem that i need a side bar that need some way of tabs the requires viewing sub links when clicking on each tab,

so i have searched more and more i&#8217;ve also tried jQuery ordinary accordion but all in vain.

while googling i&#8217;ve found a jQuery plug which worked for it as magic 😀

it&#8217;s called v-accordion

so guys let&#8217;s stop talking and start coding,

this plugin requires some piece of html structure as u&#8217;ll see.

All you need to do is to put all your tabs in one div which will be passed to jQuery to get the work done. Then you&#8217;ll have a slice for each tab. while coding actually you&#8217;ll have some problem that the plug will not work at the first, so here&#8217;s the solution.

The name of each slice must match as follows &#8220;va-slice va-slice-1&#8221; and give each slice a number, then all the job u&#8217;ll be okay.

here&#8217;s a simple html structure that may help.

[code]  
<html>  
<head>  
<title>Vertical Accrodion</title>  
<link href="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8/themes/base/jquery-ui.css" rel="stylesheet" type="text/css"/>  
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js"></script>  
<script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8/jquery-ui.min.js"></script>  
<script type="text/javascript" src="jquery.easing.1.3.js"></script>  
<script type="text/javascript" src="jquery.vaccordion.js"></script>  
<script type="text/javascript" src="jquery.mousewheel.js"></script>  
<link href="style.css" rel="stylesheet" type="text/css" />  
<link href=&#8217;http://fonts.googleapis.com/css?family=PT+Sans+Narrow&v1&#8242; rel=&#8217;stylesheet&#8217; type=&#8217;text/css&#8217; />  
<link href=&#8217;http://fonts.googleapis.com/css?family=Open+Sans+Condensed:300&v2&#8242; rel=&#8217;stylesheet&#8217; type=&#8217;text/css&#8217;>  
<script type="text/javascript">  
$(function(){  
$("#content").vaccordion({  
visibleSlices : 3,  
expandedHeight : 250,  
animOpacity : 0.1,  
contentAnimSpeed: 100  
});  
});  
</script>  
<style>  
#fst{  
height: 100px;  
width: 100px;  
background-color: red;  
}

#snd{  
height: 100px;  
width: 100px;  
background-color:green;  
}

#trd{  
height: 100px;  
width: 100px;  
background-color: black;  
}  
</style>

</head>  
<body>  
<div id="content">  
<div class="va-slice va-slice-1">  
First tab  
</div>  
<div class="va-slice va-slice-2">  
Second tab  
</div>

<div class="va-slice va-slice-3">  
Third tab  
</div>  
</div>  
</body>  
</html>  
[/code]

as you can see the .vaccordion has many option that may help you,  
Finally there&#8217;s three files needed to get the job done  
1-jquery.vaccordion.js  
2-jquery.mousewheel.js  
3-jquery.easing.1.3.js

here the download link for these files  
http://www.mediafire.com/?nbnayybznxya81m

hope you enjoyed 🙂</pre>