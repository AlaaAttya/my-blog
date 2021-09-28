---
id: 24
title: Validating user input in JavaScript
date: 2012-01-08T15:17:58+00:00
author: alaa
layout: article
guid: 24
publicize_results:
  - 'a:1:{s:7:"twitter";a:1:{i:248646703;a:2:{s:7:"user_id";s:9:"AlaaAttya";s:7:"post_id";s:18:"156031905878388736";}}}'
categories:
  - JavaScript
tags:
  - 'javascript'
  - 'js'
key: validating-user-input-in-javascript-24
---
Many developers may face a big problem while dealing with JavaScript; it’s the problem of validating user input using REGULAR EXPRESSIONS

Here are simple steps to do so:

-First what is a regular expression?!

It’s a tool for performing pattern matches and it has to categories

1_-literal syntax_ , it’s something like that  
```js
var reg = /pattern/<br />
````  
2-_Dynamic regular expression_ that can be done using the RegExp() constructor , it’s something like that

```js
var reg = new RegExp("pattern") ;<br />
``` 

after we have got a regular expression we can use it any where

and here’s an example that may be helpful

-In this example we insure that the user enters 6 digits.

first i&#8217;ll construct an html form like that

```js 
<html>
	<head>
		<script type="text/javascript"></script>
	</head>

	<body>
		<form name="iForm">
			<input type="text" name="iText" />
			<button onclick="validateInput();">Click Me</button>
		</form>
	</body>
</html>
```

and between the script tags we put our JavaScript code the will get the job done

```js
function validateInput()
{
	var reg = /^\d{6}$/
	if(document.iForm.iText.value.search(reg)==-1)
	{
		alert("Wrong input.....Please Enter Valid input !!!!")
	}
}
```

Here i&#8217;ll reveal some mysterious about the previous expression

`^` this means that it will start comparing from the first digit
`d{6}` means that it will do comparing for 6 digits
`$` means that it must be 6 digits till the end of the input(actually $ means the end of the input)

here&#8217;s another trick if you want to validate email input from the user

we can do this with this function  

```js
function validateInput()
{
	var reg = /^([a-zA-Z0-9_\.\-])+\@(([a-zA-Z0-9\-])+\.)+([a-zA-Z0-9]{2,4})+$/
	if(document.iForm.iText.value.search(reg)==-1)
	{
		alert("Wrong Email.....Please Enter Valid Email !!!!")
	}
}
```

hope you enjoyed this simple tutorial :)