---
layout: post
title:  "Introducing Boston Ipsum"
date: 2016-01-06 09:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 8
feature_image: leafy-bench
show_related_posts: false
square_related: recommend-wolf
---

Introducing the Boston Ipsum Ruby Gem.

*What is a RubyGem?*

A Rubygem is a bit of code that a ruby developer wrote, made available in a portable format and posted to a public server, so that bit of code can be used on other machines and by other developers in different web projects. If you were to think of web development as building digital things with digital Legos (And you might not be too far off, frankly), you could imagine a Rubygem as being a specific Lego that performs a specific function. Some Rubygems allow you to send email, upload images, or even display a profile picture based on your email address. This Rubygem that I created displays Boston themed "Lorem Ipsum" text.

*What is Lorem Ipsum?*

Lorem Ipsum is "filler text" used by print and web developers to take space up on a page with text so that he or she can get an idea of what the page will look like once the marketing text gets finished by the marketing department. For example, on the home page at http://JesseWaites.comyou can see that I have a small bio section on the left side. If I were still working on the bio, I could add some filler text there to take up 2 or 3 sentences and get a good idea of how much space it would take up on the page.

I wanted to experiment with making a Ruby gem, as I had never made one before, so I created a rather simple Lorem Ipsum generator that returns Boston area themed text.

Rubygems link: https://rubygems.org/gems/boston_ipsum/versions/1.5.5

You simply install the gem, bundle, and call:

{% highlight Ruby %}
<%= BostonIpsum.speak(integer) %>  
{% endhighlight %}

in any view. The integer number allows you to return a randomized yet specific number of words. To add words, make a pull request.

For example,
{% highlight Ruby %}
<%= BostonIpsum.speak(2) %>
{% endhighlight %}
could output "Patriots Somerville", and

{% highlight Ruby %}
<%= BostonIpsum.speak(4) %>
{% endhighlight %}
could output "Sox Eastie Southie MBTA"

Installation:

Add this line to your application's Gemfile:

gem 'boston_ipsum'

And then execute:

$ bundle

Or install it yourself as:

$ gem install boston_ipsum

Usage:

Simply add:

{% highlight Ruby %}
<%= BostonIpsum.speak(5) %>
{% endhighlight %}
into any view after requiring and bundling the gem into your ruby project.

To add Boston themed words to the list, simply add them and make a pull request on Github.

[Here's the Github link.](https://github.com/piratebroadcast/BostonIpsum)
