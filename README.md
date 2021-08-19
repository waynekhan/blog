---
layout: default
title: Home
permalink: /
---

Hello, thanks for visiting! You may want to check out some of my content, or [get an RSS feed](/feed.xml) for your favourite reader.

## Posts

{% for post in site.posts limit:50 %}
  [{{ post.title }}]({{ post.url }})
{% endfor %}

## Pages

{% for page in site.pages %}
  [{{ page.title }}]({{ page.url }})
{% endfor %}
