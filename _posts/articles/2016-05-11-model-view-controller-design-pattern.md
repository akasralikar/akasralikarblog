---
title: Model View Controller Design Pattern
excerpt: "In this article I am going to explain basic idea behind MVC design pattern. My attempt to explain Model View Controller Design Pattern."
image: 
  feature: mvc_role_diagram.png
  teaser: oie_11134643DjvYMLW6.jpg
tags: [design pattern]
comments: true
featured: true
author: Anirudha Kasralikar
date: 2016-05-08 11:27:43
modified: 2016-05-11 01:27:43
---

Today I am going to discuss about one of common development design pattern named Model View Controller design pattern aka MVC architecture and how it works in the real world. 

{% include toc.html %}

## Introduction: 
 
MVC is a design pattern[^design_pattern]. Although MVC architecture is used by many of the most popular application frameworks like [Symfony](http://symfony.com/ "Symfony"){:target="_blank"}, [CodeIgniter](https://www.codeigniter.com/ "CodeIgniter"){:target="_blank"}, [Laravel ]( https://laravel.com/ "Laravel" ){:target="_blank"}, etc, but it's still a concept which can be confusing sometimes, particularly to new programmers. 

[^design_pattern]: A Design pattern is a code structure that allows for common coding frameworks to be replicated quickly.

<figure>
	<img src="{{ site.url }}/images/frameworks.jpg" alt="MVC Based Frameworks" />
	<figcaption>MVC Based Frameworks.</figcaption>
</figure> 
 
Let's break MVC down into individual pieces, and go through each separately. This will also helps you in seeing the whole picture together and correlate different terms 
 
### Model 
 
This is where application data resides. The model is responsible for managing the data of the application. The model should only be called by the controller and there should not be any interaction with the view. It responds to instructions from the controller. 
 
### View 
 
The view should simply render the template and display any data passed to it by the controller.  A format of presentation of data is decided by controller. Usually views are script based templating systems like HTML, PHP, etc. There should not be any direct communication with models. 
 
### Controller 
 
All of standard frameworks have some kind of routing engine in place which forwards request to controller.   The controller is responsible for processing the incoming requests from the web browser. It receives the input, it validates that input. It communicate with model for data, and then pass that data on to the view for presentation. 

## Features 

MVC is not just a firm set of guidelines, but also an overall architecture. You need to get familiar with it and play with different components.

Imagine if everyone in team built applications using their own choices and imaginations, then if new programmer starts working on a project, he would have no idea where to find features, how to extend the code or fix bugs. It would be nightmare for him to adopt to various types implementations. But With MVC design pattern a new programmer can very quickly identify workflow, where data files are resides and where to update the view pages.  

<div class="notice--success" markdown="1">
#### Key Pointers
* MVC helps achieve two of most important design principle namely [Don't Repeat Yourself - DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself "Don't Repeat Yourself" ){:target="_blank"}  and [Separation of Concerns]( http://en.wikipedia.org/wiki/Separation_of_concerns "Separation of Concerns" ){:target="_blank"}. I suggest that you read introductions to those 2 topic.
* It allows you to logically organize different types of code so that it can also be understood by other programmers. So major benefit is easier code maintenance.  
* Last but not the least the most important benefit of MVC architecture is Isolation of business logic from the UI ( user interface ).  
</div>

## Analogy 
 
Few days back I came across cool analogy for understanding the Model View Controller design pattern.  

<figure class="third">
  <img src="{{ site.url }}/images/th.jpg" alt="Chef">
  <img src="{{ site.url }}/images/Tisch-lineart.png" alt="Table">
  <img src="{{ site.url }}/images/waiter.gif" alt="Waiter">
  <figcaption>MVC as Restaurant</figcaption>
</figure>

<div class="notice" markdown="1">
#### MVC as Restaurant
Consider that whole MVC architecture is a restaurant. The chef is a the model whose role is to get orders from waiter and then prepare dishes in kitchen.  The waiter is the controller, who takes orders from the table's / customer's, then informs the chef about it, and finally brings the meal back to the table / customer.  The glorious table is the view, which simply holds the meal and take care of user interface. 
</div>

There is another analogy you can refer [here](http://blog.codinghorror.com/understanding-model-view-controller/ "understanding-model-view-controller"){:target="_blank"}, it considers MVC architecture  as Rendering of web page in browser. In this case Model is HTML, View is CSS and controller is browser.  

Making analogies will not guarantee that you get complete understanding of MVC  design pattern, but it helps in correlating real world scenarios with these abstract terms.

## Limitations 
 
MVC is primarily a UI related design pattern, which means it cannot be used for command line tools, utility programs, etc. Also it is complex to implement especially for smaller applications and affect performance in such cases. 
Because view and controller are closely coupled, modification to one affect the other. Also any changes to model will call for changes to controller and view. 

<!---
## Example 
 
I presume you have hands on experience with [PHP]( http://php.net/ "PHP" ){:target="_blank"} programming language and its echo system to understand examples given below.  
-->

## Conclusion 
I hope that you now have a more clear idea of how the Model View Controller design pattern works and how you can implement it in your applications. 
 
 
