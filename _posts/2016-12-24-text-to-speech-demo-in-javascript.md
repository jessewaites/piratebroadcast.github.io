---
layout: post
title:  "Text To Speech Demonstration using Javascript"
date: 2016-12-20 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 2
feature_image: macbook
show_related_posts: false
square_related: recommend-wolf
---
<p>Here's a demo of the experimental "SpeechSynthesisUtterance" interface of the Web Speech API.
It should be noted that this does not currently work on mobile devices.</p>

  <label for="rate">Select a Voice:</label>
  <select name="voice" id="voices" class="form-control">
    <option value="">Select A Voice</option>
  </select>


  <label for="rate">Rate:</label>
  <input name="rate" type="range" min="0" max="3" value="1" step="0.1">

  <label for="pitch">Pitch:</label>

  <input name="pitch" type="range" min="0" max="2" step="0.1">
  <br>
  <textarea class="form-control" rows="5" name="text">Press Speak now, or change this text first, then press the green button 👍</textarea>
  <br>

  <button id="speak" class="btn btn-success">Speak</button>
  <button id="stop" class="btn btn-danger">Stop!</button>


<script>
const msg = new SpeechSynthesisUtterance();
let voices = [];
const voicesDropdown = document.querySelector('[name="voice"]');
const options = document.querySelectorAll('[type="range"], [name="text"]');
const speakButton = document.querySelector('#speak');
const stopButton = document.querySelector('#stop');
msg.text = document.querySelector('[name="text"]').value;

function populateVoices() {
voices = this.getVoices();
voicesDropdown.innerHTML = voices
  .filter(voice => voice.lang.includes('en'))
  .map(voice => `<option value="${voice.name}">${voice.name} (${voice.lang})</option>`)
  .join('');
}

function setVoice() {
msg.voice = voices.find(voice => voice.name === this.value);
toggle();
}

function toggle(startOver = true) {
speechSynthesis.cancel();
if (startOver) {
  speechSynthesis.speak(msg);
}
}

function setOption() {
console.log(this.name, this.value);
msg[this.name] = this.value;
toggle();
}

speechSynthesis.addEventListener('voiceschanged', populateVoices);
voicesDropdown.addEventListener('change', setVoice);
options.forEach(option => option.addEventListener('change', setOption));
speakButton.addEventListener('click', toggle);
stopButton.addEventListener('click', () => toggle(false));

</script>
