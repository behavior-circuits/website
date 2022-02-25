---
permalink: /examples/150_lines/
title: "Robot AI in less than 150 Lines of Code"
layout: single
toc: true

---

The following example is meant to illustrate how simple it is to develop mobile robot AI using behavior circuits.

In this example scenario, two robots called mouse and cat respectively compete in an arena.
The aim of the mouse is to reach a cheese placed in the arena before it is cought by the cat.
Conversely the cat tries to first catch the mouse.
The mouse can try to avoid the cat by hiding behind one of two colored curtains.

Both robots are equipeed with cameras and ultrasonic sensors and feature a ROS interface.
Using behavior circuits it is possible to create a intelligent of the mouse in less than 150 lines of code.
These include all necessairy code to detect the cat, cheese and hiding places using the camera and read out the ultrasonic sensors.


