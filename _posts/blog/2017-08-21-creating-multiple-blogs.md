---
title: Create multiple blogs on a single instance of Jekyll
date: 2017-08-21 00:00:00 Z
tags:
- development
layout: article
excerpt: ''
---

I am new to Jekyll, so I thought it would be a great idea to document some challenges I have overcome while building this website so other newcomers can learn off my mistakes (they are many).

This one comes from my desire to run multiple "blogs" on this page. Essentially, I wanted an actual blog page, where I could write content like this, and I wanted a portfolio blog page. THe reason being, it would be easier to update new portfolio additions in the blog format, rather than creating a new page, or update the whole page each time. Makes sense.

After some fruitless attempts at solving the issue without any research, or even rudementary understanding of Jekyll, I did some actual Googling, and came across my answer.

<figure>
  <img src="{{ site.url }}/images/multiple-blogs-fail.png" alt="Not like this">
  <figcaption>This is not the answer. Not even a little bit</figcaption>
</figure>




It turns out just making a folder called folder, and renaming things from posts to portfolio isn't the answer. You live and you learn.

The answer so far comes in the form of adding custom paramter in the post so Jekyll knows which post belongs in which blog.

First, in your _posts folder, create a blog folder, and any additional folders you plan to create. This is mostly for you, as Jekyll doesn't care what folders you have, it will find all posts within them and display them normally. If you have existing content you can test this and see.

Next we need to add a little line to the front matter of your page.


<figure>
  <img src="{{ site.url }}/images/portfolio-example.png" alt="Better">
  <figcaption>Better</figcaption>
</figure>


After adding the field portfolio: portfolio to my page, I can now pass that information to Jekyll and create the two pages I want.

For my main blog page, I added the code:

{% raw %}
~~~ruby
{% for post in site.posts %}
{% if post.portfolio != null %}
{% else %}
	{% include post-grid.html %}
{% endif %}
{% endfor %}
~~~
{% endraw %}

And for my portfolio page I added the code:

{% raw %}
~~~ruby
{% for post in site.posts %}
{%if post.portfolio == 'portfolio' %}
	{% include post-grid.html %}
{% endif %}
{% endfor %}
~~~
{% endraw %}

Adjust this according to your chosen theme, as every real life example will be different, but hopefully this helps.