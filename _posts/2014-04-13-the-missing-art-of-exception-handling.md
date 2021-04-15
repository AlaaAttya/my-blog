---
id: 124
title: The missing art of exception handling
date: 2014-04-13T10:41:12+00:00
author: alaa
layout: post
guid: http://alaaattya.wordpress.com/?p=124
permalink: /?p=124
publicize_twitter_url:
  - http://t.co/ZjN4nSx3SP
publicize_linkedin_url:
  - 'http://www.linkedin.com/updates?discuss=&scope=210771706&stype=M&topic=5861060325821935616&type=U&a=85IN'
publicize_twitter_user:
  - AlaaAttya
categories:
  - Uncategorized
---
First I would like to start by a quote I&#8217;ve learnt from <a href="https://www.facebook.com/ymohammad" target="_blank" rel="noopener">Dr.yasser farouk</a> (one of the doctor I&#8217;m proud to learned from) &#8216;as a developer it&#8217;s a shame to let the OS throw your code out of CPU because of division by zero or array out of bounds&#8217;

He was right about that and it&#8217;s also a good behavior and makes It easy for the developer to eliminate bugs. For example: you&#8217;re trying to persist a user object in database which has no &#8217;email&#8217; property set(which is required by your class responsible for db operations). This will throw an exception says that &#8217;email&#8217; property should not be null and then you should have an if statement to check if the required properties are not nulls (which is a really big hassle for an object with 20 property for example).

For me as a web developer (who writes in php) exception handling saves me a lot of time spent of dangling if else to check every single case. Using exception handling makes it easy as putting the code which I suspect in a try block such as follows:

`<br />
try {<br />
                $fbdata = $facebook->get($fbToken, $fbId);<br />
            } catch (\FacebookApiException $e) {<br />
                throw new Exception\AuthenticationFailedException('User exists but Facebook token invalid');<br />
            }<br />
` 

As an architect you should start designing classes to serve your custom exceptions.

As a Symfony2 lover I&#8217;ll show you an example how to do it in Symfony by extending the existing exception classes:

`<br />
<?php</p>
<p>namespace Smartizer\EventxBundle\Service\Exception;</p>
<p>class AuthenticationFailedException extends LogicException<br />
{<br />
}<br />
` 

as you may notice it&#8217;s pretty easy to get started and saves you alot of time spend on checking and dangling if else.

hope you&#8217;ve liked my post and start defining your custom exceptions.