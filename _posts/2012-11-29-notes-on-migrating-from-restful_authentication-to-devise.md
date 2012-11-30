---
layout: post
title: "Notes on migrating from restful_authentication to Devise"
description: ""
category: 
tags: []
---

### The Problem
My current Rails app is at 2.3.4 using the restful\_authentication plugin from
technoweenie. At the time this app was built \(2007\) this was latest and greatest but
since then, Devise seems to be the new kid on the block that handles
authentication tasks much better. In particuluar, I need the built\-in password reset
functionality that would be much harder to implement using
restful\_authentication.

### The Plan
Obviously I want to get rid of restful\_authentication entirely and just use
Devise but I'm trying to figure out the best migration path.
I have a couple options here.

1. Totally rip out restful\_authentication from the app so that it has no
authentication. And then go in and install Devise and build from there.
2. Migrate from restful\_authentication little by little until I get what I want
from Devise.

### The Solution
There's a lot of stuff going on with restful\_authentication sprinkled all
throughout the app so it's probably worthwhile going little by little \(plan #2\).

### Notes

#### Installing devise \(from railscasts\)
For Rails 2\.3, use version devise 1\.0\.x

- Include gem devise v=1\.0\.6

- run bundle install

- run rails generate devise install

  - Creates config/initializers/devise\.rb and a locale yml file

- rails generate devise User \(don't need to do this in my app\)

	- creates user\.rb model
	- has call to devise with modules you want supported like validatable
	- creates db migration
	- route devise\_for :users

- Set up views to have sign in logout buttons

	- setup

#### Customizing devise \(from railscasts\)
- authorization

  - in controller use `before_filter :authenticate_user!, :except => [:show, :index]`
  - but using Cancan might be better

- generatating devise views

  - generates passowrd reset pages etc

- locales devise yml file

  - used to change messages

- devise.rb file for config changes

- config routes at devise for :users

  - change sign up to register with `:path_names => { :sign_up => "register"}`

- config to use username instead of email

  - generate migration to add username to users
  - `config.authentication_keys = {:username}`
  - change sign in form to take `:username`
