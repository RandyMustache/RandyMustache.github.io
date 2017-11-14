---
title: Creating a Header with a gradient in Sass
date: 2017-11-14
tags:
    - development
    - SASS
layout: article
excerpt: 'Creating a gradient that will work across multiple browsers with transparancy'
image: /2017/Nov/header.jpg
---

Recently I got acquainted with SASS building a new website for my company. Like many before me, I am never looking back. Gone are my nightmare CSS files, replaced with neat folders and lots of smaller files each defining a single page (or part of page). Life is good.

Mixins have been an integral part of the process, they allow me to define larger blocks and reuse them in multiple places with new conditions each time. What a time to be alive. 

A great use of this has been to create a header, that works across browser, and has some legacy support, for a gradiented header. I built this upon several (very similar) answers you can find anywhere on the web, but I wanted to share my experience, so here it is.

Importantly, I needed the header to be transparent in the lower half, transitioning into opaque in the top half. It needed to look like it was part of the hero image when at the top of the page, but not conflict with text as you scrolled on the page.

This was the answer.

In the mixin you define the background for the various browsers, and the variables for each aspect of the gradient. 

'''scss
@mixin linear-gradient($top-color, $bottom-color, $top-opacity, $bottom-opacity) {
  background: -moz-linear-gradient(top, rgba($top-color, $top-opacity) 0%, rgba($bottom-color, $bottom-opacity) 100%); /* FF3.6-15 */
  background: -webkit-linear-gradient(top, rgba($top-color, $top-opacity) 0%, rgba($bottom-color, $bottom-opacity) 100%); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(to bottom, rgba($top-color, $top-opacity) 0%, rgba($bottom-color, $bottom-opacity) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#{ie-hex-str(rgba($top-color, $top-opacity))}', endColorstr='#{ie-hex-str(rgba($bottom-color, $bottom-opacity))}',GradientType=0 ); /* IE6-9 */
}
'''

To use it, you just include this in the class you want to use it in. It's for a header on mine, could be a button on yours.

'''scss
@include linear-gradient(black, grey, 1, 0);
'''

In the brackets you are defining top colour, bottom colour, top transparency and bottom transparency in that order. 

The header I created.

![Gradient Header](images/2017/Nov/hero.jpg)

With scrolling.

![Gradient Header with scrolling](images/2017/Nov/scroll.jpg)