---
id: 36
title: using jQuery ajax with php
date: 2012-01-29T13:16:48+00:00
author: alaa
layout: post
guid: http://alaaattya.wordpress.com/?p=36
permalink: /?p=36
publicize_results:
  - 'a:1:{s:7:"twitter";a:1:{i:248646703;a:2:{s:7:"user_id";s:9:"AlaaAttya";s:7:"post_id";s:18:"163611560160407552";}}}'
categories:
  - Ajax
  - JavaScript
  - jQuery
---
hi guys ,here&#8217;s a new trick using jQuery ajax,

while working on a login system actually i was using jQuery in building some cool GUI components

so i faced a problem how will i send the user data to the server to check them ?!!

the only solution is to use ajax and the steps to do that

  1. Get the user data from textboxes using JavaScript.
  2. Deal with some jQuery ajax codes to send the user data to the server using post.
  3. The php file will check the user data.
  4. Receive the response from the php file using jQuery ajax.

So now let&#8217;s get some geeky behavior with some code snippets

first the html file that contains the form

[code]  
<html>  
<head>  
<title>jQuery Ajax Test</title>  
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />  
<link href="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8/themes/base/jquery-ui.css" rel="stylesheet" type="text/css"/>  
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js"></script>  
<script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8/jquery-ui.min.js"></script>  
<script type="text/javascript" src="ajax_test.js"></script>  
</head>  
<body>  
<p>User Name</p><input type="text" id="userName" />  
<p>Password</p><input type="password" id="password" />  
<br />  
<div id="loginButton"><pre>Sign In</pre></div>  
<div id="check"></div>  
</body>

</html>  
[/code]

here a put an empty div with an id called check when the user data is true then i&#8217;ll user it to inform him,also when invalid data i&#8217;ll use it to tell the user

here&#8217;s the ajax_test.js

`<br />
$(function(){<br />
$("#loginButton").button() ;<br />
$("#loginButton").click(function(){`

var user = document.getElementById(&#8220;userName&#8221;).value;  
var pass = document.getElementById(&#8220;password&#8221;).value;  
$.post(&#8220;login.php&#8221;,{userName : user , password : pass } ,function(data) {//assign the php variables userName=user and password=pass  
if(data==&#8217;yse&#8217;){  
document.getElementById(&#8220;check&#8221;).innerHTML=&#8221;Login Successfully&#8221;;//if the serever respond with yes  
}  
if (data==&#8217;no&#8217;) {  
document.getElementById(&#8220;check&#8221;).innerHTML=&#8221;Error in user Data&#8221;;//if the server respond with no  
}  
});

});  
});

the most important method used here is $.post() it has three parameters

first the requested file on the server,then the passed parameters to the server (we use the : operator as an assignment operator),and last the code that handles the received data

in this tutorial the server is supposed to respond with either yes or no

and finally here&#8217;s the full source code

http://www.mediafire.com/?370f95ef27f1p3m