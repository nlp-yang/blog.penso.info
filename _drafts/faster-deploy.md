--- 
layout: post
title: Faster capistrano deploys
categories: 
- computer
description: to be filled
---

Spending minutes (or longer) for deploying a regular Rails application is
pissing me off. Litterally. I want to deploy within seconds.

Looked at recap, but it's based on capistrano2, looked at mina but it's single
host based. Fabric seems nice but I didn't feel like it either.

rake db:migrate: load the rails stack and isn't often needed. capistrano-rails
forces rake db:migrate to be ran, you loose at least 5 seconds.
