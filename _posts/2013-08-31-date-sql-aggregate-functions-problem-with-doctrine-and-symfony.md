---
id: 116
title: Date SQL aggregate functions problem with doctrine and symfony
date: 2013-08-31T16:05:50+00:00
author: alaa
layout: article
guid: 116
publicize_twitter_user:
  - AlaaAttya
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";i:0;s:6:"author";s:8:"30373923";s:7:"blog_id";s:8:"30897336";s:9:"mod_stamp";s:19:"2013-08-31 16:05:50";}'
categories:
  - Symfony
  - Web Development
tags:
  - Database
  - doctrine
  - php
  - symfony
  - web development
---
Hello GEEKs hope you are having a good day,

If you are a symfony developer you may have noticed that you&#8217;ll not be able to use sql Date functions (date, year, month, day) with doctrine. You&#8217;ll need to write an SQL query to do so and fall in the problem of mapping the results to entity. Actually i hate doing this.

While Googling i&#8217;ve found a doctrine extension which does that heavy task smoothly

https://github.com/beberlei/DoctrineExtensions

which you can easily install via composer.json just add &#8216;&#8221;beberlei/DoctrineExtensions&#8221;: &#8220;dev-master&#8217; to the required dependencies.

to use it you can just you the following snippet

```php

public function getTodaysUsers($date) {

	$emConfig = $this->getEntityManager()->getConfiguration();  
	$emConfig->addCustomDatetimeFunction(&#8216;YEAR&#8217;, &#8216;DoctrineExtensions\Query\Mysql\Year&#8217;);  
	$emConfig->addCustomDatetimeFunction(&#8216;MONTH&#8217;, &#8216;DoctrineExtensions\Query\Mysql\Month&#8217;);  
	$emConfig->addCustomDatetimeFunction(&#8216;DAY&#8217;, &#8216;DoctrineExtensions\Query\Mysql\Day&#8217;);

	$qb = $this->createQueryBuilder(&#8216;e&#8217;)  
	->select(&#8216;e&#8217;)  
	->where("DAY(e.registeredAt) = :day")  
	->andwhere("MONTH(e.registeredAt) = :month")  
	->andwhere("YEAR(e.registeredAt) = :year");

	$qb->setParameter(&#8216;year&#8217;, $date->format(&#8216;Y&#8217;))  
	->setParameter(&#8216;month&#8217;, $date->format(&#8216;m&#8217;))  
	->setParameter(&#8216;day&#8217;, $date->format(&#8216;d&#8217;));

	return $qb->getQuery()->getResult();  
}  
``` 

It&#8217;s an example for finding the today&#8217;s registered users. Only you&#8217;ll have to place this method to your Entity&#8217;s repository and here you are ready to go

Hope you&#8217;ve enjoyed,

Thanks 🙂