---
layout: post
title:  "Face Detection in HTML5"
date: 2018-05-23 012:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 4
feature_image: bad
show_related_posts: false
square_related: recommend-wolf
---


<script src="https://tastenkunst.github.io/brfv4_javascript_examples/js/libs/createjs/preloadjs.min.js"></script>
	<script src="https://tastenkunst.github.io/brfv4_javascript_examples/js/BRFv4Demo.js"></script>

	<script>
		window.onload = brfv4Example.start; //see js/BRFv4Demo.js
	</script>



  <div id="_wrapper">

  	<div id="_content">
  		<video  id="_webcam" playsinline></video>
  		<canvas id="_imageData"></canvas>
  		<canvas id="_faceSub"></canvas>
  		<canvas id="_t3d"></canvas>
  		<canvas id="_f3d"></canvas>
  		<canvas id="_drawing"></canvas>
  		<div id="_stats"></div>
  		<div id="_progressBar"></div>
  		<a href="http://www.tastenkunst.com" target="_blank">
  			<img id="_brfv4_logo" src="assets/brfv4_logo.png" alt="BRFv4 Logo"/>
  		</a>
  	</div>

  	<div id="_subline"></div>
  	<div id="_highlight"><pre><code class="javascript" id="_gist"></code></pre></div>
  </div>

  <div id="_settingsRight"></div>
