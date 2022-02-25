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

The code which can be found [here](https://github.com/behavior-circuits/150_lines_example) is divided into four files.
The main brain of the robot is located in the `fusion.py`, the sensor readout from camera and sonar sensors are located in `vision.py` and `sonar.py`.
Together the sensor nodes provide the polar coordinates of the following objects:
* The closest obstacle
* The cat
* The cheese
* The curtains

The agent takes these positions and converts them into the following behaviors:
* The closest obstacle -> avoid collisions
* The cat -> flee from cat
* The cheese -> collect cheese
* The curtains -> hide

This is done using a polynomial approach similar to the one described in  the [utility design tutorial](https://behavior-circuits.github.io/website/docs/utility_design/).

TODO ADD DESCRIPTION OF BEHAVIORDESIGN (DESCRIBE WHY ONLY ANGULAR VELOCITY NEEDS TO BE UPDATED)


These behaviors are then combined using a behavioral circuit.
It is designed such that the mouse tries to avoid the cat and get to the chees in equal parts, this is realized by an OR gate.
\\
Hiding on the other hand only makes sense if the robot wants to flee from the cat. The urge to hide should thus become stronger the stronger the robot wants to flee from the cat.
This can be modeled by an INVOKE gate.
Collisions should of course be avoided at any time and so collision avoidance overrides any other behavior by means of a PREVAIL gate.

The final circuit can be seen down below.

![150_line_circuit](https://raw.githubusercontent.com/behavior-circuits/website/master/images/150_lines_circuit.png)



