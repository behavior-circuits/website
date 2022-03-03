---
permalink: /docs/utility_idea/
title: "Behavior Circuits for Utility Combination"
layout: single
toc: true

---


There are roughly speaking two types of utility based agents.
Systems which assign utility to actions and  planner systems which assign utility to the current state of the world.
While behavior circuits can be used for both, they are better suited for the former, which is why the rest of this article will focus on action based utility systems.

# Action based Utility Example

While the actions in  action based utility systems can be as concrete as move left or right, actions can also be more abstract.
In this example scenario a robot has two actions:
* nagivate to goal
* avoid humans
In any given scenario the robot has to decide which action to perform.
In a action based utility system this is done by assigning each action a utility score and picking the action with the largest score.

This utility is commonly a function dependent on some kind of measurable state of the world.
For example, the closer a human is to the robot, the more utility the *avoid humans* might have.
This can be described using the simple function shown below:

![simplest_utility_function](https://raw.githubusercontent.com/behavior-circuits/website/master/images/simplest_utility_function.png)

Since we want to tune this utilty, in practice the function will feature several parameters.

![param_utility_function](https://raw.githubusercontent.com/behavior-circuits/website/master/images/param_utility_function.png)

The parameters of this function control the general shape as well as the scale of the function.

The problem now arises that in the design of the agent, the utility should not only depend on distance to the human.
Perhaps the angle to the human is also important. Maybe one should also consider the lighting conditions which govern wheter the human is able to spot the robot.
Depending on the situation one could think of many more parameters that should influence the final utility of the *avoid humans* action.

Finding a utility function for a single variable is managable, but finding a utility function for an arbitrary amount of parameters is hard.
Moreove if one has found such a function but then discovers that he has forgotten a parameter one has to start the work all over again.


Behavior Circuits can be used to adress this problem.
The Idea is to only design single variable utility functions and combine them using a circuit.

Going back to our robot example, perhaps the utility of the *avoid humans* action should be large 
if the distance and angle to the human is small, or if the lighting conditions are very bad (meaning the human might miss the robot and stumble over him).


Using a behavior circuit such a utility system can be expressed like this:

![example_utility_circuit](https://raw.githubusercontent.com/behavior-circuits/website/master/images/example_utility_circuit.png)


The three functions model large utility for small distances, small angles and good lighting respectively.
While the interconnection is done using a AND gate and a OR gate.
These logic gates now describe the relationship between the different utility functions.

# Behavior Circuits defined on [0,1]
While conventional binary logic circuits deal only in binary values, utility functions typically are arbitrary positive numbers.
A possible extension of binary logic are the so called s-norms and t-norms.
These operate on the range of zero to one while behaving just like the logic circuits.

Using these norms the gates of the behavior circuit can be defined as seen below:


![s_t_norms](https://raw.githubusercontent.com/behavior-circuits/website/master/images/s_t_norms.png)


This means that in order to use behavior circuits the single variable utility functions need to be capped at 1.
The added benefit of this upper limit for the utility functions is that it keeps them all at the same scale.
Otherwise a function with much larger values might overpower all other functions.


# Beyond the Basics

The basics of behavior circuits for utility combination can be summarized as:
* Defining single variable utility functions with a upper limit of 1 and a lower limit of 0
* Combine these functions using logic gates (based on t-norms and s-norms) 


While the initial example used basic AND and OR gates, there are in fact more continous gates than just these basics.
There are gates in which the utility of one behavior supercedes the utility of another, there are circuits where the relative contribution of two functions is governed by a third input.

With all these gates the question remains: how to effectively design a ciruit which combines different utility functions.
All this is governed in the section [Design for Utility Combination](utility_design.md)




