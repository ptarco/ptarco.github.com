---
layout: post
title: "Gem agendare-schedule"
date: 2013-08-17 12:22
comments: true
categories: [Rails, Gems]
keywords: "agendare schedule, agendare-schedule, gem agendare schedule, gem agendare-schedule, agendar, gem schedule, gem" 
description: "The basic structure to implement schedule project. You have 3 objects to implement yours views, because the logic is implemented in this gem."
 
---
---

<!--more-->
####VERSION = "0.0.2"

The basic structure to implement schedule project. You have 3 objects to implement yours views, because the logic is implemented in this gem.

## Installation

Add this line to your application's Gemfile:
	{% codeblock %}
    gem 'agendare-schedule'
    {% endcodeblock %}

And then execute:
	{% codeblock %}
    $ bundle
    {% endcodeblock %}

## Usage
	 
Create controlllers.
{% codeblock %}
     rails  generate agendare:install controllers
{% endcodeblock %}
     
Create models.
{% codeblock %}
     rails  generate agendare:install models
{% endcodeblock %}
     
Create migrations.
{% codeblock %}
     rails  generate agendare:install migrations
{% endcodeblock %}
     
Import the structure to database.
{% codeblock %}
     rake db:migrate
{% endcodeblock %}
     
Add this lines in your config/routes.rb
{% codeblock %}
	 resources :schedules
	 resources :scheduleds
	 resources :users 
{% endcodeblock %}

---