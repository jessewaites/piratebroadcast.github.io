---
layout: post
title:  "Working with React"
date: 2016-10-17 012:20:28
categories: coding
author_name : Jesse
author_url : /author/jesse
author_avatar: jesse
show_avatar : true
read_time : 3
feature_image: react_logo
show_related_posts: false
square_related: recommend-wolf
---

React, the javascript library invented by Facebook, is a very hot technology right now, and rightly so. With such a small surface area of API calls to learn and implement, it seems to do a small number of things just right, without over extending itself into other sections of web application development where it might not be completely needed. I've decided to jot down some ideas and concepts I've learned / am learning in the hopes of both teaching others and reinforcing for myself the things I pick up as I go. They say the best way to remember something is to write it down, after all. I've been building a Youtube clone with React and Redux using the Youtube API for fun and have been learning quite a bit about it lately. Here's a screenshot of my progress on that so far...

![React App from Jesse Waites](http://i.imgur.com/CdY8xjj.png)

This article will be updated with new information as I build and continue to learn more.

From Wikipedia, "React (sometimes styled React.js or ReactJS) is an open-source JavaScript library providing a view for data rendered as HTML. React views are typically rendered using components that contain additional components specified as custom HTML tags. React promises programmers a model in which subcomponents cannot directly affect enclosing components ("data flows down"); efficient updating of the HTML document when data changes; and a clean separation between components on a modern single-page application.

React is maintained by Facebook, Instagram and a community of individual developers and corporations. React is currently being used on the websites of Facebook, Instagram, Netflix, Imgur, Bleacher Report, Feedly, Airbnb, SeatGeek, HelloSign, and others."

Some of the ideas and concepts I've learned since working with React are:

### State ###

Probably the most important concept in React is the concept of "State". State is described as how a React component’s data looks at any moment in time. This concept is better explained elsewhere by people far better at this that I so I will leave it to you to find resources about this. I may come back to this at a later moment and flesh this section out.

### One-way data flow ###

Properties, a set of immutable object values, are passed to a component's renderer as properties in its HTML tag. A component cannot directly modify any properties passed to it, but can be passed callback functions that do modify values. This mechanism is expressed as "properties flow down; actions flow up". As an example of this, in my app, I have a concept called "selected video" that flows down all the way from the "App" concept to "Video List", to "Video List Item".

### Virtual DOM ###

Another notable feature is the use of a "virtual DOM." React creates an in-memory data structure cache, computes the resulting differences, and then updates the browser's displayed DOM efficiently. This allows the programmer to write code as if the entire page is rendered on each change while the React libraries only render subcomponents that actually change. Basically, this "virtual" or "shadow" DOM pushes only the needed page changes to the "real" DOM.

### JSX ###

React components are typically written in JSX, a JavaScript extension syntax allowing quoting of HTML and using HTML tag syntax to render subcomponents. HTML syntax is processed into JavaScript calls of the React library. Developers may also write in pure JavaScript. Interesting, I've found that some HTML is not supported in JSX, specifically "break" tags and horizontal rule tags.

### NPM Server Error Reporting ###

Errors such as syntax errors and whatnot are pretty easily found in the NPM server log, which is pretty amazing. I always know exactly where to look to begin debugging the issue. I am definitely a fan of that.
