---
layout: post
title:  "Sending Responsive Emails In Ruby On Rails with Foundation For Emails"
date: 2017-05-06 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 2
feature_image: responsive
show_related_posts: false
square_related: recommend-wolf
---
<p>Recently. I was tasked with building a Report Card feature for our customers at work. After getting
more details about the intent of the feature, I decided that a slick looking responsive email would
bets fill this need. I did a lot of research about the best tools for this and settled on using Foundation
For Emails, by the Zurb company. (For the layperson, a "Responsive" email is an email that "morphs" to fit the
screen of whatever device it is currently being read on, so that means that it looks great on both an iPhone or an Android or a huge desktop monitor in a web browser.)</p>

Main Foundation For Emails website: http://foundation.zurb.com/emails.html

<p>One of the reasons I chose Foundation For Emails is that A) they have some great templates (http://foundation.zurb.com/emails/email-templates.html) to choose from, so I could choose the one that closest met the needs of the Report Card, and B) They're almost the only game in town. There aren't a lot of other tools for this particular job.<p>

<pre>rails g mailer CardMailer</pre>
