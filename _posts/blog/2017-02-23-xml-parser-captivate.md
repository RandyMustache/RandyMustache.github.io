---
title: XML Parser for Captivate
date: 2017-02-23 00:00:00 Z
categories:
- Captivate
- Development
layout: article
description: 
image: 2017-02-23-xml.jpg
---

## XML Parser for Captivate

![Screenshot of XML Parser](/assets/images/2017-02-23.png)

Let me start off by saying, forgive the boring name.

I understand this problem might be limited in scope, but it's something my team kept encountering when developing Captivate projects started by another team.

Basically, we are provided with Captivate development files, that include all the slides, and all the text for the project, and we then edit them into something actually watchable. That's the fun part.

The not so fun part is that we need the text within the development files to be separated from Captivate, and placed into another tool for our final delivery. Captivate provides several options for exporting text, but if you've used them before, they are quite awful. 

Especially considering our Captivate workflow works like this: 

![Captivate TTS Dialogue](/assets/images/tts.PNG)

As you can see, we often work with multiple lines of captions for a single slide, and then we break out those caption lines into a separate field to work on the text to speech. This lets us use VTML and the likes to control text to speech speed and pronunciation, without affecting the final captions.

Captivate doesn't care about easy workflow though, Captivate hates it. So when you export the text in a word file, it gives you absolutely everything. Yay! So this is no better than just copy pasting from each and every slide.

This is what led me to create this tool for reading the XML for you, and then printing out a formatted, readable version of the text. 

It uses the rendered speech as the text that it uses, so it overcomes any issues with VTML, or having multiple lines of text, or having actual notes in your slide notes. I also found Captivate exports all the text within shapes, etc. 

So instead of having to wade through an XML sheet of sheer insanity, I did it for you.

I'd love to find time to add features like turning the file back into XML captivate can read so you can download the text, edit it, transate it, etc and then publish it straight back to your project and have it appear exactly where you left off.
Let me know if it helps!
I'd also be keen to look into making a version that's available on the web, but at the time it was easiest to do it with the .net framework.

Download the source files here, and contribute if you can! (Requires Visual Studio)

[GitHub Repo](https://github.com/RandyMustache/XMLParser) 
