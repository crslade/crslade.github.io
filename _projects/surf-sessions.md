---
layout: page
title: Surf Sessions
description: iOS App that automatically logs surfing sessions
img: assets/img/Surf1024.png
importance: 3
category: fun
---

I love to surf, so I created an app to record my sessions. It downloads weather and buoy data from the NOAA. Then, when you park to go surfing it starts a timer. When you leave, it notifies you to record your session. It also integrates with the health app.

<div class="row">
Surf Sessions makes it easy for you to integrate your surfing into an overall fitness plan. Create a list of surfing locations, and then start recording your surfing sessions. This app will estimate the calories you burned while surfing and then share your surfing workouts with the Health App.
</div>

[![Download from the App Store](/assets/img/AppleAppStore.svg)](https://apps.apple.com/us/app/surf-sessions/id935513127)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/surf1.jpeg" title="log your session" alt="log your sessions" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/surf2.jpeg" title="current conditions" alt="current conditions" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/surf3.jpeg" title="auto record" alt="current conditions" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Screenshots of my Surf Sessions App.
</div>

# Privacy Policy 

Surf Session's does not collect or store any health information about you. All of the data is located either on your device and/or Apple's iCloud servers. It is never sent to us. We take your privacy very seriously and do not intend to collect or share your personal health data. For more information you can read our detailed [privacy policy](/assets/pdf/surfsessions-mpdf.pdf) (pdf).

# FAQ 

## Why do you need my location?
We use your location to find and load buoy data. While you are selecting location points, your location is used to adjust the map to your current location. Your location is not used to track you.

##  Why is the Buoy Data only available in the US?
The only free service that can load current conditions is the United States National Buoy Data Center (NBDC), which is part of the National Oceanic and Atmospheric Administration (NOAA). There might be some Buoys outside the US that are included in their service, however that is not a guarantee. If there is enough interest and financial support (people willing to pay for it), I will consider using a non-free service that can collect data around the world. If you know of a service that provides better data, please contact me.

## How do you determine which Buoys to use?
I use the buoy data that is closest to you. In the search, all Buoys within a 100 mile radius are queried. If there are not any buoys within a 100 mile radius, then no data will appear. Hopefully, if you are on an island, the buoy used will be the buoy monitoring the closest shore.

## What value should I use for my intensity (MET Value)?
The Metabolic Equivalent is a way to estimate the amount of calories burned by activity type. Surfing has a reported MET Value of 3.0, and competitive surfing has a value of 5.0. However, swimming has a value of 8.0. Any value you use will be an estimate. If you were fighting a current and paddling most of the time, than you might want to use a value closer to 8. That might be closer to a swimming activity. If you just sat on your board the full time, you might want to use a value closer to 2.

## Can I recommend new features?
Yes, just email me.

