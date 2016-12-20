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
    <input type="color" name="base" value="#b4251b">
  </div>

  <img src="http://i.imgur.com/zSUPCqp.png">
  <p>This is a photo of me on a recent hiking trip to the Swiss Alps, in Gimmelwald, Switzerland.
  It's an amazing place-- You should go if you ever have the chance!</p>

  <style>
  input[type=range]{
  -webkit-appearance: none;
}

input[type=range]::-webkit-slider-runnable-track {
  width: 300px;
  height: 5px;
  background: #ddd;
  border: none;
  border-radius: 3px;
}

input[type=range]::-webkit-slider-thumb {
  -webkit-appearance: none;
  border: none;
  height: 16px;
  width: 16px;
  border-radius: 50%;
  background: #b4251b;
  margin-top: 0px;
}

input[type=range]:focus {
  outline: none;
}

input[type=range]:focus::-webkit-slider-runnable-track {
  background: #ccc;
}

    :root {
      --base: #b4251b;
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
