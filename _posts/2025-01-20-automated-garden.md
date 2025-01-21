---
layout: post
title: Automated garden
subtitle: Arduino with soil sensors reporting to a time series database
gh-repo: 
gh-badge: [star, fork, follow]
tags: [arduino, influxdb, python]
comments: true
---

A few years ago I decided to make a garden next to a lake so I could use the lake to water the garden. This evolved into the current project that senses the soil
and fills a rain barrel when the soil becomes too dry.  The sensor data is gathered with an arduino and presented as a prometheus data format.  The arduino
has an ethernet shield and uses power over ethernet.  

Next I used [InfluxDB](https://www.influxdata.com/) to scrape the arduino page in prometheus data format.  There are 3 soil sensors, and a multi-sensor for humidity, pressure, and temperature.  
![Moisture Sensors](/assets/img/moisture-sensors.png)
This is a graph of the moisture senors.  The higher the value the drier the soil.

The result is a time series graph of the scraped data.  There is also a script that averages the three soil sensors and runs a sump pump in the lake for 10 minutes
to fill the rain barrel.

I was expecting to use Grafana, but the new InfluxDB graphs are pretty good so I decdied to keep it more simple.  The next step is to have the watering 
script notify InfluxDB that the water is on so that I can compare the moisture level from when the water kicks on.  It would be nice to know exactly when it is on and 
what the delay is from when the moisture sensors begin to see the change.

Here are more pictures of the other sensor graphs:
![Humidity](/assets/img/humidity.png)
![Pressure](/assets/img/pressure.png)


