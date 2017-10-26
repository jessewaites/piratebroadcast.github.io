---
layout: post
title:  "Redirecting To An External Link In A React Application"
date: 2017-10-26 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 2
feature_image: detour
show_related_posts: false
square_related: recommend-wolf
---
<p>Recently, I was working on a React Application and wondered how I could link to an external web page. I was learning the in's and out's of React Router and decided to figure it out. (If you haven't figured it out yet, that's the best way to learn: Have an idea and work on it until you implement it.)</p>

<p>A React focused internet forum directed me to look at the the Redirect
function of the React Router, so I started there. I created my component, imported it into Index.js, but for the life of me I couldn't get it to work. The issue is that Redirect is for internal links only. Going from /Posts to /Users, for example. (It seems kind of obvious in retrospect.) I deleted the component and reverted the rest of my work and kept up the research.<p>

<p>The solution to this wasn't obvious so I thought to write this blog post and document this simple solution so that others can find it. Without further ado...

It turns out that what I wanted to do was use an inline component and window.location to force the browser to go to another page. I'll paste a gist below so you can see how I set my React Router up in Index.js. This definitely works with React Router 3 and 4. If this was useful to you, send me an email or follow me and let me know to keep it up.<p>

<script src="https://gist.github.com/piratebroadcast/ff057097328b823251b3976117404934.js"></script>
