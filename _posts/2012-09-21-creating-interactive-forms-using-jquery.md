---
id: 67
title: Creating interactive forms using jQuery
date: 2012-09-21T12:18:40+00:00
author: alaa
layout: article
guid: 67
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:8:"30373923";s:7:"blog_id";s:8:"30897336";s:9:"mod_stamp";s:19:"2012-09-21 12:18:40";}'
categories:
  - JavaScript
  - jQuery
tags:
  - UI
  - Web design
key: creating-interactive-67
---
hi guys,  
Today i&#8217;ll show you how to create an interactive action for some forms using jQuery. Actually when you want to create a good UI you should make use of every single pixel in your page. Also try to use some interactive action form displaying and hiding your forms.

Here we are gonna use [code]fadeIn();[/code] and [code]fadeOut();[/code] actions to do so. Actually this design can be used for example to hide and display login forms or creating any usable forms.

first i&#8217;ll show you the mark up below

```js
<html>
    <head>
        <title>Creating Interactive Forms Using jQuery</title>
        <link href="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8/themes/base/jquery-ui.css" rel="stylesheet" type="text/css"/>
        <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js"></script>
        <script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8/jquery-ui.min.js"></script>
         
         
        <link rel="stylesheet" type="text/css" href="demos.css" />
         
        <style>
            #form{
                display:none;
                height : 200px;
                width:200px;
                color: black;
                background-color : black;
            }
             
            #mask {
                display: none;
                background: #000; 
                position: fixed; left: 0; top: 0; 
                z-index: 10;
                width: 100%; height: 100%;
                opacity: 0.8;
                z-index: 999;
            }
 
        </style>
         
    <head>
    <body>
        <button class="ui-button ui-button-text-only ui-widget ui-state-default ui-corner-all">
            <span class="ui-button-text">Click Me</span>
        </button>
         
        <center>
            <div id="form">
            </div>
        </center>
    </body>
</html>
```

as you can see above there is a mask that is hidden, the mask will be the background for the form that will appear when we click on the button.

Then i&#8217;ll list the click button action.  
When we click on the button the mask must be visible, and the form will be shown above it. So first we will append our markup with the mask element. Then use the 
`fadeIn();` to display our form. `fadeIn();` takes one parameter the time for the form to be shown in m seconds. Also we&#8217;ll use the `fadeIn();` to display the mask after we have appended it&#8217;s markup element.  
Here we have another action that we must pay attention for, when the user clicks anywhere on the mask element. First its markup must be remove then the mask and the form must be hidden and here we&#8217;ll use the `fadeOut();` to do so.

Here&#8217;s the button click action code

```js
$(function(){
                 
    $("button").button();
     
    $("button").click(function(){
     
        //display the form area
        $("#form").fadeIn(1000);
         
        //add the mask to the html body
        $('body').append('<div id="mask"></div>');
         
        //display the mask
        $('#mask').fadeIn(1000);
    });
     
    $('#mask').live('click', function() { 
     //hide the mask and form
     $('#mask , #form').fadeOut(300 , function() {
            //remove the mask to display the normal html page without <div id=""></div>
            $('#mask').remove();  
        })
    });
});
```

hope you enjoyed this tutorial, and finally here&#8217;s the full code

```js
<html>
    <head>
        <title>Creating Interactive Forms Using jQuery</title>
        <link href="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8/themes/base/jquery-ui.css" rel="stylesheet" type="text/css"/>
        <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js"></script>
        <script src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8/jquery-ui.min.js"></script>
         
         
        <link rel="stylesheet" type="text/css" href="demos.css" />
         
        <script type="text/javascript">
            $(function(){
                 
                $("button").button();
                 
                $("button").click(function(){
                 
                    //display the form area
                    $("#form").fadeIn(1000);
                     
                    //add the mask to the html body
                    $('body').append('<div id="mask"></div>');
                     
                    //display the mask
                    $('#mask').fadeIn(1000);
                });
                 
                $('#mask').live('click', function() { 
                 //hide the mask and form
                 $('#mask , #form').fadeOut(300 , function() {
                        //remove the mask to display the normal html page without <div id=""></div>
                        $('#mask').remove();  
                    })
                });
            });
        </script>
         
        <style>
            #form{
                display:none;
                height : 200px;
                width:200px;
                color: black;
                background-color : black;
            }
             
            #mask {
                display: none;
                background: #000; 
                position: fixed; left: 0; top: 0; 
                z-index: 10;
                width: 100%; height: 100%;
                opacity: 0.8;
                z-index: 999;
            }
 
        </style>
         
    <head>
    <body>
        <button class="ui-button ui-button-text-only ui-widget ui-state-default ui-corner-all">
            <span class="ui-button-text">Click Me</span>
        </button>
         
        <center>
            <div id="form">
            </div>
        </center>
    </body>
</html>
```