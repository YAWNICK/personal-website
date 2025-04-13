---
title: "StabiShare: A platform for exercise sharing and smart workout generation"
date: 2025-04-12T17:09:50+02:00
draft: false
disable_share: true
categories: ["Programming"]
---

A platform and webapp for creating and sharing exercise repositories, and for generating workouts that balance exercises between defined muscle groups.

<p>
<img src="https://img.shields.io/badge/python-3776AB?logo=Python&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/typescript-3178C6?logo=TypeScript&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/django-092E20?logo=Django&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/angular-0F0F11?logo=Angular&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/ionic-3880FF?logo=Ionic&logoColor=white" height="30px"/>
</p>

<!--more-->

## Pitch

You know you need to do your core exercises. But you don't want to think about which exercise to do next and you also don't want to do the same core workout every time. The solution? Dump all exercises you know into a StabiShare space or join you track club's space and let StabiShare generate a random workout for you. Just put in the length, and how much of each muscle group you want to focus on. StabiShare does the rest and you never get bored or have any excuses! The generated workout is even balanced, so that you don't have a bunch of exercises of the same focus in a row.

## Interesting Challenges

### Balancing exercise focuses in a workout

When generating a workout exercises with the same focus should be as far apart from each other as possible. But there are likely different numbers of exercises for each focus for this workout, as per the user-specified focus distribution. Generating this workout exercise sequence is not trivial.

## Features

- Create spaces, and focuses and exercises in a space
- Make a space findable by anyone or just via invite
- Different space join modes: public (open access) and private (request - accept)
- Different space roles with e.g. exercise creation permission: admin, editor, member
- Workout generation with user specified focus distribution

## Architecture

- Django backend
- Angular + Ionic frontend

## Dev story

Main motivation was my actual need for such an app and my desire to gain more experience with the stack we used for TEQST (Django + Angular). And also I had fun trying to make it an actual platform where users can sign up, and publish their spaces to the world, as opposed to just an offline single player app. I worked on if on and off during my undergrad studies, usually more during lecture-free periods. Also fun would be to write an Android app / Garmin ConnectIQ app frontend for this so that I could run the workout from the watch. 