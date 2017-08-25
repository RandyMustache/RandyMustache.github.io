---
title: Latest Posts
permalink: "/blog/"
layout: archive
---

<div class="tiles">
{% for post in site.posts %}
{% if post.portfolio != null %}
{% else %}
	{% include post-grid.html %}
{% endif %}
{% endfor %}
</div><!-- /.tiles -->