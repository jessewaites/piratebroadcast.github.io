---
layout: post
title:  "Theatre JS Demo"
date: 2016-07-14 09:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 3
feature_image: theatre
show_related_posts: false
square_related: recommend-wolf
---

<p>Recently, I discovered a cool little library called TheatreJS, created by Gabin Aureche. This library adds a typing effect mimicking typing human behavior in real time. I love libraries like this because it is a really creative way to get your users attention. It is great to be reminded that web developers can do very, very creative things online. I'd love to made a demo of a rap or rock song duet if I ever have the time! I added a demo below that I lifted from Gabin's Codepen demo.</p>

[Here is the project on Github](https://github.com/Zhouzi/TheaterJS), and you can follow Gabin [here on Twitter.](https://twitter.com/Zh0uzi/)


<style>
.actor {
  font-size: 2.8rem;
  display: flex;
  margin-bottom: $spacing;

  &:last-of-type {
    margin-bottom: $spacing-large;
  }
}

.actor__content {
  flex-grow: 1;
}

@keyframes blink {
  from { opacity: 0; }
  to { opacity: 1; }
}

.actor__content--typing::after {
  content: '|';
  animation: blink 500ms infinite;
}
</style>

<p>Without further ado, the demo:</p>

<br>

<main class="scene">
  <div class="actor">
    <div class="actor__prefix">-</div>
    <div id="vader" class="actor__content"></div>
  </div>

  <div class="actor">
    <div class="actor__prefix">-</div>
    <div id="luke" class="actor__content"></div>
  </div>
</main>

<br>
<br>

<iframe height='319' scrolling='no' src='//codepen.io/Zhouzi/embed/JoRazP/?height=319&theme-id=0&default-tab=html&embed-version=2' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/Zhouzi/pen/JoRazP/'>TheaterJS</a> by Gabin Aureche (<a href='http://codepen.io/Zhouzi'>@Zhouzi</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

<script src="//cdn.jsdelivr.net/theaterjs/latest/theater.min.js"></script>

<script>
var theater = theaterJS()

theater
.on('type:start, erase:start', function () {
  theater.getCurrentActor().$element.classList.add('actor__content--typing')
})
.on('type:end, erase:end', function () {
  theater.getCurrentActor().$element.classList.remove('actor__content--typing')
})
.on('type:start, erase:start', function () {
  if (theater.getCurrentActor().name === 'vader') {
    document.body.classList.add('dark')
  } else {
    document.body.classList.remove('dark')
  }
})

theater
.addActor('vader', { speed: 0.8, accuracy: 0.6 })
.addActor('luke')
.addScene('vader:Luke.', 600)
.addScene('luke:What?', 400)
.addScene('vader:I am your father.', 400)
.addScene('luke:Nooo...', -3, '!!! ', 600, 'No! ', 600)
.addScene('luke:That\'s not true!', 600)
.addScene('luke:That\'s impossible!', 400)
.addScene('vader:Search your feelings.', 1600)
.addScene('vader:You know it to be true.', 1000)
.addScene('luke:Noooooooo! ', 600, 'No!', 400)
.addScene('vader:Luke.', 600)
.addScene('vader:You can destroy the Emperor.', 1600)
.addScene('vader:He has foreseen this. ', 800)
.addScene('vader:It is your destiny.', 1600)
.addScene('vader:Join me.', 800)
.addScene('vader:Together we can rule the galaxy.', 800)
.addScene('vader:As father and son.', 1600)
.addScene('vader:Come with me. ', 800)
.addScene('vader:It is the only way.', 2000)
.addScene(theater.replay.bind(theater))
</script>
