---
id: 79
title: 'solution for On &#8220;Enter Key&#8221; press event in javascript'
date: 2012-12-15T03:25:50+00:00
author: alaa
layout: article
guid: 79
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1094482;i:115;}s:2:"wp";a:1:{i:0;i:4;}}'
publicize_twitter_user:
  - AlaaAttya
categories:
  - Uncategorized
tags:
  - enter key event
  - JavaScript
  - javascript events
  - tricks
  - web development
key: solution-for-on-enter-key-press-event-in-javascript-79
---
Hello guys,  
while working on a project i needed to add a text input which takes some action when the user press on the &#8220;enter key&#8221;, you know it&#8217;s something like facebook comment text input 😉

as you may know there is no &#8220;onenterkey&#8221; or &#8220;onsubmit&#8221; for the text input. I stayed 15 min. trying to get the job done but in vain. That got me mad that i was talking to the text input &#8220;hey you mr. input how the hell you get that event fired ?!!!!!!&#8221;. finally i got a trick.

Here&#8217;s a little trick that may help.

you can use the &#8220;onkeydown&#8221; event and then check the pressed key if the key code is 13 &#8220;actually is the enter key code&#8221;. you can get the key code with that command &#8220;event.keyCode&#8221; 

As you can see it seen a little snippet but it got me out of that problem 😀

Here&#8217;s a snippet that can demonstrate what i&#8217;m talking about

```js 
<input type="text" onkeydown="if (event.keyCode == 13) doSomeThing(paam1 , param2.....);" >
``` 

Hope you&#8217;ve enjoyed  
Thanks 🙂