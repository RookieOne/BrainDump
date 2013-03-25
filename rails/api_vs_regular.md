---
layout: page
title: API vs Regular Rails
tagline: More than routes
---
{% include JB/setup %}

An API is going to be used by mobile devices and client side js frameworks. It responds to HTTP requests and returns JSON.

Rails controllers can respond to many different formats include json and xml. In fact, we could respond with JSON in our normal Rails controllers.

EXAMPLE

We choose to make our API separate from our regular application because the needs of an API user will differ from the needs of a normal user. Suddenly our controller will start getting very complex deciding which type of request is coming in and how it should be handled.

Instead we move our API to its own namespace.

EXAMPLE

Sometimes in addition to the API namespace, we add a version namespace. We version the API so we can evolve the API and still support legacy mobile applications. We can version using a namespace in the route or we can plan to use HTTP Headers to handle versioning.

Now our API controllers will be isolated from our normal controllers.

Besides the routes and the controller's file location, the controllers themselves will be different. An API Controller will generally inherit from a API specific base controller.

As an example, we will look at the create action for a controller

EXAMPLE - NORMAL

Notice in the normal controller we set flash messages and redirect the user to different pages.

EXAMPLE - API

With an API we don't have flash messages and in general we don't redirect users. Instead we return a hash that will be converted into JSON

Where does Rabl fit in?

Rabl is gem that allows us more control in serializing our results to JSON. With complex results there would be too much code in our controller. Rabl allows that complexity to live in a rabl view.