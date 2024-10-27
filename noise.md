# What is “Noise” anyway? {#what-is-“noise”-anyway?}

When it comes to “Noise Functions”, we aren’t talking about something you hear, what we are actually talking about is Coherent Noise. 

Think about the static on an old TV, black and white pixels all over. That is like Random Noise, where each pixel (or block) has no relation to its neighbours, it is just random, and mostly not useful for us. 

In contrast, Coherent Noise flows relatively smoothly between points, so there aren’t big differences between adjacent values. This is an example of Coherent Noise where each pixel has a brightness value determined by the noise function:

![](.gitbook/assets/noise\_noise.png)

You can see that it looks kind of blurry, but there are no points where completely black sections are beside completely white sections without some kind of gradient of points between them.

This smoothness makes it great for procedural generation which itself is used all over the place in game and art design. See this excellent [presentation](https://www.youtube.com/watch?v=CSa5O6knuwI) by one of the Minecraft devs explaining how they use this noise to generate Minecraft worlds.

There is plenty more that we could get into with noise as a concept and we would encourage you to research it further if interested. However, for our purposes here it is often better to learn by example and experimentation.
