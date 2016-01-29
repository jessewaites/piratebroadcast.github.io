---
layout: post
title:  "Introducing the TwitterImageTag Rubygem"
date: 2016-01-29 09:50:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 4
feature_image: twitter_large_jpeg
show_related_posts: false
square_related: recommend-wolf
---

When I'm building a web application that is in the early prototype stage, I like to allow users to have profile pictures, but sometimes want to skip the process of actually building a mechanism (configuring Paperclip) to upload and store profile pictures so I can focus on something else.

So I got to work on this, TwitterImageTag.

> “To invent, you need a good imagination and a pile of junk.”
>
>  Thomas Edison

This gem allows you to easily add Twitter Avatar Images to your Ruby / Rails app views. Based on the Twitter v1.1 API, the primary usage would be for building out quick prototypes, or bypassing the need to have users upload their own avatar images. Ideally, you would have a field in your user onboarding form called "twitter handle", and call something like:

<pre>
<%= TwitterImageTag.show_me(current_user.twitter_handle, "normal") %>
</pre>

This image pretty much explains it all:

![Example](https://pbs.twimg.com/media/CZ1x9D1VAAEWITQ.png:large "Example")

This takes 2 arguments - any valid twitter handle, and any of 4 size options:
"normal", "bigger", "mini", or "original". The dimensions of the size options are:

normal: 48 x 48 pixels.
bigger: 73 x 73 pixels.
mini:   24 x 24 pixels.
original: No idea.

There's no telling what the "original" image size will be. It is whatever
size the user uploaded.



## Installation

Add this line to your application's Gemfile:

NOTE: Make sure you are using the latest version of this gem - it went under a significant rewrite at version 1.9.5 - Don't use anything lower than that.

```ruby
gem 'twitter_image_tag'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install twitter_image_tag

## Usage
<pre>
<%= TwitterImageTag.show_me(current_user.twitter_handle, "normal") %>
</pre>
## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake false` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/piratebroadcast/twitter_image_tag.
