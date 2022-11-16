---
layout: post
title:  "How-to: Smart Roller Shutters"
description: "How to convert your existing roller shutters, so you can operate them from your mobile phone"
date:   2022-11-16 00:00:00 +0300
categories: blog
tags: [home automation, home assistant, iot, smart home ]
---


## Requirements 

The easiest way to convert your existing roller shutters in remote-controlled "smart" roller shutters involves
adding a single device behind your existing wall switch.

Let's say you have a wall switch like this:

{% include image.html path="posts/roller_shutters/roller_shutters-switch.jpg" path-detail="posts/roller_shutters/roller_shutters-switch.jpg" alt="Roller Shutter Switch" caption="Roller Shutter Switch" %}

Here's what else you'll need:

* A wall switch to operate your roller shutters
* A neutral wire available behind your wall switch 
* A Shelly 2.5 
* Enough depth behind your wall switch for the Shelly 2.5 to fit

**Total Cost:** ~ 30 EUR per switch

**Expected time:** if you already have a Neutral wire installed - a couple of hours.

## Installation

With a Neutral wire in place, the installation is pretty straightforward (even if it does feel intimidating 
if this is your first time - it was the same for me!). 

Here's how it goes: 

The wall switch will probably have 3 wires going into it: 

* Line 
* One return to the UP direction
* One return to the DOWN direction

Here's how Shelly recommend that you connect: 

{% include image.html path="posts/roller_shutters/Shelly-25-ac-Wiring-1341167975.png" path-detail="posts/roller_shutters/Shelly-25-ac-Wiring-1341167975.png" alt="Shelly Wiring" caption="Shelly Wiring" %}

So, with that in mind, here is what you have to do: 

* O1 (Output 1): connect here the cable that **was** connected to your UP switch (and make a note of where on your switch this cable was connected, you'll need it below)
* O2 (Output 2): connect here the cable that **was** connected to your DOWN switch (and make a note of where on your switch this cable was connected, you'll need it below)
* SW1 (Switch 1): connect to your wall switch, at the same connection point where your UP was
* SW2 (Switch 2): connect to your wall switch, at the same connection point where your DOWN was
* L: You need **two** line cables going into the Shelly. These can be bridged with the existing Line cable that was going into your roller shutters wall switch. 
* N: The Neutral wire that should exist behind your wall switch. 


Here are a few photos from a real world installation:


{% include image.html path="posts/roller_shutters/roller_shutters-installation1.jpg" path-detail="posts/roller_shutters/roller_shutters-installation1.jpg" alt="Shelly Installation 1" caption="Shelly Installation 1" %} 
{% include image.html path="posts/roller_shutters/roller_shutters-installation2.jpg" path-detail="posts/roller_shutters/roller_shutters-installation2.jpg" alt="Shelly Installation 2" caption="Shelly Installation 2" %}



## Shelly setup 

### Ensure CoIoT is enabled

* `Internet & Security => Advanced - Developer Settings` 
* Ensure there is an "Enable CoIoT" option there. If not, you will need to update to the latest firmware - see below. 


### Connect to WiFi and Update Firmware (optional steps)

Just documenting here my own steps - this will probably be different for everyone: 

* Connect Shelly to Guest WiFi (with internet access, but no connection to other home networks).
* Update the firmware to the latest.  
* Connect Shelly to the IoT WiFi (no internet access)
* Assign a static IP

### Roller Shutter setting

* Connect to the Shelly web interface through the static IP. 
* Change the Shelly to operate as a roller shutter:  `Settings => Device Type => Roller Shutter`
* Check that when pressing UP and DOWN your roller shutter moves UP and DOWN accordingly. If not - no need to change the cables around! Play around with the below 2 settings: `Settings => Reverse Directions => Enable the Checkbox` and `Settings => Swap Inputs`. 
* Ensure the **Button type** is also correctly set. If you try to stop the roller shutter from the wall switch but it doesn't stop, you might need to change the Shelly Button type to Momentary switch.  

{% include image.html path="posts/roller_shutters/roller_shutter-settings.png" path-detail="posts/roller_shutters/roller_shutter-settings.png" alt="Shelly Roller Shutter Settings" caption="Shelly Roller Shutter Settings" %}


### Calibration

Once the buttons are correctly configured, it's now time to let Shelly calibrate itself for your roller shutter positions. It will go up and down a few times (don't worry if it happens more than once)

* The calibrate option is available under `Settings => Positioning Controls`. 

{% include image.html path="posts/roller_shutters/roller_shutter-calibrate.png" path-detail="posts/roller_shutters/roller_shutter-calibrate.png" alt="Roller Shutter Calibrate" caption="Roller Shutter Calibrate" %}


### Add to Home Assistant

With that, it is now time to add the roller shutters to Home Assistant! 

* With CoIoT enabled, there is 1 more step recommended - switching from multicast to unicast: Go to `Internet & Security => Advanced - Developer Settings` and change the `mcast` value to your Home Assistant IP and CoIoT port. e.g. `192.168.100.100:5683`. With that, the Shelly 2.5 switch should appear in your Shelly integration (ensure you have that integration installed). 
* You should receive a notification about the new device. If not, a restart of Home Assistant might help. 
* You should now have a new `cover` entity available in your Home Assistant, which you can add to your Dashboards, Scenes and Automations!! 🎉🎉🎉


* Bonus: for extra fun 🥳 , try out the custom Roller Shutter card from HACS:  https://github.com/Deejayfool/hass-shutter-card

{% include image.html path="posts/roller_shutters/roller_shutter-home_assistant_card.png" path-detail="posts/roller_shutters/roller_shutter-home_assistant_card.png" alt="Home Assistant Roller Shutter Card" caption="Home Assistant Roller Shutter Card" %}


## Credits

Big shout out to [Michalis](https://twitter.com/mzampetakis) for all his help putting this guide together !! 🙏 🍻



### Home Assistant Configuration 

You can find all my Home Assistant configuration [here](https://github.com/gsaslis/home-assistant-config/). 