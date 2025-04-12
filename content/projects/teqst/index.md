---
title: "TEQST: Tool to easily quench speechdata thirst"
date: 2025-03-31T10:09:50+02:00
draft: false
disable_share: true
categories: ["Programming"]
---

![>TEQST Logo<](images/teqst.png)

A mobile-first web platform to create audio recordings of texts (e.g. ASR training data). I'm very proud of this acronym.

<p>
<img src="https://img.shields.io/badge/python-3776AB?logo=Python&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/typescript-3178C6?logo=TypeScript&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/django-092E20?logo=Django&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/angular-0F0F11?logo=Angular&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/ionic-3880FF?logo=Ionic&logoColor=white" height="30px" align="left" style="margin-right:10px;"/>
<img src="https://img.shields.io/badge/PostgreSQL-4169E1?logo=PostgreSQL&logoColor=white" height="30px"/>
</p>

<a href="https://github.com/TEQST/TEQST"><img src="https://img.shields.io/badge/GitHub-TEQST-000000?logo=GitHub" height="30px"/></a>

## Pitch

You need a few people to record a few sentences for you? You need a bunch of people to record large amounts of ASR data? In any case, TEQST is what you're looking for. It's designed for easy, intuitive, and efficient audio recording by your speakers. Just upload your texts and share a link with them. Then you can track you speakers' progress, hours, and audio quality. 

I needed a small ASR test dataset for a group project once, and with TEQST we were able to quickly produce ca. 1000 samples spending a collective 2h on recording - barely more than the audio data itself.

## Features

- 3 Roles: Publisher, Speaker, Listener
- Publisher can create folder structure and upload texts in leaf folders
- Publisher can share folders with speakers
- Speaker can record texts
- Publisher can listen to recordings and see statistics
- Publisher can download data
- Publisher can share folder with listener
- Listener can listen to recordings

## Architecture

- Django backend with rest-like API
- Angular + Ionic frontend

## Dev story

This was PSE (Practical Software Engineering) project in my 3rd Semester at Uni, developed in a team of 5. We built the initial version in one semester and continued to work on it for the following 2 years. I was mainly involved in the backend, later more in the frontend. We've used it with Postgres and SQLite databases.