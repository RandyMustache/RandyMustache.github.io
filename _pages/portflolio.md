---
title: Latest Posts
permalink: "/portfolio/"
layout: archive
---

<div class="tiles">
{% for post in site.posts %}
{%if post.portfolio == 'portfolio' %}
	{% include post-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->