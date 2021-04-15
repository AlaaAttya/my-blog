---
id: 130
title: writing readable clean code
date: 2015-01-15T21:43:04+00:00
author: alaa
layout: post
geo_public:
  - "0"
publicize_linkedin_url:
  - 'https://www.linkedin.com/updates?discuss=&scope=210771706&stype=M&topic=5961608334749478912&type=U&a=3kmE'
publicize_twitter_user:
  - AlaaAttya
publicize_twitter_url:
  - http://t.co/z9llgq1vDP
categories:
  - software engineering
tags:
  - architect
  - clean code
---
How many times did you work with a codebase which you did not write?  
How many times you were working on a codebase and a newly hired developer did not able to work on the same codebase with you?! (and you&#8217;ve got that comment &#8220;who&#8217;s the hell did write that code?! and it was you&#8230;it&#8217;s the very annoying situation&#8221;)

Writing a nice readable clean code has no manual which you can follow. It&#8217;s just best practices and guidelines and here are some points I&#8217;ve faced while my career path which may help.

**Functions and procedures:**  
Function names should be descriptive as you can understand what it&#8217;s doing even by reading its name. Function name should not belong and it&#8217;s preferred to start by a verb. For example, using the following function is a bad practice &#8220;_check\_valid\_membership\_data\_for_user_&#8221; you may use such name &#8220;_validate_membership_&#8220;.

If you&#8217;re working with classes do not use the class name within the names of your functions (function for sure it belongs to its class so no need to replicate such info).  
For example, if you have a &#8220;_User_&#8221; class creating a function with the following name is a bad experience &#8220;_get\_user\_payments_&#8221; but the best name for such function is &#8220;_get_payments_&#8221; as you&#8217;ll use it as follows within your code &#8220;_$user->get_payments_&#8220;.

Camel-case or underscored! yeah, it&#8217;s one of the annoying experiences to have camel-case underscored mixed code. If you&#8217;re working within a team you&#8217;ve to agree on which type of naming conventions you need to work with. I&#8217;ve faced such a case lately while working with <a title="Peter" href="https://twitter.com/peter_yanni" target="_blank" rel="noopener">Peter</a>. He suggested using underscores while naming our method and variables. At the first, I saw that it&#8217;s useless to do so (as I love the came-cased methods). After some point in time, I was reading a class in which we&#8217;ve applied such convention and then compared it with and old version of code. I smiled and said yup you were right <a title="Peter" href="https://twitter.com/peter_yanni" target="_blank" rel="noopener">Peter</a>(he won the land this time :D).

**The naming convention for variables and properties:**  
Well, who doesn&#8217;t use a variable in his code, the answer is no one but who is writing non-readable or even understandable variable names, then the answer is everyone. When you ask a developer why you did so he&#8217;ll surely say “Man I got stuck with a new release and had a very long backlog how come to care about a useless variable name. That may consume a lot of time” (actually I was one of those fools who do so). BTW it&#8217;s not useless to care about variable names and yup it deserves to invest a minute to think about a descriptive name. I&#8217;ve read some old articles that agreed if you&#8217;re working as an individual or a freelance developer it&#8217;s useless to care about naming conventions. I can see that it&#8217;s wrong. If you look back to see the old code you&#8217;ve written 2 months ago you&#8217;ll never remember why the hell you&#8217;ve written such a variable name. So it deserves taking a minute to think about it.  
**Managing dependencies:**  
One of the most things that annoy me is working with lots of dependencies within a project without having a dependency manager that handles such annoying tasks of updating and getting the chain of dependencies. For example: using _bootstrap_ within your frontend code. If you&#8217;ve downloaded bootstrap manually you&#8217;ll end up downloading _jquery_ too. And the later _bootstrap_ versions cares about the minimum version of _bootstrap_. And here we go, we&#8217;ve to get the proper _jquery_ version. That was a simple example. If you&#8217;re working with a complicated dependency that has a long chain of other dependencies this will be very annoying to care about each version. Using dependency managers like bower (in frontend) and composer (for backend) will help you to have free nightmares sleep.

**Loops and control structures:**  
loops, if statements and loops and even more if statements, ugf I cannot read such code, who&#8217;s the asshole who wrote that shittttttt!. Lots of us faced such problem when reading not well-written code. Using loops and control structures is a mixed blessing. And to avoid being an asshole. You have to care not to have lots and lots of nested loops and control flow items within your code. Suppose having such code

<p style="text-align: center;">
  <div class="dm-code-snippet dark default " style="background-color:#000;">
    <div class="control-language language-php">
      <div class="dm-buttons">
        <div class="dm-buttons-left">
          <div class="dm-button-snippet red-button">
          </div>
          
          <div class="dm-button-snippet orange-button">
          </div>
          
          <div class="dm-button-snippet green-button">
          </div>
        </div>
        
        <div class="dm-buttons-right">
          <a id="dm-copy-raw-code"> <span class="dm-copy-text">Copy Code</span> <span class="dm-copy-confirmed" style="display:none">Copied</span> <span class="dm-error-message" style="display:none">Use a different Browser</span></a>
        </div>
      </div>
      
      <pre>
					<code id="dm-code-raw" class="wrap">&lt;pre>&lt;/p>
&lt;pre class="dm-pre-admin-side">foreach(............){
    if(..................){
        switch(......){
            case 1:
                foreach(.........){

                }
            break;
            …..
       }
    }
}
&lt;/pre>
&lt;p>&lt;/pre></code>
				</pre>
    </div>
  </div>
</p>

This is a bad experience to have such a code. Having 3 nested indentations is enough to have a readable code. So please do not write that shitty eye-bleeding code that has lots and lots of nested blocks.

The previous notes are not rules that have to be followed when writing code, they&#8217;re just best practices I&#8217;ve come up with. You build up better rules for better code. Just set your own rules and follow them.