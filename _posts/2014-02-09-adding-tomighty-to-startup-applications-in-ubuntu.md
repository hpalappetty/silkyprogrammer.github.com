---
layout: post
Title: 'Adding tomighty pomodoro timer to Ubuntu startup applications'
---

<p>I am a big fan of productivity tools, esp. observing and tweaking my own daily routines to achieve best results is one of my passion.Recently, I came across a pomodoro timer "Tomighty" and have been using it regularly on windows section of my machine. I have a Linux (Ubuntu) partition as well, where I play around with code and my lessons on programming. This post details, how I installed this pomodoro timer in Ubuntu as a startup application.This helps me avoid doing the following, everytime I start my System.</p>

    java -jar tomighty.jar

<p>Following are the steps to get this done on Ubuntu Machine</p>

      1. Download tomighty.jar from http://www.tomighty.org/download - All operating systems jar file.
      2. Copy this from Downloads to /opt or /tools wherever you keep your useful toolset.
      3. Create a tomighty.sh file for creating an entry in startup applications.


<p>Copying from Downloads to /opt or /tools can be done by</p>

    $ cp ~/Downloads/tomighty.jar /opt

    or

    $ cp ~/Downloads/tomighty.jar /tools

<p>Contents of tomighty.sh is </p>

    #! /bin/bash
    java -jar /home/hpalappe/tools/tomighty-0.7.1.jar

<p>Go to the gear sign on the top right most section on panel, click on startup applications and add a new entry. This solved my problem of getting tomighty working on Ubuntu.</p>