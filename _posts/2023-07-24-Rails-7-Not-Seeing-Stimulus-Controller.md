---
layout: post
title:  "How to make Rails 7 recognize your new Stimulus Controllers"
date: 2023-07-24 012:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 4
feature_image: macbook
show_related_posts: false
square_related: recommend-wolf
---

If you are reading this blog post, chances are that a search engine brought you here. You probably created a new stimulus controller for your Rails 7+ app, the system is not recognizing this new file, and you are searching the web for ideas on what might have went wrong.

I recently went through the experience and there was a bit of inaccurate information out there, I decided to make this post to help those facing this issue in the future.

When *manually* creating a new stimulus controller, you also have to add this new file name to the system js manifest in the Index.js file. When you use the Rails Generator to create this file, this step is done for you, but if you create the file yourself (like a lot of us do) then you have to add it to the index.js file yourself.

It is possible to avoid this issue going forward by writing a funciton in index.js to autoload those files, but if you made it this far into this article, chances are y'all do not have that set up. Add your new file to this index.js file and you should be all set.

To test that this fix is working, you can add a console.log inside of the connect function in your new stimulus controller to confirm that the system is seeing your new controller upon page load. 

Hope that helps! 

By the way, I absolutely love working with Rails and Hotwire - Let me know if you or your company does as well! 
