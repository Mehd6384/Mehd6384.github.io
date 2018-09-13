---
layout: post
title: "Unity Tips & Tricks #1: Skating game"
categories: [Unity, skating]
---
<img src="/images/skate1.jpg" class="fit image">

# GameDev Insights 1: Skating game, the beginning

One of the main incentives for starting this blog was for me to keep a trace of some of the hard-earned insights both in game programming and machine learning. Indeed, I recently found myself fighting with some recurrent problems, having forgotten the solution I came up with in a previous game prototype. In order to increase efficiency and maybe help out some others self-taught game devs, I tought blog posts could be a nice solution !

## Context 

While browsing Twitter and Reddit, I came across some videos promotting the game SKTBRD, currently under developpement by [KevKev](https://twitter.com/Der_Kevin). The game feel really appealed me and I thought that it would be interesting to figure out how to do something similar. 

## My realisation

After a few hours of works, here's what I came up with: 

[![Skating ! ](http://img.youtube.com/vi/kTH7jAw3kyk/0.jpg)](http://www.youtube.com/watch?v=kTH7jAw3kyk "Skating")

The whole scene is rather basic but I was satisfied with the physics aspects.


## Some insights gained  

### Camera
Firstly, it was in this game that I figured out the setup for nice, smooth, lerping camera. 

Basically I: 

1. Update the camera's rotation, look target in the `Update` method 
1. Added the code for updating the camera position in the `FixedUpdate` method

### Skater

In the current state, the player's rotation relies on the **concatenation of two quaternions** and the applied force's vector's rotation. 

* A first rotation that would align the player's forward axis with the current rigidbody's velocity. Both vector are projected on the **`y = 0`** plane, using `Vector3.ProjectOnPlane(vector, plane_normal)`
* The second rotation aligns the player's up vector with the current ground normal. The latter is obtained via **raycasting**. 
* Finally, forces are rotated to match player's input, according to camera position. This way the player rotates eventually towards this direction. 


### Specific stuff

* I locked all rotations axis in the rigidbody's definition. This prevent unwanted flips. 
* I separated airborne and grounded rotation. Indeed, I use an important speed of interpolation to nicely follow curves. This would make the skater snap when jumping, which was unsatisfying.  
* The rotation using the ground's normal is set to the **identity** when airborne
* `Quaternion.FromToRotation` is likely to be a good friend in this setting.

By the way, [here's the whole code.](https://github.com/Mehd6384/Unity/tree/master/SkatingGame)

## TODO

As I said, the game physics are quite satisfying, from a realistic point of view. However, even though it seems obvious, fun (both in creating and playing the game) depends heavily how you tweak reality. I'm now aiming to 
* Allow wall riding
* Implement the possibility of jumping and falling into the same quater
* Allow slid