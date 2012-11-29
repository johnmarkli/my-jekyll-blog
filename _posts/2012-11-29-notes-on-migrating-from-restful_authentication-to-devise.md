---
layout: post
title: "Notes on migrating from restful_authentication to Devise"
description: ""
category: 
tags: []
---

### The Problem
My current Rails app is at 2.3.4 using the restful_authentication plugin from
technoweenie. At the time this app was built (2007) this was latest and greatest but
since then, Devise seems to be the new kid on the block that handles
authentication tasks much better. In particuluar, I need the built-in password reset
functionality that would be much harder to implement using
restful_authentication.

### The Plan
Obviously I want to get rid of restful_authentication entirely and just use
Devise but I'm trying to figure out the best migration path.
I have a couple options here.
1. Totally rip out restful_authentication from the app so that it has no
authentication. And then go in and install Devise and build from there.
2. Migrate from restful_authentication little by little until I get what I want
from Devise.

### The Solution
There's a lot of stuff going on with restful_authentication sprinkled all
throughout the app so it's probably worthwhile going little by little (plan #2).


