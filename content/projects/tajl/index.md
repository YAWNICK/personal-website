---
title: "tajl: Split expenses without downloading an app"
date: 2025-03-31T10:09:50+02:00
draft: true
disable_share: true
categories: ["Programming"]
---

A simple webapp to split expenses with groups of people. No accounts, just invite sharing and localstorage.

<p>
<img src="https://img.shields.io/badge/python-3776AB?logo=Python&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/html-E34F26?logo=HTML5&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/css-1572B6?logo=CSS3&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/javascript-F7DF1E?logo=JavaScript&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/django-092E20?logo=Django&logoColor=white" height="30px"/>
</p>

<a href="https://tajl.yawnick.de/"><img src="https://img.shields.io/badge/Demo-000000" height="30px"/></a>

## Pitch

You're on a trip with a group of people and you need to track and split expenses. But everyone uses a different app for that and nobody wants to download another app. Also, nobody wants to create an account just for some simple group expense tracking. You just want a simple solution. tajl is the answer. You just create a group, share the invite code with everyone, and now everyone can add people and expenses. Whenever you want, you'll get a list of suggested equalizing payments to settle up.

## Features

- create groups
- share invite code, so other people can edit the group
- add people to groups
- add expenses, also with unequal shares
- view current balances
- get suggested payments to settle up

## Architecture

- Django backend
- Vanilla HTML/CSS/JS frontend
- group codes are stored in localstorage for persistence

## Dev story

I just really wanted to have this. Quickly put up a backend, and then asked myself if it's worth to use a frontend framework. I decided it's probably not much code and I rather wanted this to be super light weight and just see how far i can go with plain html/css/js.