---
layout: page
title: Superbike
description: My work on an all-electric motorcycle through Washington Superbike!
img: assets/img/Superbike_logo.jpg

importance: 2
category: work
---

The point of Superbike is to make an electric racing bike from scratch to compete in the biennial Motostudent competition.
At UW's Superbike team, I worked on the firmware subteam, helping manage embedded systems on the bike.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/bikePicture.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Here are the innards of the 2023 bike! Pretty dope.
</div>

Much of my work was devoted to calculating the state of charge of the bike at any given time. This is harder than it seems due to several variables that change the battery life.
I had to find a way to accuratley find the amount of "juice" left in the bike at any time taking into account temperature, number of cycles previously ran, and previous charge capacity.
The calculations were complex, and involved integral calculations which could not be done on the 3 MB microcontroller on the bike: 


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/SOC_Equation.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/SOC_code.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left the equation used to calculate State of Charge. On the right, sketch for a riemmann sum approximation for the function
</div>


In order to make the function work, I decided to implement it as a riemann sum instead of an integral. This introduced some error, but the reading was within 4% in tests which we deemed good enough.
Implementing the State of Charge function in the actual firmware was more than writing a simple sketch however. I had to learn about RTOS and add a priority to my task in order to make it work.
All in all, I learned a great deal about low-level systems programming in C through this project, and hope to keep working with embedded systems in the future.


