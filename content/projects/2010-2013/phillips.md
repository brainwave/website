---
title: "Interfacing a Phillips Remote with AVR atmega8"
date: 2017-12-21T21:26:28+05:30
draft: false
---
Ability to control a robot using a remote would be useful. Remotes have the range of roughly a living room. I wanted a robot to just move based on my instructions. This was a very small scale project, as I was just beginning to learn the basics of Robotics.

To learn more on microcontrollers in general, and the AVR series in particular I worked on a project to interface a Phillips remote with atmega 8. Now that I had my usbasp ready, I could program and play around the microcontroller.

The remote sends encoded signals using Infra Red radiation. Many phillips remotes use the RC 5 protocol for encoding. Luckily, this open source protocol was also used by the remote controller of my phillips music system. Using a TSOP IR sensor, the project used the 16-bit timer peripheral and corresponding interrupts on atmega 8 to read the wave and take corresponding actions. This was later used to make a TV remote control robot.
