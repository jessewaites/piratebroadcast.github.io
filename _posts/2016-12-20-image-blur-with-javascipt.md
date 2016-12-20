---
layout: post
title:  "Updating CSS variables with Javascript in the Swiss Alps"
date: 2016-12-12 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 2
feature_image: alps
show_related_posts: false
square_related: recommend-wolf
---

<body>
  <p>Move the range sliders around to update our CSS variables with <span class='hl'>Javascript</span>
  and reveal my hiking picture taken in the Swiss Alps, in Gimmelwald, Switzerland.</p>

  <div class="controls">
    <label for="spacing">Frame Size:</label>
    <input type="range" name="spacing" min="10" max="200" value="10" data-sizing="px">

    <label for="blur">Blur:</label>
    <input type="range" name="blur" min="0" max="25" value="5" data-sizing="px">

    <label for="base">Frame Color</label>
    <input type="color" name="base" value="#9d2425">
  </div>

  <img src="http://i.imgur.com/zSUPCqp.png">
  <p>This is a photo of me on a recent hiking trip to the Swiss Alps, in Gimmelwald, Switzerland.</p>

  <style>
    :root {
      --base: #9d2425;
      --spacing: 10px;
      --blur: 5px;
    }

    img {
      padding: var(--spacing);
      background: var(--base);
      filter: blur(var(--blur));
    }

    .hl {
      color: var(--base);
    }

    body {
      text-align: center;
    }

    body {
      color: black;
      font-family: 'helvetica neue', sans-serif;
      font-weight: 100;
      font-size: 50px;
    }

    .controls {
      margin-bottom: 50px;
    }

    input {
      width:100px;
    }
  </style>

  <script>
    const inputs = document.querySelectorAll('.controls input');

    function handleUpdate() {
      const suffix = this.dataset.sizing || '';
      document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
    }

    inputs.forEach(input => input.addEventListener('change', handleUpdate));
    inputs.forEach(input => input.addEventListener('mousemove', handleUpdate));
  </script>


</body>
