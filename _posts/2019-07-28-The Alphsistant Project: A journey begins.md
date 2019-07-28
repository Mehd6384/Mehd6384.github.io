---
layout: post
title: "The Alphsistant Project"
categories: [Alphsistant]
---
<img src="/images/kratos_front.jpg" class="fit image">

# Context 

Welcome to the Alphsistant Project ! After spending the year making game protoypes, I felt I was rather lost without a specific purpose. When I realised the end of my PhD was getting closer, I thought it would be nice to make a more global project that would feature all of my interests and skills. The Alphsistant Project aim is to create a vocal assistant with a face, powered by deep learning. Ideally, I want it to be able to generate text, speak it, synchronise facial animations. Additional features should be added over time.  


# Workflow 

To keep myself motivated, I plan to first create the full pipeline, and then refine and improve each part. Hence, here are the things that shall be done: 

* Sculpt the face. Retopologize.  
* Text to Speech model 
* Text Generation 
* Synchronise face with text  
* Make a pipeline 


# The Face 

I created a first version of the face (which will probably be adapted over time). A video with my very first shape keys is available [here](https://www.youtube.com/watch?v=VnPJdENJ87s)
For the face retopology, I followed [this tutorial](https://youtu.be/3L8eZAwmG2E) 

# Text to Speech 

It is my first contact with text to speech (TTS) approaches. Having not much of an expertise in this field, I followed sendtex's advices and went with the DC TTS model (Covolutional model with Guided Attention). It is a two-staged model, with a first part that transforms text input to a spectrogram while the second part upscales the spectrogram. [Sendtex's video](https://youtu.be/6bFN2YkN6bo) has a link to the github page holding the model. 

# Text Generation 

For now, I am going with the well-known GPT-2 from OpenAI. Check the [HuggingFace](https://github.com/huggingface/pytorch-transformers) Github page for the model and relevant instructions.

# Conclusion 

The Alphsistant Project is just getting started and a lot of work lies ahead ! I hope that keeping track of my progresses through blog posts will ensure motivation stays as high as possible ! Stay tuned :)   