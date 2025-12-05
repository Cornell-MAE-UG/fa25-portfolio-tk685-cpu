---
layout: project
title: Designing Lifting Mechanism for Maximum Height and Load
description: For ENGRD 2020 homework
technologies: [NA]
image: /assets/images/first_design_model.jpg
---

**Project Overview**

For this project, we were tasked with designing a mechanism capable of lifting the maximum possible weight to the greatest possible height. The given constraints included a design space of 150 cm by 50 cm, a rigid bar of fixed length, an actuator, and support structures. We were also provided with a list of Tolomatic actuators, allowing us to select the most suitable one based on our design approach.

**Conditions**
Problem: Design a pin-jointed actuator–bar mechanism inside a 150 cm × 50 cm rectangular space that can lift a payload at the top-right corner, and determine the maximum lift height and maximum weight it can raise.
Constraints: Mechanism must fit entirely within the 150 cm (length) × 50 cm (height) design envelope.
Objectives: to maximize vertical lift and payload
Degrees of freedom: One

**Actuator Choice – IMA55**

After comparing the IMA22, IMA33, IMA44, and IMA55 models, I found that although the actuator size increases progressively from 22 to 55, the maximum thrust grows at a much faster rate. Therefore, I selected the IMA55 actuator, which offers a peak thrust of 17.93 kN, an actuator length of 31.44 cm, and a maximum stroke length of 457.2 mm.


**Overall Design Choice**

I began by examining the actuators and noticed that their stroke lengths were all sufficient to span the diagonal of the design space, meaning the lifting direction could be freely chosen. I decided to orient the actuator diagonally from the bottom left to the top right. 

**Analysis**

*Rigid Bar*
![Design of my choice]({{ "/assets/images/first_design_model.jpg" | relative_url }}){: .inline-image-r style="width: 400px"}

As shown in the diagram, one pin connects the end of the actuator to the ground, another connects the end of the rod to the ground, and the final pin links the rod and the actuator, creating a stable triangular configuration. With this design, the mechanism achieved a maximum height of 40 cm and was capable of lifting a maximum weight of 5,668.5 N.







