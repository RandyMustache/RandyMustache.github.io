---
layout: archive
permalink: /portfolio/
title: "Latest Posts"
---

<div class="tiles">
{% for post in site.posts %}
{%if post.portfolio == 'portfolio' %}
	{% include post-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->