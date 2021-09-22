---
id: 108
title: Template Engines how to start
date: 2013-06-27T22:58:24+00:00
author: alaa
layout: article
guid: 108
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1094482;i:183;}s:2:"wp";a:1:{i:0;i:7;}}'
publicize_twitter_user:
  - AlaaAttya
categories:
  - Knockout
  - Template Engine
  - Web Development
tags:
  - Front-end
  - MVVM
---
Hello everyone,

Today i&#8217;m gonna show you something which you&#8217;ll really love to work with. It&#8217;s template engines.  
Template engines are libraries which is used to manage large amount of data. Actually creates customized data-structures for the front-end. This picture may clarify the functions of template engines.

<img class="image image--xl" style="width: 100%" src="/assets/images/templating-engine1.png"/>


When the font-end acquires data, the back-end replies with a row data which need to be formatted in a well organized data-structure and then viewed at the front-end.

It&#8217;s the template engine task to do so.

This will show you how the template engine manages data  
<img class="image image--xl" style="width: 100%" src="/assets/images/templating-engine2.png"/>

and there&#8217;s the final step, managing the view

<img class="image image--xl" style="width: 100%" src="/assets/images/templating-engine3.png"/>

There are various template engines like <a href="http://mustache.github.io/" title="Mustache" target="_blank" rel="noopener">Mustache</a> , <a href="http://emberjs.com/" title="Ember js" target="_blank" rel="noopener">Ember js</a> and <a href="http://knockoutjs.com/" title="Knockout js" target="_blank" rel="noopener">Knockout js</a>

I prefer to use Knockout. Knock out uses MVVM (Model View View Model).

All you need is to create your view model, add observables to it and apply it.

Observable are used in knockout wherever you want to track properties. Then apply your model view model.  
Observables has setters and getters. To set it&#8217;s values you need to deal with [code]ko.observable("Your value goes here");[/code]  
And the getter is the observable name  
for example suppose you need to define an observable for username  

```js  
function viewModel(){  
	this.username = ko.observable("Alaa Attya");//setting username observable value  
}

var vm = new viewModel();  
ko.applyBindings(vm);  
```

You need to know that each observable tracks a specific data-bind. And data-binds has many types text, value, event,&#8230;. you can go and see the <a href="https://knockoutjs.com/documentation/introduction.html" title="knockoutjs" target="_blank" rel="noopener">documentation</a>.If you wanna create an input text which you wanna track it&#8217;s values.

follow this [example](http://jsfiddle.net/AlaaAttya/PAZ82/1/)

That&#8217;s the big idea behind the template engines, hope you enjoyed.

Thanks 🙂