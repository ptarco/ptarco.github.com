---
layout: post
title: "Gem previsao-clima-tempo"
date: 2013-08-17 00:00
comments: true
categories: [Rails, Gems]
keywords: "clima tempo, clima-tempo, gem clima tempo, gem clima-tempo, previsao tempo, previsao-clima-tempo, gem" 
description: "Gem Communication with Clima Tempo accessing information about the weather of Brazil."
---
---


<!--more-->
####VERSION = "0.1.4"
Communication with Clima Tempo accessing information about the weather of Brazil.

## Installation

Add this line to your application's Gemfile:
{% codeblock %}
    gem 'previsao-clima-tempo'
{% endcodeblock %}

And then execute:
{% codeblock %}
    $ bundle
{% endcodeblock %}

Or install it yourself as:
{% codeblock %}
    $ gem install previsao-clima-tempo
{% endcodeblock %}

## Usage
	 
### From Webservice
##### .new
Instantiating a object.The city code should be informed.
	 {% codeblock %}
PrevisaoClimaTempo.new(:codCity => '3156')
     {% endcodeblock %}
##### .now     
Returns an object PrevisaoDia with information from the current day.
     {% codeblock %}
     PrevisaoClimaTempo.new(:codCity => '3156').now
     {% endcodeblock %}
##### .tomorrow     
Returns an object PrevisaoDia with information the next day.
     {% codeblock %}
     PrevisaoClimaTempo.new(:codCity => '3156').tomorrow
     {% endcodeblock %}
##### .days     
Returns a collection of objects PrevisaoDia with information of days referenced.
     {% codeblock %}
     PrevisaoClimaTempo.new(:codCity => '3156').days(13) maximum of 13 days from the current day
     {% endcodeblock %}
##### .day     
Returns an object PrevisaoDia with information the day referenced.
     {% codeblock %}
     PrevisaoClimaTempo.new(:codCity => '3156').day(date)
     {% endcodeblock %}
     
### From Page
####(contains more information than is extracted from the webservice)
##### .nowFromPage     
Returns a hash of condtions of weather from page
     {% codeblock %}
	 PrevisaoClimaTempo.new(:codCity => '314').nowFromPage
	 {% endcodeblock %}
return:
	 {% codeblock %}
	 {
		:last_update: 18:00
		:wind:
		  :velocity: 3 Km/h
		  :direction: Su-sudeste
		:moisture: 91%
		:condition: Poucas nuvens
		:pression: 1022 hPa
		:temperature: 13ºC  
 	 }
 	 {% endcodeblock %}
#####.fullFromPage 	 
Returns a hash of condtions of weather whith 5 days from page.
     {% codeblock %}
  	 PrevisaoClimaTempo.new(:codCity => '314').fullFromPage
  	 {% endcodeblock %}
return:
	 {% codeblock %}
	 {
		1:
		  :last_update: 19:00
		  :date: Sábado, 17/08/2013
		  :condition: Sol com muitas nuvens durante o dia e períodos de céu nublado. Noite
		    com muitas nuvens.
		  :wind:
		    :velocity: 6km/h
		    :direction: Su-sudeste
		  :probability_of_precipitation:
		    :volume: 0mm
		    :percentage: 0%
		  :moisture_relative_complete:
		    :max: 100%
		    :min: 49%
		  :temperature:
		    :max: 16º
		    :min: 7º
		  :uv: Alto
		  :sunrise: 06h13
		  :sunset: 17h36
		2: ...
 	 }
 	 {% endcodeblock %}
#####.trendsFromPage 	 
Returns a hash of condtions of weather whith 5 days from page.
If today is 16-12-2013 returns 21,22,23,24,25 trends.
	 {% codeblock %}
  	 PrevisaoClimaTempo.new(:codCity => '314').trendsFromPage
  	 {% endcodeblock %}
return:
	 {% codeblock %}
	 {
		1:
		  :date: Quinta-Feira, 22/08/2013
		  :condition: Sol com algumas nuvens. Não chove.
		  :probability_of_precipitation:
		    :volume: 0mm
		    :percentage: 0%
		  :temperature:
		    :max: 23º
		    :min: 7º
		2: 
 	 }
 	 {% endcodeblock %}
 	 
---
