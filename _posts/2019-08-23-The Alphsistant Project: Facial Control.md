---
layout: post
title: "The Alphsistant Project: Creating useful addons"
categories: [Alphsistant]
---
<img src="/images/alphdien_bone2hook.png" class="fit image">

# Context 

Animating a face is a rather complex task. From what I've learned so far, it appears that the animation is enabled by three specific approaches. 

1. Using shape keys (smiles, cheek puffs, mouth deformation). Shapes keys are particularly useful for creating wrinkles and creases.  
1. Lattice-controlled deformations. 
1. Additional bones for more specific or local deformation. 

I found really useful workflow advives in the book **Blender Character Animation Cookbook** and I managed to create my first facial rig, which is showcased [here](https://www.youtube.com/watch?v=1ktlyoOD3oU). 

# Easin' the workflow 

Getting the first result, especially with lattices was really encouraging. Having done only body animation so far, I had very low expectations concerning the quality of my rig, but, as I matter of fact, I was rather pleased with what resulted from this. This however was only a draft and, once the first-time enthousiasm gone, I realized that the workflow inherent to facial rig preparation was rather tedious and repetitive, yielding an absurd number of clicks to get things done. That is: 

|            |             Fun part            |                                 Boring part                                 |
|------------|:-------------------------------:|:---------------------------------------------------------------------------:|
| Shape Keys | Creating the shape keys         | Mirroring shape keys Assigning vertex groups as masks                       |
|   Lattice  | Placing the bones for hooks (?) | For each bone, creating the hook, selecting target, assigning lattice point |
Thus, I created two Blender addons for automating this process. 

1. MirrorSK_Operator. Create your shape keys, your vertex groups, call the script and pouf, everthing is mirrored with specific groups assigned.
1. Bone2Hook. Create your lattice and place the bones you plan to use as hooks. Then, call the script and it will iterate over the bones and for each one create a hook, set the bone as target object and assign the closest lattice point to it. 

Code is available on [my github](https://github.com/mome36/BlenderWorkflowAddons)  and videos are [here](https://www.youtube.com/watch?v=Mszffr8R61k) and [here](https://www.youtube.com/watch?v=XKrTlb55Hqs&)

