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
feature_image: hotwire2
show_related_posts: false
square_related: recommend-wolf
---

If you are reading this blog post, I am going to assume some level of familiarity with Ruby on Rails version 7 and some of the new tooling it provides, such as the "Hotwire" stack of Turbo, Turbo Frames, Turbo Streams, Stimulus. I've bene using it at work lately and have not felt this excited about web development technologies since I first started learning Rails oh so many years
ago. It is an exciting time to be a Rails developer!

So on to the point of this article... If Google brought you here, you are having some unexpected behavior between the service objects / service classes you are calling in your controller and the partials that are getting rendered. In fact, if you are looking at your Turbo Stream HTML response, you may be very surprised to see that attributes you expected to see updated are not updated- This issue happened to me and after chasing it down, it was discovered that we are padding an ID into the service object, not the object itself. That means that the object we are mutating in the service class is not the same object you have access to in the controller.

You will want to update the object, before you send it off to be rendered, with something like
UpdaterService.

    def set_as_primary
      authorize(Consumable)
      result = AedPrimaryConsumableUpdaterService.call(consumable_id: @consumable.id)
      if result[:success?]
        Consumable.search_index.refresh
        flash.now[:success] = t('controllers.consumables.set_as_primary.set_as_primary')
      else
        flash.now[:notice] = t('controllers.consumables.set_as_primary.something_went_wrong')
      end
      @consumable.reload
      render turbo_stream:
      [
        turbo_stream.update('is_primary', partial: 'admin/shared/tables/consumable_row', locals: { variable: @consumable.is_primary? }),
        turbo_stream.update('flash', partial: 'shared/flash')
      ]
    end

I hope someone finds this helpful, and I look forward to documenting more Hotwire learnings.



