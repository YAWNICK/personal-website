---
title: "CatchCounter: Counting juggling catches with my Garmin watch"
date: 2025-04-12T16:09:50+02:00
draft: false
disable_share: true
categories: ["Programming"]
---

A Garmin ConnectIQ and Android app to count juggling catches based on hand movement data.

<p>
<img src="https://img.shields.io/badge/Monkey_C-000000?logo=Garmin&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/Java-EC2025?" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/Android-3DDC84?logo=Android&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/Bluetooth-0082FC?logo=Bluetooth&logoColor=white" height="30px"/>
</p>

<!--more-->

<a href="https://github.com/YAWNICK/CatchCounter"><img src="https://img.shields.io/badge/GitHub-CatchCounter-000000?logo=GitHub" height="30px"/></a>

<a href="https://youtu.be/SSTXHXLsrTM"><img src="https://img.shields.io/badge/YouTube-Demo-FF0000?logo=YouTube" height="30px"/></a>

## Pitch

You're trying to set a new juggling endurance record, but counting catches in your head makes you loose focus? Use CatchCounter and your Garmin watch takes care of counting catches for you! All you have to do is wear your watch!

## Interesting Challenges

### Where to process the sensor data

The watch has very limited resources and a weak and slow cpu. Processing on the watch would have the advantage of only needing to communicate very little with the phone or not even needing the phone in the first place. But only simple processing approaches are possible on the watch due to the resource constraints. So I opted to stream the sensor data to the phone for processing.

### Live streaming accelerometer data

The watch can get sensor data 10 times per second. It uses BLE to communicate to the phone app. Sending 10 messages per second is too much, so I send 1 message per second with the x,y,z axis accelerometer data from the watch to the phone.

### Catch detection

There are many ideas with varying degrees of complexity. As version 1 I implemented a check for a large delta between two z axis acceleerometer datapoints, which happens every throw when a ball is released from a hand.

## Features

- 3-5 ball juggling catch counting. Lower number of balls works better.

## Architecture

- A Garmin ConnectIQ app is installed on the watch
- The official Garmin Connect app must be installed on the phone. It provides an interface for BLE communication with a watch.
- The CatchCounter Android app is installed on the phone and uses the Garmin BLE library.
- The Garmin ConnectIQ app on the watch continuously sends messages with accelerometer data to the phone, triggering processing in the phone app

## Dev story

This is a project for a mobile computing and IoT class at KIT. The task was to write a phone app that communicates with a sensor gadget over Bluetooth and provides some kind of functionality. The juggling catch counter idea was there quickly, but I was unsure about the hardware constraints given the live online nature of the idea. For catch detection I first logged the accelerometer data of myself juggling different numbers of balls to get a sense of the quality. Eventually I decided that the simple z axis delta approach should work okay. To be honest, with 5 balls I have to exaggerate the hand movements a bit, but other than that it works well. And, last caveat, of course I only track one hand and then double the catch count, so the app only reports even numbers of catches.