---
layout: post
title:  "Speech to Text Translation Demo with Javascript"
date: 2016-10-17 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 3
feature_image: microphone
show_related_posts: false
square_related: recommend-wolf
---

Check this out -- See that thing in the upper right corner of the browser? Click "Allow"
to allow my website to briefly access your microphone, then start talking to your computer.
This works on non-mobile devices only, and best in Chrome. I built this with the HTML5 Speech Recognition API, which allows JavaScript to have access to a browser's audio stream and convert it to text.

<pre><div class="words" contenteditable>
</div></pre>

<script>
  window.SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

  const recognition = new SpeechRecognition();
  recognition.interimResults = true;

  let p = document.createElement('p');
  const words = document.querySelector('.words');
  words.appendChild(p);

  recognition.addEventListener('result', e => {
    const transcript = Array.from(e.results)
      .map(result => result[0])
      .map(result => result.transcript)
      .join('');

      const poopScript = transcript.replace(/poop|poo|shit|dump/gi, '💩');
      p.textContent = poopScript;

      if (e.results[0].isFinal) {
        p = document.createElement('p');
        words.appendChild(p);
      }
  });

  recognition.addEventListener('end', recognition.start);

  recognition.start();

</script>
