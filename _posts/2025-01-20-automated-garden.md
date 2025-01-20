---
layout: post
title: Automated garden
subtitle: 
gh-repo: 
gh-badge: [star, fork, follow]
tags: [test]
comments: true
---

A few years ago I decided to make a garden next to a lake so I could use the lake to water the garden. This evolved into the current project that senses the soil
and fills a rain barrel when the soil becomes too dry.  The sensor data is gathered with an arduino and presented as a prometheus data format.  The arduino
has an ethernet shield and uses power over ethernet.  

Next I used [InfluxDB](https://www.influxdata.com/) to scrape the arduino page in prometheus data format.  There are 3 soil sensors, and a multi-sensor for humidity, pressure, and temperature.  
[!](/assets/img/moisture-sensors.png)
This is a graph of the moisture senors.  The higher the value the drier the soil.

The result is a time series graph of the scraped data.  There is also a script that averages the three soil sensors and runs a sump pump in the lake for 10 minutes
to fill the rain barrel.

