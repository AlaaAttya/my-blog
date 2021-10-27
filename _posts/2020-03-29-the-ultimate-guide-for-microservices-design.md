---
id: 132
title: The ultimate guide for Microservices’ design
date: 2020-03-29T19:13:07+00:00
author: alaa
layout: article
guid: 132
categories: microservices
tags:
  - 'microservices'
  - 'software-engineering'
  - 'system-design'
  - 'software-architecture'

key: the-ultimate-guide-for-Microservices
---
The Process of defining/designing a microservice's architecture is always painful and flaky. I used to read the word "make it small", "make it simple" and all those kinds of microservices stereotypes. But how to measure how small is small? or how simple it is that simple.

**So I started doing research to define a strict guideline for how to define your system as a list of collaborative microservices and it worked for me.**

Hint: I believe that if you are starting to build a new service from scratch you should not pick microservices. Microservices come as a step after having your service alive and you totally understand every single part of it. Also, your team grows at that point there's a solid need to go for microservices.

*If you can’t build a well-structured monolith, what makes you think you can build a well-structured set of microservices? — distrubuted big balls of mud by: Simon brown*


Also, Martin Fowler has a strong opinion regarding this

*- Almost all the successful microservice stories have started with a monolith that got too big and was broken up*
*- Almost all the cases where I’ve heard of a system that was built as a microservice system from scratch, it has ended up in serious trouble. — Monolith first by: Martin Fowler*


In this article, we might be applying some concepts from domain-driven-design (DDD). But it’s not a prerequisite to have previous knowledge about it.


####So, what is a service?

the best definition that I always liked to define the word service is A stand-alone, independently deployable software component.


We'll be listing the steps to be followed to define your system as a list of services collaborating together.
I’ll be using an example of building a social network.
In my blog post, I will specify the steps/checklist you need to follow, and I will define the output format for each step.

####1. Identifying system operations

In this step, your team should collaborate together to define your service’s operation. This should be the starting point at any service’s life cycle.
System operations are usually operations to be done between domain models. So the first step in this process is to define the high-level domain models.
Hight-level domain models are not related to what will be implemented, they are much simpler.

System operations could with either **command** or **query**.

- **Commands** are those operations related to create, update, delete
- **Queries** are those operations related to query/read data. Example queries are: find a user, get pending orders, get paid transactions,…


The easiest way to define system operations is to use the “Given, when, then” format.

Martin Fowler has published a very nice article that has extensive information about that format for specifying system behavior/operation. https://martinfowler.com/bliki/GivenWhenThen.html


#### To summarise it

Each operation should have an Actor, who will be performing this operation. To define any system operation we should have the state/pre-condition before executing the operation which is defined by the Given block. Given could consist of multiple states/pre-conditions. Then it comes to the When block which defines that operation/behavior that we need to define. The last thing is the Then block, which describes the state of the system after applying/executing that operation we are trying to define.
An example to describe an operation of user reset password


**Feature**: User password reset
**Actor**: User
**Given that**
— I’m logged in to my account
— and I’ve landed on my profile page
**When**
— I change my password
**Then**
— I should receive a password reset email.
— And email should contain valid reset password link
— And I could able to use this link for one time


If you need further details you can check Martin Fowler's blog post here,it has more details, https://martinfowler.com/bliki/GivenWhenThen.html


**The output format for this step should be two documents**:

- High-level domain model diagram with some dummy description of how they are linked together. For example below a high-level diagram for a social network.
- The other document would be a list of system operations written in "Given, When, Then" format.


#### 2. Extract domain models/subdomains

This step comes right away after defining all the system operations. At this step, you can start by defining high-level domain models based on the system operations. For example, in the previous system operation, we can obviously define User as a domain model.

Another example of system operation, if we are designing a social network


**Actor**: user
**Given that**
— I’m logged in to my account
**When**
— I try to change my current home city
**Then**
— My friends should be able to view the change in their timeline


From the previous operation, we can identify ***User*** as a domain model and ***Address location*** as a subdomain.


**The output format from this shep could be**:
List of domains and their sub-domains



#### 3. Define specification for system commands

After the previous steps, we should be able also to dig deeper and define the system commands and queries.



You can start by listing all the system commands as a high level. For example


**Actor**: User
**Story**: write a new group post
**Command**: `postToGroup()`
**Description**: write a post to a group I’m a member of


Afterward, you’ll be able to define the specification for that command. For example:

**Operation**: `postToGroup(user id, group id, post)`
**Returns**: `postId`
**Preconditions**:
— User should be logged in
— User should be a member of the group
Postconditions:
— The post was successfully created
— All group members are able to view/interact with the post





