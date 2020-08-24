---
layout: page
title: Blog
where: Blog
permalink: /blog
desc: Robert's blog
---
# Blog

Random stuff

{% for post in site.categories["blog"] %}
    <li style="color: white;"> {{ post.date | date: '%d %B, %Y' }} -  <a style="color:cornflowerblue;" href="{{post.url}}">{{ post.title }} </li></a>
{% endfor %}