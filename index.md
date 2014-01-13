---
layout: default
title: Journal
description: Gedanken an der Schnittstelle von Kunst, Technologie und allem anderen. Von Thomas Gerstendörfer.
---

{% for post in site.posts %}
# [{{ post.title }}]({{ post.url }})

{{ post.excerpt | strip_html | truncatewords: 40 }}
<span class="post-date">{{ post.date | date: "%d.%m.%Y" }}</span>
{% endfor %}

<p style="margin-top: 20px;" class="nav"><a type="application/atom+xml" href="/feed.xml">Atom Feed</a></p>
