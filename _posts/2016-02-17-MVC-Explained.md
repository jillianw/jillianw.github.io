---
title: Explaining Models, Views and Controllers (To Myself...)
---

It's been a confusing couple of weeks, trying to build my first database-driven web app, so it's definitely a good exercise to take a few minutes to put into words just how models, views and controllers work together to as components of a functioning website. 

Starting with models, these are what represent the data and it's where the wisdom about your application resides. We give our models the magical powers of ActiveRecord and they become full of knowledge about how to do things. We can add more knowledge by defining methods.

One resource I looked at gave a helpful example for models: they contain "is-a" and "has-a" relationships. To illustrate the point, if you're talking about a dog, that would represent a method you would define in a model. The dog "is-a" aniaml (the class), and "has-a" tail (something that would be defined in a method). Obviously, the model would know all about the behaviors of an animal, and what they can and cannot do.

Views, to put it simply, are what gets displayed to a user. Views display data and send information about user actions to the controller (e.g., clicking a link on a page).

The controllers in an application are the part of a web app that receive commands from the user and, in turn, tells the view what to show. So there's a give-and-take between the controller and views. Likewise, there's a give-and-take between the controller and model in figuring out what data to retrieve (and display in the view) and what data to save (determined by the controller).