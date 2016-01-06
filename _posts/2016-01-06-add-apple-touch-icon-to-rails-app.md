---
layout: post
title:  "Add an Apple Touch Icon to a Ruby App"
date: 2016-01-06 012:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 3
feature_image: icons
show_related_posts: false
square_related: recommend-wolf
---

This website runs on the Jekyll framework, which is a Ruby based blogging platform invented by Tom Preston-Werner, the founder of GitHub.
After getting this website styled and configured the way I wanted to, I wanted to add some personal touches to it, so I added an Easter Egg and decided to add my Avatar as an apple touch icon, so if someone were to add it to their homescreen (which would never, ever happen), it would have a corresponding app icon. Pretty fancy, like so:

![Icon in Action](http://i.imgur.com/Rru5zJX.png)


Ok, lets do this.

Create a square 180 x 180 pixel image graphic in .png format using your design, logo, whatever. Next, name the image "apple-touch-icon.png" and save it. You can use the Preview program in the Mac to easily do this.

Now upload the image to your Ruby or Rails app - You can do this by opening 2 different Finder windows locally and draggin' it on over from your Desktop or wherever to your images folder. In this example, since this is a Jekyll app, I moved it to the Img folder.

Lastly, add this HTML to the header of your site before the closing </head> tag, without the outer, external quote marks:

{% highlight HTML %}
"<link rel="apple-touch-icon" href="img/apple-touch-icon.png">"
{% endhighlight %}

I've noticed a lot of major sites aren't doing this but details matter, so take a few minutes and give it a shot.

Cheers.
