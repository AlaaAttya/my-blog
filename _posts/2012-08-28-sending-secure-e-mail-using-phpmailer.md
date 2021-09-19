---
id: 61
title: Sending secure e-mail using PHPMailer
date: 2012-08-28T15:53:09+00:00
author: alaa
layout: article
guid: http://alaaattya.wordpress.com/?p=61
permalink: /?p=61
categories:
  - Uncategorized
---
Hi guys,

Here a new PHP class that helps you to send emails securely. This may be so helpful for those who need a contact us or newsletter forms.  
This class can send emails using three different ways (via SMTP server, via qMail MTA or via sendmail command).

This differs from the ordinary php mail function. If anyone tried before to use php mail function you&#8217;ll find your message in the junk not inbox and you may wonder why this happens. It happens because the mail server did not trust the sender so it see&#8217;s your message as spam message and places it in the junk.  
PHPMailer uses a secure way to send emails. Here i&#8217;ll show you the most important functions that you may use it frequently.

All You need to configure PHPMailer is to download the source files from this <a href="http://code.google.com/a/apache-extras.org/p/phpmailer/" title="PHPMailer" target="_blank" rel="noopener">link</a>

Then extract the files and copy these three files to the place you will include them

class.phpmailer.php  
class.pop3.php  
class.smtp.php

Then just include this class.phpmailer.php file and the configuration is done.

[code]require_once &#8216;class.phpmailer.php&#8217;;[/code]

First you need to create and instance of the PHPMailer class as follows

[code]$email = new PHPMailer();[/code]

To send email via &#8220;SMTP&#8221; you need to call this member function  
[code]$email->IsSMTP();[/code]

To send email via &#8220;qMail MTA&#8221; you need to call this member function  
[code]$email->IsQmail();[/code]

To send email via &#8220;sendmail command&#8221; you need to call this member function  
[code]$email->IsSendmail();[/code]

Then if you need to enable email authentication you can call this member function  
[code]$email->SMTPAuth = true;[code/]

Some mail servers will require "SSL" for secure email sending (like Google) so you can call this member function to enable "SSL"  
[code]$email->SMTPSecure = &#8216;ssl&#8217;;[/code]

For &#8220;SMPT&#8221; you need to specify the &#8220;SMPT server&#8221; so you can call this function  
[code]$email->Host = &#8216;smtp.gmail.com&#8217;;[/code]

Actually PHPMailer uses the 465 port to send emails so you can specify it using this function  
[code]$email->Port = 465;[/code]

In case if you had an error in sending email you can view this error using this function  
[code]$email->ErrorInfo;[/code]

Here i had written a function that you can use to send emails using PHPMailer all you need is to pass it some usual arguments to specify the sender and the reciever emails, body, subject and sender name

[code]

<?php 

require_once &#8216;class.phpmailer.php&#8217;;

//setting up Authentication info.  
$authMail = &#8216;YourMailGoesHere@gmail.com&#8217;;  
$authPass = &#8216;Your Password Goes Here&#8217;;

define(&#8216;mail&#8217; , $authMail);  
define(&#8216;password&#8217; , $authPass);

function sendEmail($to, $from, $from_Name, $body, $subject)  
{  
$email = new PHPMailer();

$email->IsSMTP(); // enable SMTP to  
$email->SMTPDebug = 0; // debugging: 1 = errors and messages, 2 = messages only  
$email->SMTPAuth = true; // authentication enabled  
$email->SMTPSecure = &#8216;ssl&#8217;; // secure transfer enabled REQUIRED for GMail  
$email->Host = &#8216;smtp.gmail.com&#8217;; //specifying SMTP mail server  
$email->Port = 465;  
$email->Username = mail;  
$email->Password = password;  
$email->SetFrom(mail, $from_Name);  
$email->Subject = $subject;  
$email->Body = $body;  
$email->AddAddress(mail);  
if(!$email->Send()) { //call $email->Send() to send emails  
$error = &#8216;Mail error: &#8216;.$email->ErrorInfo;  
echo $error;

return false;  
} else {  
$error = &#8216;Message sent!&#8217;;  
echo $error;

return true;  
}

}

?>  
[/code]

Hope you enjoyed 🙂