---
layout: post
title:  "Hotwire and Service Objects in Rails 7"
date: 2020-03-03 012:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 4
feature_image: macbook
show_related_posts: false
square_related: recommend-wolf
---

If you are reading this blog post, I am going to assume some level of familiarity with Ruby on Rails version 7 and some of the new tooling it provides, such as the "Hotwire" stack of Turbo, Turbo Frames, Turbo Streams, Stimulus. I've been using it at work lately and have not felt this excited about web development technologies since I first started learning Rails oh so many years
ago. It is an exciting time to be a Rails developer!

So, on to the point of this particular article... If Google brought you here, it is fair to say that you are bearing witness to some very unexpected behavior between your instance variables,  the service objects / service classes you are calling in on them in your controllers, and the partials that are getting rendered as an end result.

In fact, you might think something is wrong with your hotwire implementation until you look at the Turbo Stream HTML response in your browser Inspector's Network tab, where you may be very surprised to see that attributes you expected to see updated are not being updated at all!

This issue happened to me and after chasing it down, realized that I was passing in the objects ID into the service object, and not the object itself. That means that the object I was mutating in the service class is ***not the same object in memory*** as the object I had access to in the controller, so sending it along to be rendered displayed no updates. Keep in mind that previously we were not displaying real-time updates on the webpage (In fact, the page and the object would both be reloaded upon controller actions being triggered) so this Service Class ID vs Object issue never surfaced until we added Hotwire into the mix.

The solution to this issue is to either refactor your service class to accept the object rather than an ID (so that you are now performing operations on the exact same object throughout the entirety of this controller action), or, to reassign the mutated widget (the payload) back to the widget instance variable after it exits the service, as seen below...



    def set_as_primary
      authorize(Widget)
      result = WidgetUpdaterService.call(widget_id: @widget.id)
      if result[:success?]
        flash.now[:success] = t('controllers.widgets.widgets_updated')
      else
        flash.now[:notice] = t('controllers.widgets.something_went_wrong')
      end
      <!-- pay attention to the line below -->
      @widget = result[:payload]
      <!-- pay attention to the line above -->
      render turbo_stream:
      [
        turbo_stream.update('is_primary', partial: 'admin/shared/tables/widget_row', locals: { variable: @widget.is_primary? }),
        turbo_stream.update('flash', partial: 'shared/flash')
      ]
    end


PS If all else fails and you are desperate, you could call reload on your object in the controller ***after*** the service, but before the render,  but the way above is a more elegant solution to the issue.    





