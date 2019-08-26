---
layout: post
title: "The Alphsistant Project: Expected path to LipsSync"
categories: [Alphsistant]
---
<img src="/images/face_lm.png" class="fit image">

# Creating the face controller 

After some reflexion, I devised a possible way to create a face controller. The basic idea would be to learn through supervision a mapping between utterances and face movement. Similarly to the current Text2Speech model, I'd like to segment the phonemes and, instead of using them to generate sound, rely on these features to control the face. 
So in order to create the **sentence - face movement** mapping, I plan to :
1. Construct a dataset that would be obtained by extracting facial landmark from videos. For each sequence of image, also record the text. 
1. Use a network that would, upon observation of the text (and optionnally additional features, describing the mood or whatever feature deemed important) returns a sequence of values for the controller and the loss function would be based on mean square error over time between the mesh's facial landmarks and the target ones.  

# Current advancement. 

A pytorch model has been trained on the Helen dataset. Results are decent, but clearly lack precision. Currently trying to improve accuracy using FastAI framework.  
