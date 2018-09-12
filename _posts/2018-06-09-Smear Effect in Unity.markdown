---
layout: post
---
<img src="/images/fulls/02.jpg" class="fit image">

# Smear effect in Unity 

Recently, I came across a video displaying smear effect in Unreal. Pretty neat stuff, especially when your game has a cartoony side. 
After looking at some implementations, in particular from Chris Wade (https://github.com/cjacobwade/HelpfulScripts/blob/master/SmearEffect/Smear.shader), I figured out the secret recipe for this effect which lies in the vertex shader

## Vertex shader for smear effect 

Basically, the effect relies on the Unity surface shader with a little help from a vertex shader. This implementations needs to be provided current and previous position of the object through a C# script. With this, we compute a local and a global offset: 

```c
//Compute offsets 

fixed4 worldPos = mul(unity_ObjectToWorld, v.vertex);
fixed3 worldOffset = _Position.xyz - _PrevPosition.xyz; 
fixed3 localOffset = worldPos.xyz - _Position.xyz; 


float dirDot = dot(normalize(worldOffset), normalize(localOffset));
fixed3 unitVec = fixed3(1, 1, 1) * _NoiseHeight;

// Make sure worldOffset isn't too big 
worldOffset = clamp(worldOffset, unitVec * -1, unitVec);
worldOffset *= -clamp(dirDot, -1, 0) * lerp(1, 0, step(length(worldOffset), 0));

// Apply scaled noise 
fixed3 smearOffset = -worldOffset.xyz * lerp(1, noise(worldPos * _NoiseScale), step(0, _NoiseScale));
worldPos.xyz += smearOffset;
v.vertex = mul(unity_WorldToObject, worldPos);
```

The current implementations relies on a custom noise function that may appear heavy. Maybe a time-scrolled perlin noise would be interesting to test. 

## A small demo: 

https://youtu.be/X3LlX-zTCko
