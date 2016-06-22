---
layout: post
title:  "Embedding Interactive Ruby Snippets Into Web Pages"
date: 2016-06-22 09:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 8
feature_image: leafy-bench
show_related_posts: false
square_related: recommend-wolf
---


<p>Let's say you're a web developer and occasionally need to blog about code.
You want to show off how to do this or that. Conventionally, there is no way
to do this because browsers only understand HTML, CSS, and Javascript.</p>

<p>With this new javascript plugin called <strong>klipsify</strong>, I can now
run interactive Ruby snippets in the browser. Let's take a tour...</p>


<pre><code class="language-klipse-eval-ruby">[9,8] * 2
</code></pre>

In the section above, change the "2" to a "20", so that it says "[9,8] * 20"
Did you see the output change? Cool, right?


Let's show off something more complicated. Let's write a custom Ruby method
called "trumpify".

<pre><code class="language-klipse-eval-ruby">def trumpify(text)
"Wow! #{text} Sad!!"
end
trumpify("My campaign is a garbage fire!")
</code></pre>

<p>Change "My campaign is a garbage fire" to anything else and the custom ruby
method will trumpify it.</p>

<br>

In this next example, let's explore Ruby's Upcase method.

<pre><code class="language-klipse-eval-ruby">"Ban Assault Rifles".upcase
</code></pre>

<p>Here, we explore the Swapcase method.</p>

<pre><code class="language-klipse-eval-ruby">"Trump Is A Con Artist.".swapcase
</code></pre>

Note that, where words were capitalized, they are now lowercase, and vice versa.

You can check out Klipse here: https://github.com/viebel/klipse

*Ok. Thanks for reading.*

![Fin](http://2.bp.blogspot.com/-d94FNkb_Zxc/Tij3o8NE77I/AAAAAAAAAdw/DeZlPhbh2uM/s1600/fin.png)







<link rel="stylesheet" type="text/css" href="http://app.klipse.tech/css/codemirror.css">

<script>
    window.klipse_settings = {
        selector_eval_ruby: '.language-klipse-eval-ruby', // css selector for the html elements you want to klipsify
    };
</script>
<script src="http://cdn.opalrb.org/opal/current/opal.min.js"></script>
<script src="http://cdn.opalrb.org/opal/current/opal-parser.min.js"></script>
<script src="http://app.klipse.tech/plugin/js/klipse_plugin.js"></script>
