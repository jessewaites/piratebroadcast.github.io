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
<p>Recently, I was tasked with building a Report Card feature for our customers at work. After getting
more details about the intent of the feature, I decided that a slick looking responsive email would
best fill this need. I did a lot of research about the best tools for this and settled on using Foundation
For Emails, by the Zurb company. (For the layperson, a "Responsive" email is an email that "morphs" to fit the
screen of whatever device it is currently being read on, so that means that it looks great on both an iPhone or an Android or a huge desktop monitor in a web browser.)</p>

Main Foundation For Emails website: http://foundation.zurb.com/emails.html

<p>A few of the reasons I chose Foundation For Emails is that A) they have some great pre-built templates (http://foundation.zurb.com/emails/email-templates.html) to choose from, so I could choose the one that closest met the needs of the Report Card, and B) They're almost the only game in town. There aren't a lot of other tools for this particular job. A key thing to know about is that responsive emails is a tricky process -- there are entire companies that build products around doing this, because each email client renders things differently, and GMail strips the style tags out of emails completely, so to find a single tool that deals with all of this for you is a great thing. So after looking at my options, Zurb it is. Onwards...<p>

<p>In this feature, lets presume Users have_many ReportCards, and ReportCards belong_to Users.
I used the Whenever gem and the Schedule.rb file to automatically generate these User ReportCards without any user intervention on the last day of the month, every single month.

Now lets talk about the data in these Report Cards. The data in the actual thing I built was, franlkly, very complicated, but for this example lets keep it nice and simple... Lets say a Report 7 "grades", for 7 days a week, as the string datatype. Each day the user can receive an A, B, C, D, or F (Why is there no E grade? I just realized that. Super weird. Anyways...)


Now that I understand the data structure, I generate a Mailer in the rails app from the Rails console:

<pre>$ rails g mailer CardMailer</pre>

<p>And inside that mailer, I need to add the local variables that will render into the email itself:<p>

<script src="https://gist.github.com/piratebroadcast/f2428257baaab951fc5aa10dce42ffc0.js"></script



<p>Let us now imagine it is the 1st of a new month and we have 5 users, each with 1 completed report card.</p>
