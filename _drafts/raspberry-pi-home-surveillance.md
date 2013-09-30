--- 
layout: post
title: Use your Raspberry Pi as home surveillance
categories: 
- computer
description: to be filled
---
I was unlucky enough to be broke in this year, thiefs taking laptops and iPads
(please note than I'm an iOS developer, therfor yes I owned more than one). I
always had in mind to put a video surveillance inside my small apartment, now I
had a reason.

More than a decade ago, I had to do a similar system using Axis camera. I was
finding my office door opened every morning, and didn't know who was doing it.
I put an axis recording all videos, using motion detection, and found out the
cleaning guy working at 6AM was opening all doors on the building level, to
later close all of them and sometimes forgot a few. A decade later I would have
expected those Axis camera to blew XXX in the water, doing more than it did a
long time ago. To my surprise it doesn't, it still costs half my ass, and
convinced me to look for other option.

#### What to buy

I bought a Raspberry Pi (model B, the most powerful at the time), and I already
owned a Logitech XXX which I had no use for, since the Apple Thunderbolt display
includes a webcam, as well as all Apple laptops. 

I found its new use.

#### What you won't get

I tried for weeks to make my Pi work with motion, recording 960x720 images. It
kept crashing and as I was using it headless (no HDMI screen at home) I had a
very hard time debugging this. I kept getting Kernel panic and IO errors.

It ends up not using Motion works, my feeling is the CPU isn't powerful enough.
I could probably have it working for 320x240 image size, but I want high
resolution to be able to see what happened while I was away.

#### What I got

The stable configuration I did uses `uvccapture` with startup scripts to store
a single image every second. I actually get a single image every two seconds,
which confirms what I first thought: not enough CPU.

#### The next step

I'm going to buy a [Reed switch](http://en.wikipedia.org/wiki/Reed_switch) to
detect the opening of my door, and send myself a text message every time it
happens. Paranoid? Not really, it allows you to know your system currently
works, how many times do you think an alarm system hasn't been working for
months, finding it *after* a burglar. It even happens to Banks.

#### Wifi configuration
http://svay.com/blog/setting-up-a-wifi-connection-on-the-raspberrypi/
