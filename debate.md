---
layout: page
title: Debate
where: Debate
permalink: /debate
desc: Debate stuff
---

# Debate
Posts about debate.

## Cases
{% for post in site.categories["debate_case"] %}
    <li style="color: white;"> <a style="color:cornflowerblue;" href="{{post.url}}">{{ post.title }} </li></a>
{% endfor %}

<br><br>

## Theory

## Values

<h2>Values</h2>
{% for post in site.categories["value"] %}
    <li style="color: white;"> <a style="color:cornflowerblue;" href="{{post.url}}">{{ post.title }} </li></a>
{% endfor %}