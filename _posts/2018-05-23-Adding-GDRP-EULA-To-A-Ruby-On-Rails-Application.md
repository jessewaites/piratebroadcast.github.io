---
layout: post
title:  "Implementing a GDPR EULA in a Ruby on Rails Application"
date: 2018-05-23 012:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 4
feature_image: GDPR
show_related_posts: false
square_related: recommend-wolf
---

As almost everyone has by now heard, the EU has passed some new consumer privacy
laws that go into effect later this week. There are a lot of new technical ramifications
of this, but this blog post specifically covers having existing and new users accept
our new GDPR Terms Of Service.

When building a new feature, I like to think backwards from the end result of what
we want: At the end of the day, we need all users to accept the new terms. That means we need to display these new terms. If the users don't agree, let's assume they will no longer be able to use our service.

I solved this by adding an uncloseable popup modal on our logged-in homepage. You can make a bootstrap modal static with:

$('#myModal').modal({backdrop: 'static', keyboard: false}) )

Ok, so users are now locked out of the rest of the application and are forced to make a choice in the modal. So far, so good. The text of the new GDPR EULA is within the modal, as are two buttons: Accept, or Log Out. If they click Log Put, I sent them to the regular Devise "Log Out" path. So what happens if they click accept?

I added a column to our Users table called accepted_gdpr_eula_at that accepts Datetime, and ran the migration. Next, I created a new Controller in the Rails Application called GrprEulaController, and added an action called "accept_gdpr_eula!". Then I added my route in the routes.rb file. (Bonus points for making this a proper RESTful action, when I refactor this I will do so then-- the rest of our app is built in a similar way to this, so it is actually more consistent with everyone else's work to name it this way. Don't @ me.)

The user clicks the "Accept" button, and the method in the controller updates the current_users gdpr_accepted_at column to Time.now, then redirects them to the home path.

I also added some logic to the Popup Modal - if the current_users gdpr_accepted_at column is nil, show the modal. If it is not nil, don't show the modal (Since logically it means they have already seen and accepted it.)

We can now determine who has and has not accepted our new terms, and have restricted the ability of users who have not accepted the new terms from using our web application. Yes it could be argued that we could have built an entire EULA management system, but implementing it this way has solved the business goal in a reasonable amount of time. For what it's worth, I wrote this on my lunchbreak because I thought it might be helpful to other developers currently working on the same issue, so don't read too much into any of this or feel you need to break it apart. Have a great Memorial Day Weekend!
