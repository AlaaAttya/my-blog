---
id: 76
title: Using twitter authorization in Implementing twitter module for your website
date: 2012-12-02T23:14:15+00:00
author: alaa
layout: post
guid: http://alaaattya.wordpress.com/?p=76
permalink: /?p=76
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1094482;i:106;}s:2:"wp";a:1:{i:0;i:4;}}'
publicize_twitter_user:
  - AlaaAttya
categories:
  - twitter api
tags:
  - login with twitter
  - twitter authorization
---
Hello guys,  
Before i started my big love story with web development i saw many websites are using twitter accounts for user login instead of registering new account. Actually i was impressed how those guys hacked twitter and got the accounts and passwords of the user and then check for the validity of these accounts 😀

Days and months later i got what&#8217;s happening behind the scenes. First you app sends the user email and password and asks twitter if this guy has a twitter account. Twitter then responds with &#8220;yes master he is a twitter user&#8221;, else twitter shows that he is not a registered twitter user. This process is called authorization process and that what actually happens. After the user successfully authorized, you can get his id and save it to your database. Each time user logins using his twitter account you check for the existence of that user.

Twitter uses OAuth protocol for authorization and there&#8217;s a simple library that implements that protocol in a simple way. Here&#8217;s what i&#8217;m gonna taking about https://github.com/abraham/twitteroauth

First you need to have a Twitter developer account, then create a twitter app to get the app secret and consumer key. You should specify the callback url because if you don&#8217;t do so it causes an big problem (specially for me :D). **So don&#8217;t leave the callback url blanck.**

I have written a simple code that helps you to authorize users through little snippet.

[code]  
<?php

include &#8216;twitter_lib/OAuth.php&#8217;;  
include &#8216;twitter_lib/twitteroauth.php&#8217;;  
include &#8216;twitter_lib/config.php&#8217;;

/* creating twitter object  
* TwitterOAuth: @params : CONSUMER\_KEY, CONSUMER\_SECRET  
*  
*/  
$connection = new TwitterOAuth(CONSUMER\_KEY, CONSUMER\_SECRET);

/* retrieving request tokens  
* getRequestToken: @params : none  
* @return : request token array contains &#8216;oauth_token&#8217;  
* &#8216;oauth\_token\_secret&#8217;  
* &#8216;oauth\_callback\_confirmed&#8217;  
*  
*/  
$request_token = $connection->getRequestToken();

/* creating authorization url using twitter connection object  
* getAuthorizeURL: @params : oauth token returned from the request token array  
*  
*/  
$auth\_url = $connection->getAuthorizeURL($request\_token[&#8216;oauth_token&#8217;]);

//redirect user to the authorization url  
header(&#8216;Location: &#8216;.$auth_url);

?>

[/code]

As you can see i have included three files at the top of my script &#8216;OAuth.php&#8217; which is the core AOuth library, &#8216;twitteroauth.php&#8217; which is the twitter implementation for AOuth and finally &#8216;config.php&#8217; which holds your app configurations.

All you need to do is to open the &#8216;config.php&#8217; and set the constants to your app consumer key and app consumer secret.

Here&#8217;s the full example source code download link.

http://www.mediafire.com/?p17z236k0qda4nl

Hope you have enjoyed, thanks 🙂