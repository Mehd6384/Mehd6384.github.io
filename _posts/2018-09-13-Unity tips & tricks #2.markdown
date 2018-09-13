---
layout: post
title: "Unity Tips & Tricks #2: 2.5D Controller"
categories: [Unity, Gamedev, Controller]
---
<img src="/images/san.jpg" class="fit image">

# Setting up a controller

Designing my dream controller for a TPS game has proven way more difficult than I intially thought. Sure, it's quite easy to add a collider and a rigidbody to a character and apply forces to move it. But there is no way a raw approach such as this one leads you to a subtle, delicate and awesome controller. A controller that is responsive, that makes you feel the character's explosiveness, strength, without letting it slide, or drift or feel unatural. Of course, reaching such a level of perfection requires **a lot** of polishing, but through this simple prototype, I have uncovered some of the important principles to manage a character. Though I was inspired by the 2D phases in [NierAutomata](https://www.youtube.com/watch?v=gaBUAw0W6bU) I didn't have anything precise in mind designing this prototype. I have sequentially thought of a side runner, Mario-style, a fighting game via *balls*, but so far, I've not implemented any. Anyway, here are my hard-earned 2.5D controller secrets: 


## Moving:

1. In case you consider a character with the god-blessed ability to jump, it seems usually necessary to apply additional gravity to the character, otherwise, the fall might appear rather slow. 
1. I've had interesting results when I lerped this additional gravity while jumping. The idea is that having a low gravity at the beginning of the jump allows you to apply a smaller jumping force to reach the same height, which in turns can give you more expression through the animation. 
1. Lerp the rigidbody's drag, or at least change it when moving. This is **fundamental**.  
1. I also added a function checking the maximal rigidbody's velocity. If the velocity exceeds a threshold, I gently lerp it to the maximal value. This way, you can have a fulgurant acceleration while still conserving an admissible maximal velocity. Can be wise to only constraint the horizontal speed.
1. A nice addition is a function that transfers horizontal speed on landing. For some reason, my character always lost most of its speed when touching ground. Hence, this function transfers a ratio of the rigidbody's horizontal speed on landing. Gives some pretty cool effect, enhancing the animation. 
1. FINISH jumping ! 

[![2.5D Controller](http://img.youtube.com/vi/Kpp5O6CXXN8/0.jpg)](http://www.youtube.com/watch?v=Kpp5O6CXXN8 "San Movements")
