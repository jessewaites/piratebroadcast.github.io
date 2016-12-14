---
layout: post
title:  "Javascript Drum Machine Demo"
date: 2016-10-17 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 3
feature_image: drum
show_related_posts: false
square_related: recommend-wolf
---

<style>
.keys {
  display:flex;
  flex:1;
  min-height:20vh;
  align-items: center;
  justify-content: center;
}

.key {
  border:4px solid black;
  border-radius:5px;
  margin:1rem;
  font-size: 1.5rem;
  padding:1rem .5rem;
  transition:all .07s;
  width:100px;
  text-align: center;
  color:white;
  background:rgba(0,0,0,0.4);
  text-shadow:0 0 5px black;
}

.playing {
  transform:scale(1.1);
  border-color:#ffc600;
  box-shadow: 0 0 50px #ffc600;
}

kbd {
  display: block;
  font-size: 40px;
}

.sound {
  font-size: 5.2rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  color:#ffc600;
}
</style>

<div class="keys">
    <div data-key="65" class="key">
      <kbd>A</kbd>
      <span class="sound"></span>
    </div>
    <div data-key="83" class="key">
      <kbd>S</kbd>
      <span class="sound"></span>
    </div>
    <div data-key="68" class="key">
      <kbd>D</kbd>
      <span class="sound"></span>
    </div>
    <div data-key="70" class="key">
      <kbd>F</kbd>
      <span class="sound"></span>
    </div>
    <div data-key="71" class="key">
      <kbd>G</kbd>
      <span class="sound"></span>
    </div>
    <div data-key="72" class="key">
      <kbd>H</kbd>
      <span class="sound"></span>
    </div>
    <div data-key="74" class="key">
      <kbd>J</kbd>
      <span class="sound"></span>
    </div>
    <div data-key="75" class="key">
      <kbd>K</kbd>
      <span class="sound"></span>
    </div>
    <div data-key="76" class="key">
      <kbd>L</kbd>
      <span class="sound"></span>
    </div>
  </div>


  <audio data-key="65" src="/sounds/clap.wav"></audio>
  <audio data-key="83" src="/sounds/hihat.wav"></audio>
  <audio data-key="68" src="/sounds/kick.wav"></audio>
  <audio data-key="70" src="/sounds/openhat.wav"></audio>
  <audio data-key="71" src="/sounds/boom.wav"></audio>
  <audio data-key="72" src="/sounds/ride.wav"></audio>
  <audio data-key="74" src="/sounds/snare.wav"></audio>
  <audio data-key="75" src="/sounds/tom.wav"></audio>
  <audio data-key="76" src="/sounds/tink.wav"></audio>

  If you're on a laptop, press the letter "A" , then "F" - Cool, right? (This demo works on non-mobile devices only. Sorry, iPhone and Android users.)

  Recently, my friend Ben shared a link to Web Bos' free new Javascript course, Javascript30. I've known Wes' name around for quite a while being that he has
  created what is known as the de facto ReactJs course, so I was curious to what his free course would offer. I've recently decided to give it a spin and was happy to see that the first course is building a javascript drum machine. I've always wanted to build one of these.

  Long story short, you create a directory in your project full of .wav sound files. In your HTML, you have various audio tags - each one has a custom data-key attribute assigned to a different keyboard letter. In your javascript, you have a window listener waiting and watching for keyboard presses. When a key on the keyboard is pushed that corresponds to an audio file, that file is played via the audio HTML API. Otherwise, if a key is pressed that is NOT associated with an audio file, the function is exited and begins again, waiting and listening for the next keypress. I'm happy with Wes' course so far and am looking forward to the rest of it.

  [Click here to see Wes' Javascript30 course.](https://javascript30.com/)



  <script>
    function removeTransition(e) {
      if (e.propertyName !== 'transform') return;
      e.target.classList.remove('playing');
    }

    function playSound(e) {
      const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
      const key = document.querySelector(`div[data-key="${e.keyCode}"]`);
      if (!audio) return;

      key.classList.add('playing');
      audio.currentTime = 0;
      audio.play();
    }

    const keys = Array.from(document.querySelectorAll('.key'));
    keys.forEach(key => key.addEventListener('transitionend', removeTransition));
    window.addEventListener('keydown', playSound);
  </script>
