---
layout: author
title: Author
permalink: author/jesse/
feature_image: feature-sea
author_avatar: Jesse
author_name: Jesse Waites
title: About Jesse Waites

---

# About Jesse Waites

<p>Here for the book? You can now buy the PDF version of my book here. Also, enjoy this fun chart.</p>

<form action="https://jesse-book-server.herokuapp.com" method="POST">
    <script
        src="https://checkout.stripe.com/checkout.js"
        class="stripe-button"
        data-key="pk_live_JEwYdUmZ8ZNhYt9gZvqlpXWx"
        data-name="JESSE WAITES"
        data-description="PDF Book"
        data-amount="500">
    </script>
    <input name="amount" value="500" type="hidden">
    <input name="description" value="Secrets of my App Success eBook" type="hidden">
</form>
<br>

> “If you think math is hard, try web design.” ―Trish Parr

<p>Skills, Tools, and Keywords for the busy people: UI, UX, JavaScript, JQuery, D3, HTML, CSS, Git, Ruby, Ruby on Rails, Boston Rails Developer, Boston UI, Boston UX, iOS, OSX, Drupal, WordPress.</p>

<canvas id="c" width="auto" height="auto"></canvas>

After seeing a chart of some of my hobbies, here is a little about me: After growing up in the South and serving a short stint in the Air Force, I worked as an Operating Room Technician specializing in Trauma, Orthopaedic, and Neurosurgery in hospitals all over the US. After accepting a job in Trauma Surgery in Boston at MGH and falling in love with the city, I decided to stay in New England and have been here for almost 10 years. Boston is my home now.

<img style="float:left" src="/img/W.jpg" />hile working in surgery, the iPhone was developed and I took advantage of the opportunity and hired a developer to create a medical terminology dictionary app for me. Released on opening day of the App Store, it sold fairly well and served as a springboard into my second career as a web and software developer after learning web development on my own for years and eventually graduating thoughtbot's Ruby on Rails intensive course.

My consulting work and I have been written about in Wired Magazine, Entrepreneur Magazine, Inc., Forbes, and a full profile in the Boston Globe.
I also wrote a book about the process of mobile app development, which is currently on sale on the iBookstore and the Amazon Kindle, and have given talks about the App Development process at M.I.T. and General Assembly. You can buy the PDF version of my book here.
<br>

<form action="https://jesse-book-server.herokuapp.com" method="POST">
    <script
        src="https://checkout.stripe.com/checkout.js"
        class="stripe-button"
        data-key="pk_live_JEwYdUmZ8ZNhYt9gZvqlpXWx"
        data-name="JESSE WAITES"
        data-description="PDF Book"
        data-amount="500">
    </script>
    <input name="amount" value="500" type="hidden">
    <input name="description" value="Secrets of my App Success eBook" type="hidden">
</form>
<br>
I have since created multiple mobile and web applications for myself and clients such as social networks, e-commerce applications that sell goods and services online, and scheduling applications that allow consultants to charge fees to book an appointment. In addition to my primary web development framework, Ruby on Rails, I also have extensive experience with Wordpress, Drupal, and Squarespace.

I love what I do because being a web developer is the rare career field that affords me the ability to be both an engineer and an artist.

I can do everything from back end programming to mocking up a User Interface in Omnigraffle, Balsamiq, or InVision and coding it up in HTML/CSS and building out a great backend in Rails. I've used Bootstrap, Foundation, Stripe, Twilio, and a ton of other Ruby on Rails supporting technologies and frameworks.

I firmly believe that it is not good enough for a website to merely function properly from a programmatic perspective, it must also look great and be pleasant for people of all demographics to use.

> “Websites should look good from the inside and out.” ― Paul Cookson

I currently spend my time surrounding myself with great friends, hiking, traveling, backpacking, climbing at Brooklyn Boulders, reading great books, watching amazing films, posting overly filtered Instagram pictures, making smalltalk and fleeting friendships with Uber drivers, and building great looking web applications primarily with Ruby on Rails.

Need to get in touch? Email Me or schedule an appointment for a phone call.


<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/1.0.2/Chart.min.js"></script>
<script>
  var ctx = document.getElementById("c").getContext("2d");
  var data = {
    labels: ["Movies", "Books", "Hiking", "Dogs", "Photography", "Tea", "Other"],
    options: {
    responsive: true,
    maintainAspectRatio: true
    },
    datasets: [{
      label: "Weekdays",
      fillColor: "rgba(220,220,220,0.2)",
      strokeColor: "rgba(220,220,220,1)",
      pointColor: "rgba(220,220,220,1)",
      pointStrokeColor: "#fff",
      pointHighlightFill: "#fff",
      pointHighlightStroke: "rgba(220,220,220,1)",
      data: [75, 69, 80, 81, 76, 95, 40]
    }, {
      label: "Weekends",
      fillColor: "rgba(151,187,205,0.2)",
      strokeColor: "rgba(151,187,205,1)",
      pointColor: "rgba(151,187,205,1)",
      pointStrokeColor: "#fff",
      pointHighlightFill: "#fff",
      pointHighlightStroke: "rgba(151,187,205,1)",
      data: [28, 48, 40, 69, 86, 67, 90]
    }]
  };
  var MyNewChart = new Chart(ctx).Radar(data);


</script>
