---
layout: post
title:  "Installing Drift into a Ruby on Rails or Jekyll Site"
date: 2017-11-28 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : false
read_time : 1
feature_image: carpenter
show_related_posts: false
square_related: recommend-wolf
---
<p>I frequently compare the profession of web development to that of being a carpenter. Much of our expertise relies in knowing the correct tool for any particular job, and knowing the layout of the problem and the tools available to us to solve the current problem.</p>

<p>I mention this because I like using this personal website of mine to show off my work or the tools available to us. Far too frequently, a web developer will not have any samples of their work to show a prospective client, employer, etc. Would you hire a carpenter that couldn't show you anything they've built before, or if the table they showed you was kind of terrible looking? I think not.</p>

<p>So I've seen this tool Drift around for a bit now and thought to myself, "Could I install thing into my personal site that runs on the Jekyll framework? Could I easily add the Drift Conversational Marketing into a Ruby on Rails app? I wonder how long it would take me?" I considered it a personal challenge to get it set up and deployed as quickly as possible. I started the clock and got to work onboarding through the free tier of their website.</p>

<p>So, spoiler alert: It was super easy and I was done in less that 5 minutes. I went through their creation wizard (Select "Javascript" for Jekyll / Ruby on Rails), uploaded my avatar into the system, and had some javascript copies to my clipboard in a matter of minutes.</p>

<p>In Jekyll, open up includes/head.html and paste it into that partial. Save it. Commit it, deploy it. For Rails, you'll want to open views/shared/header.html.erb and paste the js there.<p>

<p>It literally was one of the easiest things I've ever added to this site and now I have a super cool chat box on my personal website. Head on over to Drift.com and check them out sometime.</p>
