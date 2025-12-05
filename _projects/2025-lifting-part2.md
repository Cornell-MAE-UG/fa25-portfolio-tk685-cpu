---
layout: project
title: Beam selection for the lifting mechanism
description: For ENGRD 2020 homework
technologies: [NA]
image: /assets/images/second_design_model.jpg
---

**Project Overview**

For this project, we were tasked with designing a mechanism capable of lifting the maximum possible weight to the greatest possible height. The given constraints included a design space of 150 cm by 50 cm, a rigid bar of fixed length, an actuator, and support structures. We were also provided with a list of Tolomatic actuators, allowing us to select the most suitable one based on our design approach. Then, based on our design, we were asked to design and select the beam that we want to use.  

**Conditions**
Problem: Choose suitable beam to use for the pin-jointed actuator–bar mechanism from part 1
Constraints: 
- vertical deflection is below 2% of beam's legnth and is most mass-efficient possible
- the height of the bar is 9.93 cm.
Objectives: to design the bar that can withstand the force that the actuator creates
Degrees of freedom: One

**Overall Design Choice**

I began by examining the actuators and noticed that their stroke lengths were all sufficient to span the diagonal of the design space, meaning the lifting direction could be freely chosen. I decided to orient the actuator diagonally from the bottom left to the top right. 

**Analysis**

*NOT Rigid Bar*

Assumptions: 
- only transverse force applied on the bar
- load is not moving, therefore not contributing affecting the bar
- weight of actuator is negligible
- gravity is 9.81N/kg

When I calculated the weight of IMA55 actuator, it was 243N which is approximately one percent of the force that the acutator is generating. So, for the simplicity of the problem, I decided to make ignore the weight force acting on the bar. 

![Design of my choice]({{ "/assets/images/second_design_model.jpg" | relative_url }}){: .inline-image-r style="width: 400px"}

According to our calculation, we need a Ix value of 0.0000913 (10^6 mm^4), which all(W, S, C, and angle) shapes has bigger value of. So, I tried to find one with the lowest weight by comparing each shapes' small area. Based on the calculations, I found that angle has the lowest weight.
So, my beam choice will be the following:

*Beam Choice*
Shape: Angled (equal length)
Material: Steel
Height: 9.93cm
Surface Area: 312 mm^2

