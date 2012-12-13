---
layout: post
title: "Migrating from restful_authentication to Devise (Part 2)"
description: ""
category: 
tags: []
---

I've finally got Devise up and running along side restful_authentication.

Steps:

1. `ruby script/generate devise_install`

    - devise.rb in config/initializers

      - `require 'devise/orm/active_record'`

    - devise.en.yml locale file

2. `ruby script/generate devise Devuser`

    - model named Devuser so it doesn't conflict with User

    - devuser.rb model -> moved to Common/models

    - DB migration -> moved to Common/db/migrate

3. `rake db:migrate` in Web (to pick up Devise::Schema)

4. `ruby script/generate devise_views`

    - creates view templates -> changed most to haml to fit in to layouts

Also, config.mailer should be configured according to your enviornment.

The next step is to look at what restful_authentication is doing and replace that behaviour with that of devise.
Devise offers a number of helper functions that do exactly what restful_authentication was doing.
Another thing to look at is using CanCan for doing authorization.

