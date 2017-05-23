---
layout: post
title:  "Debug Your Rails Application With This One Weird Trick"
date: 2017-05-23 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 2
feature_image: debug
show_related_posts: false
square_related: recommend-wolf
---
<p>Fate is a fickle mistress. Sometimes you find yourself working in a fresh Rails application, the entire architecture
of which fits inside of your mind. Other times, you find yourself working on a massive project with dozens of interconnecting pieces. I've found myself of the receiving end of the latter rather than the former more often not.
I would sometimes run into a problem where, I would try and save a new instance of an object through a form (called Thing.rb in this example) and the thing just wouldn't save, no matter what I tried. Logs weren't helpful, and Pry wouldn't help because I simply don't know what I don't know.

I could try all kinds of incantations on it and shove the kitchen sink into the object (maybe a validation somewhere I don't know about?) but at the end of the day, you don't know what you don't know.

Then one day I figured out this one weird trick...

Drop a flash notice into the create action that tells me the errors on the object. Using this syntax, it even
comes out in human english so it's useful for your users as well. (Not just us developer types)

Using this technique, I was able to see that the reason my object wasn't saving was that there was a validation being called on it on the model level, even though that association had long been removed. Who knows how long this had been broken in production?

Try dropping the flash message line into your controllers sometime and see if you find it helpful for you as well.

Cheers.

<script src="https://gist.github.com/piratebroadcast/fa56eb3fd9d576f0f1211b2098952b99.js"></script>
