---
layout: post
title:  "Elizabeth Warren / Coretta Scott King Senate Letter Auto-Reader"
date: 2017-02-08 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 2
feature_image: warren
show_related_posts: false
square_related: recommend-wolf
---
<p>Elizabeth Warren was recently forced from the Senate Floor for reading a letter from Corretta Scott King that reveals how Jeff Sessions has intimidated and frighten elderly black voters in the 1960s. This cannot stand. Feel free to call Senator Mitchell and play the transcript of the letter for him. Simply adjust your settings, dial (202) 224-2541, and press "Play". (This does not currently work on mobile devices.)</p>

  <label for="rate">Select a Voice:</label>
  <select name="voice" id="voices" class="form-control" autofocus>
    <option value="">Select A Voice</option>
  </select>


  <label for="rate">Speech Speed Rate:</label>
  <input name="rate" type="range" min="0" max="3" value="1" step="0.1">

  <label for="pitch">Voice Pitch:</label>

  <input name="pitch" type="range" min="0" max="2" step="0.1">
  <br>
  <label for="rate">Call Senator Mitchell at (202) 224-2541 and press "Play":</label>
  <textarea class="form-control" rows="5" name="text">Dear Senate:

I write to express my sincere opposition to the confirmation of Jefferson B. Sessions as a federal district court judge for the Southern District of Alabama. My professional and personal roots in Alabama are deep and lasting. Anyone who has used the power of his office as United States Attorney to intimidate and chill the free exercise of the ballot by citizens should not be elevated to our courts. Mr. Sessions has used the awesome powers of his office in a shabby attempt to intimidate and frighten elderly black voters. For this reprehensible conduct, he should not be rewarded with a federal judgeship.

I regret that a long-standing commitment prevents me from appearing in person to testify against this nominee. However, I have attached a copy of my statement opposing Mr. Sessions’ confirmation and I request that my statement as well as this be made a part of the hearing record.

I do sincerely urge you to oppose the confirmation of Mr. Sessions.

Sincerely,

Coretta Scott King</textarea>
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
