---
layout: post
title: Jekyll and Website Localization
description: Adapting a multilingual static site to Jekyll
img:
---


\**This post has been edited from its original version since migrating my site to Jekyll*

For my *Website Localization* course's final project, I chose to work with the site-builder, Jekyll. My project was two-fold: what exactly is Jekyll and how does it work, and how could I use the special characteristics of Jekyll to my advantage in site building and localization?
## Background

### Why Jekyll?

Firstly, Jekyll is aimed toward creation of personal sites and portfolios; it’s meant to be clean and easy to understand, and easy to pick up. I thought this would be a good test to see how suitable it'd be for my own personal website. I was keen to find something that wasn’t Wordpress or Drupal as well as test out its localization potential.
In addition, my initial analysis of how Jekyll functioned made me feel that it was a platform that would be easier to add in localized content (when compared with WYSIWYG editors such as Squarespace or Wix).

### So, what is Jekyll?

Jekyll is a static-site builder. At its core basics, it takes the content (written in Markdown) and the layout (written in a mix of HTML and Liquid), puts them together, and creates the corresponding page you see in your browser.
Markdown is a formatting language. If you have used Reddit before to post either a comment or a post, you have encountered Markdown. I like it a lot because it’s easy to read and very easy to pick up. This is what you use to write all of your content.
Markdown works in conjunction with Liquid. Liquid is a templating language, which means it is used in conjunction with HTML (in this case) to build a site layout or template. It has a few similar characteristics to Javascript, a programming language I had experience with at the start of this project.
For both Markdown and Liquid, I did some quick reading and mainly referenced some [cheat](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf) [sheets](https://www.shopify.com/partners/shopify-cheat-sheet). Additionally, I utilized Github, because Github allowed me to host a Jekyll site for free. For a text editor I used Atom as it had a plug-in that integrated well with Github.
 
## Preparation - Turning a previous site into a Jekyll site

Rather than building a completely new Jekyll site from scratch, I took a static website built previously during the course and turned that into a Jekyll site. I was able to immediately apply my newly-acquired knowledge of Liquid, as I had to modify or adapt some aspects of the static site so that it would function the same in Jekyll. Additionally, each English content page had to have its corresponding Japanese content page, which were stripped of their HTML tags and rewritten into Markdown.


## Localization

### Before localization

Before adding the Japanese site, I did a quick search in case anyone had done this before and had documented it. A very helpful [blog post](https://www.sylvaindurand.org/making-jekyll-multilingual/) by Sylvain Durand came up. This gave me a few insights into how to start my process, but his approach was aimed more toward blog posts and also did not work with the layout of my static site. However, my main takeaway from this was to create a strings YML file for each language, examples of which are below.
<div class="img_row">
  <img class="col three" src="/img/jekyll_01.png">
</div>
<div class="col three caption">Part of the English strings YML file</div>
<div class="img_row">
  <img class="col three" src="/img/jekyll_02.png">
</div>
<div class="col three caption">Part of the Japanese strings YML file</div>
I also added the corresponding Liquid code to the layout HTML file for it to pull the right YML file.

### Building a multilingual Jekyll site


<div class="img_row">
  <img class="col three" src="/img/jekyll_03.png">
</div>
<div class="col three caption">Added code to allow for multiple languages</div>

The code shown above is the part of the code for the menu items. Because of the nature of the layout, the site had a sidebar area with content that also needed to be put into the strings file, making it a little more unwieldy than a site built in Jekyll from the start.

<div class="img_row">
  <img class="col three" src="/img/jekyll_04.png">
</div>
Most importantly, a specific line was added to the header of each .md file.
 
If no language is indicated at all at the top of the md file, the page doesn’t know which strings to load, and so nothing gets loaded at all! Below you can see the empty menu tabs and the empty sidebar.
<div class="img_row">
  <img class="col three" src="/img/jekyll_05.png">
</div>


 
### Switching between languages

For the language switcher, we opted to go for a simple link language picker. Because of how Markdown and Liquid works, adding a reference in each .md file’s header made creating the language picker very simple.
<div class="img_row">
  <img class="col three" src="/img/jekyll_06.png">
</div>


 

## The Finished Product and Takeaways

With that, the website was fully localized. The final setup of files looks like this.
<div class="img_row">
  <img class="col three" src="/img/jekyll_07.png">
</div>


You can check out the project [here](https://sugarfins.github.io/2017WebLocProject/)

Although it took some time to learn and setup, overall my experience with Jekyll is a positive one. I like the versatility that comes with it not being a CMS, so I can upload my website to any hosting service. Jekyll really is a simple and easy to utilize website builder, and I plan on moving my personal website (currently on Wordpress) to Jekyll in the near future.
