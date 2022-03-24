---
permalink: /docs/about/
title: "The Idea behind Behavior Circuits"
layout: single
toc: true

---

Behavior Circuits extend the binary logic circuits to continous values.
Instead of combining binary values, this allows behavior circuits to combine continous functions.

There are two main applications for these circuits:

* Combining normalized utility functions based on simple rules to create more expressive agents
* Directly combining movement commands of different subsystems based on simple rules


## Combining Utility Functions

When designing utility based agents for video games or robotic, the design of utility functions with multiple variables is often more an art form than a science.
Behavior circuits can be used to structure this process by describing these functions as a number of single variable utility functions combined using a behavior circuit.
More information on this application can be found [here](https://behavior-circuits.github.io/website/docs/utility_idea/).

## Directly combining steering Commands

Especially in behavior based robotics, one often designs indipendent behaviors which are meant to directly control the robot.
The Question for the designer of the robotics system is then, how to choose when each behavior should be active.

Behavior circuits can be used to directly connect these control commands based on a rule based circuit.
These circuits can use the current commands of the behaviors themself to decide on the final steering command.
More information on this application can be found [here](https://behavior-circuits.github.io/website/docs/control_idea/).
