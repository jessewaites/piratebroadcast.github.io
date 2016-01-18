---
layout: post
title:  "Adding Twitter Cards & Facebook Cards to a Jekyll App"
date: 2016-01-18 09:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 7
feature_image: card_preview_jpeg
show_related_posts: false
square_related: recommend-wolf
description : "The easy way to add social cards to your website links."
---

Twitter and Facebook Cards makes it possible to attach images to posts that automatically link to your content. LinkedIn also uses the same "Open Graph" protocol that Facebook uses, so this will work for LinkedIn as well with no additional code needed.

Cards are the difference between pasting a link that is just a link, or having Twitter, Facebook, or LinkedIn scrape for an article title, image, and description. These cards look very professional and studies have proved that they lead to increased content sharing. You would be surprised how many otherwise professional websites and web services overlook this trivial yet effective step. The image below will show you what a Twitter Card looks like - When displayed on Twitter on either a user page or in a feed, the entire image will serve as a clickable hyperlink to the page or post.

![twitter card validation](http://i.imgur.com/otUP8vj.png "twitter card validation")

Interestingly, I found what may be a bug in the Jekyll framework when writing this blog post - When pasting my code sample, a line of code such as "page.title" is being evaluated, so when I paste "page.title", the output on the screen is the actual page title, in this case "Adding Twitter Cards & Facebook Cards to a Jekyll App". This makes it difficult to share code with you but I found a workaround - I'll simply need to share this code as a Github Gist to skip all of that drama. The  code below is for a Jekyll app, but you should be able to convert this to your programming language of choice rather easily, provided that you have access to your page objects. The code is simple if/else conditional statements that should be trivial to convert to use in Django, Drupal, Ruby on Rails, et cetera.


<script src="https://gist.github.com/piratebroadcast/425724b1b5b75ae6c037.js"></script>

Once you've added the code to your site header and pushed those updates to your production server, you can preview what your Cards will look like by pasting a blog post link in the validators below. I should note that I have hardcoded the same image to display whenever any link is posted to my site - This way I always know that SOME image is present. I'm mostly writing about code anyway so having a dynamic image is not important to me.

[You can preview what your Twitter Card will look like by pasting a blog post link here.](https://cards-dev.twitter.com/validator)

[You can preview your Facebook links here.](https://developers.facebook.com/tools/debug/og/object/)
