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

<script src="https://gist.github.com/piratebroadcast/f2428257baaab951fc5aa10dce42ffc0.js"></script>


Now on to the tricky part: When we ran the mailer generator command, it created a folder in our Views called "Report Card Mailer" - Inside of this, we need to create a file called "report.html.erb". The file has to be names EXACTLY that for the mailer to find the right template... Our method is called def report(user), and it looks for the report.html.erb template based on that name. That took me forever to debug and figure out the first time through.

Now that we have a place to put our responsive code, we need to grab it. Head over to the Foundation For Emails site and choose the template you want. Lets say this time we go with the "basic" template found here: https://litmus.com/checklist/emails/public/eb690d2

Sign up and download the whole Foundation For Emails project file and open the folder in your editor. Now copy the CSS file completelym and paste it into the CSS section of the Inliner found here:

http://foundation.zurb.com/emails/inliner-v2.html

Next, open the HTML fir the Basic email and paste it into the HTML part. Make sure to uncheck the "compress HTML" option, then click the Inline! button. Copy that output and paste it directly into the report.html.erb file we created earlier in that mailer folder in the Views section.

This is a good time to install the letter_opener rubygem in the development section of your gemfile if you don't already have it.

Now, fire up your Rails console and enter the following:

<pre>$ ReportCardMailer.report(User.last).deliver</pre>

You should see a sweet looking email open up in your web browser that looks identical to the one we selected from the template. You can also use Google Chromes device emulator in the developer tools to emulate an iPhone device to see how it will look on a mobile. I took a screenshot of the screen at this point and dropped it into one of the devices at Mockuphone, so my bodd was able to show our stakeholders our progress and we could communicate visually with the rest of the team how the feature was coming along. Its also useful for making marketing materials for your new feature if need be. Mockuphone link: https://mockuphone.com/#ios

Anyways, go through the email and edit it with whatever marketing text you need, and populate the variables we need with things like

"Day One Grade:" "<%= day_1_grade %>"
"Day Two Grade:" "<%= day_2_grade %>"
and so on...

One of the most important "Gotchas" I learned form this process is how to fix broken images. You see, when
these emails would open for me locally, the image paths would be broken. This is because the email itself has no knowledge of the rails app and no idea about how image paths work. We need to tell our email where our app is located on the internet through action mailers asset host config setting. The way to do this is to edit your application.rb file and add the following line:

<pre>config.action_mailer.asset_host = 'http://YourSiteUrl.com'<pre>

In development.rb, we need to override this to localhost:

<pre>config.action_mailer.asset_host = 'localhost:3000'</pre>

Fire off another email and your images, if you are using them, should now be working as intended.
