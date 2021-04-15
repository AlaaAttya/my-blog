---
id: 101
title: Solving PHP5.3 properties access using get_object_vars() method
date: 2013-03-12T13:42:20+00:00
author: alaa
layout: post
guid: http://alaaattya.wordpress.com/?p=101
permalink: /?p=101
publicize_twitter_user:
  - AlaaAttya
publicize_reach:
  - 'a:2:{s:7:"twitter";a:1:{i:1094482;i:127;}s:2:"wp";a:1:{i:0;i:6;}}'
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:8:"30373923";s:7:"blog_id";s:8:"30897336";s:9:"mod_stamp";s:19:"2013-03-12 18:13:19";}'
categories:
  - php
  - Web Development
tags:
  - php bug issue
  - php5.3
  - web development
---
Hello PHPians 😀

While working on a project i&#8217;ve face a bug in php5.3. In PHP4 [code]get\_object\_vars($obj);[/code] was returning only public proprties of the object while in php5.3 it&#8217;s also returning private properties.  
For example if you try to run this code  
[code]  
<?php  
class user{  
public $username=&#8221;alaa&#8221;;  
private $password=&#8221;1234&#8243;;

function get_user()  
{  
var\_dump(get\_object_vars($this));  
}  
}

$user_data = new user();  
$user\_data->get\_user();  
?>

[/code]

output will be:  
[code]

array  
&#8216;username&#8217; => string &#8216;alaa&#8217; (length=4)  
&#8216;password&#8217; => string &#8216;1234&#8217; (length=4)  
[/code]

Actually it&#8217;s not the end of the story. There&#8217;s a class that will got this bug solved. This magical class is called &#8216;ReflectionObject&#8217; class.

you can use this handy function which takes an object as a parameter and returns and object contains only the public properties.

<div class="dm-code-snippet dark default " style="background-color:#abb8c3;">
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
					<code id="dm-code-raw" class="no-wrap">&lt;pre>&lt;/p>
&lt;pre class="dm-pre-admin-side">/**
* return the public properties only, solving php5.3 bug issue
*/
function my_get_object_vars($obj) {
    $ref = new ReflectionObject($obj);
    $pros = $ref -&gt; getProperties(ReflectionProperty::IS_PUBLIC);
    $result = array();
    foreach ($pros as $pro) {
        false && $pro = new ReflectionProperty();
        $result[$pro -&gt; getName()] = $pro -&gt; getValue($obj);
    }

    return $result;
}&lt;/pre>
&lt;p>&lt;/pre></code>
				</pre>
  </div>
</div>

now you can modify your class to test the function to be as follows

[code]  
<?php  
class user{  
public $username=&#8221;alaa&#8221;;  
private $password=&#8221;1234&#8243;;

function get_user()  
{  
var\_dump(my\_get\_object\_vars($this));  
}  
}  
/**  
* return the public properties only, solving php5.3 bug issue  
*/  
function my\_get\_object_vars($obj) {  
$ref = new ReflectionObject($obj);  
$pros = $ref -> getProperties(ReflectionProperty::IS_PUBLIC);  
$result = array();  
foreach ($pros as $pro) {  
false && $pro = new ReflectionProperty();  
$result[$pro -> getName()] = $pro -> getValue($obj);  
}

return $result;  
}

$user_data = new user();  
$user\_data->get\_user();  
?>

[/code]

and auto-magically this will solve your bug 🙂  
and here&#8217;s the output

[code]  
array  
&#8216;username&#8217; => string &#8216;alaa&#8217; (length=4)  
[/code]

Hope you enjoyed, thanks 🙂