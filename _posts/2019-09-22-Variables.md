---
layout: post
title:  Variables
categories: [lesson]
tag: [basics]
where: Programming
permalink: /:categories/:title:output_ext
desc: Imagine that you pass by a river and you want to get some water for later use. One way of doing that is by storing the water in a container. In programming you don't want to store water but data and you do it by putting it in a variable.
---

## Introduction

Imagine that you pass by a river and you want to get some water for later use. One way of doing that is by storing the water in a container. In programming you don't want to store water but data and you do it by putting it in a **variable**.

Now imagine that you don't want to store water but some other substance that has a complicated name. You can put it in a bottle and if you need it later you know you need that bottle so things become easier.

So a formal definion of a variable can be:

> Variable = symbolic name associated with a value and whose associated value **may** be changed

## Data types

The bottle in which the substance will be stored can have different characteristics. It can be a red bottle, it can be a green bottle and so on. So what bottle will you choose? Most probablly you will choose the bottle that can be used to store that substance and that can be used to do whatever you want to do with it.

In programming it's the same but there are no green bottles there are but there are **data types** . You have a variety of data types, depending on what programming language you are using. I will cover in more depth this subject in the next lesson.

## Naming

You need to follow some rules regarding the naming of the variables. This stuff depends on the programming languages but usually these are the rules:

* You can only use letters, numbers and underscores
* The variable name needs to start with a letter or an underscore
* No keywords (example: you can't name your variable the same as a data type)

Programming languages can be case sensitive, meaing that *this* is not the same as *THIS*.

## Where are variables stored?

This depends on the programming language and its compiler/environment. Usually they are stored either in RAM or in the registers.
I will get into compilers later, for now you just need to know that the variables are stored somewhere in the memory. 

## Declaring variables

Before using a variable the computer first needs to allocate the memory for that variable. It's like before going to a trip you need to prepare yourself. 
In **most** programming languages to declare a variable you do something like this:

> data_type variable_name

### Example

In C, if you want to declare a variable that will store integer values  you do:

{% highlight c %}
int x;
{% endhighlight %}

## Assignment

Usually to store a value into a variable you do somthing like this:

>variable_name = value

### Example

In C if you want to store value *0* into the variable that we've declared previous you do:
{% highlight c %}
x = 0;
{% endhighlight %}

In most programming languages you can do declaration and assignment in the same time:

> data_type variable_name = value

### Example

By combining the two previous examples we get:
{% highlight c %}
int x = 0;
{% endhighlight %}
