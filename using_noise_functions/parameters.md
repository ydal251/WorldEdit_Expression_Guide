## **Parameters** {#parameters}

### *Seed* {#seed}

 ![](../.gitbook/assets/noise_functions/noise\_seed.gif)
| *//gen \-c light\_blue  perlin(SEED,x,y,z,0.03,1,0) \> 0.5 //gen \-c magenta    voronoi(SEED,x,y,z,0.03) \> 0.5 //gen \-c yellow ridgedmulti(SEED,x,y,z,0.03,1) \> 0.5* |
| ----- |

*(Command 5.1.1)*

This is the ‘*seed*’ value that the noise function starts from. Like the Minecraft seed, if all your other parameters are the same, including location if using world coordinates, then you will get an identical output when using the same seed.

You can change this value when you want to see a different version of the same noise output.

This parameter must be an integer value.

### *Frequency* {#frequency}

![](../.gitbook/assets/noise_functions/noise\_frequency.gif) 
| *//gen \-c light\_blue  perlin(1,x,y,z,FREQUENCY,1,0) \> 0.5 //gen \-c magenta    voronoi(1,x,y,z,FREQUENCY) \> 0.5 //gen \-c yellow ridgedmulti(1,x,y,z,FREQUENCY,1) \> 0.5* |
| ----- |

*(Command 5.3.1)*

Frequency can be thought of as how dense or closely packed your noise function will be. As you can see in the example above, as the frequency value increases our cube gets much busier.

When using anything other than the normalized **\-1…1** coordinate system, then your frequency values are ideally placed in the area of **0.01**. When using the normalized coordinates, then you will see the best results with a frequency in the area of **1.00**.

Frequency must be given as a number, either integer or decimal.

### *Octaves & Persistence* {#octaves-&-persistence}

In essence, the usage of Octaves and Persistence within noise is how you would take away the smoothness of the output and add in some more detail.

Used in both the Perlin and Ridgedmulti noise functions (i.e not Voronoi), Octaves is the parameter that determines how many runs of the noise functions to add on top of eachother. You may have noticed in the previous examples that all of the perlin() functions ended with perlin(..., **1**, 0\) and ridgedmulti() ended with ridgedmulti(..., **1**). In both cases this ‘**1**’ means they each ran with a single octave.

This number must be at least 1, but as we increase it the underlying functions will re-run our noise function, with some modification to the input values, as many times as we have input and will combine all runs before returning the value. Here’s a timestamped [link](https://www.youtube.com/watch?v=CSa5O6knuwI&t=652s) to a video visualizing this concept.

![](../.gitbook/assets/noise_functions/noise\_octaves.gif) 
| *//gen \-c light\_blue  perlin(1,x,y,z,0.02,OCTAVES,0.5) \> 0.5 \- //gen \-c yellow ridgedmulti(1,x,y,z,0.02,OCTAVES) \> 0.5* |
| ----- |

*(Command 5.5.1)*

In both examples you can see that increasing from 1 octave to 2 has quite an impact, but the change becomes more and more subtle as you increase the number.

This is because each additional octave has a weight that determines how much of the final value it will influence. For example if the weight was **1** then every octave will be as strong as each other and the final output value will just be a sum of each of those octaves. If it was **0.5** then each run would be half as strong as the previous.

We can’t control this value for Ridgedmulti[^11] , but we can for the Perlin function, which brings us to the Persistence parameter.

[^11]: It's hardcoded at 0.5.

![](../.gitbook/assets/noise_functions/noise\_persistance.gif) 
| *//gen \-c light\_blue perlin(1,x,y,z,0.02,8,PERSISTENCE) \> 0.5 – \-* |
| ----- |

*(Command 5.5.3)*

This example demonstrates the result of increasing the weighting/strength of each of the 8 octaves of noise within our function. 

Low values give us a smooth texture, moderate values give us a more detailed texture, and high values can give a very fuzzy result.

![](../.gitbook/assets/noise_functions/noise\_terrain.gif)

| *//gen \-c lime\_terracotta perlin(123,x,y,z,0.03,8,PERSISTENCE)\>((y+32)/64)\*3* |
| :---- |

*(Command 5.5.4)*

An alternative way to visualize this is with noise that has been compressed based on the Y level, giving us what looks like surface terrain.

Again, as the value of the persistence increases so too does the roughness of our terrain. In the example above we have a selection with a height of 64, hence the *((y+32)/64)\*3* threshold. The values for the persistence range from 0 to 0.5 and back again.

Overall, Octaves and Persistence are useful to give you a pattern that doesn’t look too smooth, which is especially useful for terrain and texturing.


### *Coordinates* {#coordinates}

![](../.gitbook/assets/noise_functions/noise\_coords.gif) 
| *//gen \-c light\_blue  perlin(123,x,y,z,0.03,1,0) \> 0.5 //gen \-c magenta    voronoi(123,x,y,z,0.03) \> 0.5 //gen \-c yellow ridgedmulti(123,x,y,z,0.03,1) \> 0.5* |
| :---- |

*(Command 5.2.1)*

The three coordinate values are the input coordinates which give the noise function a point to sample from. By default, you would use “**x,y,z**” which is the x, y, & z values for each block in your selection.

If you were to set any of these coordinates to a fixed value such as **1** for “**y**” then every block in your selection will be treated as if it were at Y-level 1\. Same for the other axes.

Coordinates must be an “**x,y,z**” variable, number, custom variable, or any combination of the three.

![](../.gitbook/assets/noise_functions/noise\_offset.gif) 
| *//gen \-c light\_blue  perlin(1,x,y+(...),z,0.03,1,0) \> 0.5 //gen \-c magenta    voronoi(1,x,y+(...),z,0.03) \> 0.5 //gen \-c yellow ridgedmulti(1,x,y+(...),z,0.03,1) \> 0.5* |
| :---- |

*(Command 5.2.2)*

In *(Command 5.2.2)* you can see what happens as we add a constant to the input value for Y. We get an offset in the output noise.

![](../.gitbook/assets/noise_functions/noise\_scaling.gif) 
| //gen \-c light\_blue  perlin(1,x,y\*(...),z,0.03,1,0) \> 0.5 //gen \-c magenta    voronoi(1,x,y\*(...),z,0.03) \> 0.5 //gen \-c yellow ridgedmulti(1,x,y\*(...),z,0.03,1) \> 0.5* |
| :---- |

*(Command 5.2.3)*

Instead of adding to the value, if we instead multiply the coordinate input, we will squish the output along that given axis.

![](../.gitbook/assets/noise_functions/noise\_scaling2.gif) 
| *//gen \-c light\_blue  perlin(1,x,y/(...),z,0.03,1,0) \> 0.5 //gen \-c magenta    voronoi(1,x,y/(...),z,0.03) \> 0.5 //gen \-c yellow ridgedmulti(1,x,y/(...),z,0.03,1) \> 0.5* |
| :---- |

(*Command 5.2.4*)

In contrast with the previous example, if we instead divide the coordinate value then we will stretch along that axis.

### *Threshold* {#threshold}

![](../.gitbook/assets/noise_functions/noise\_threshold1.gif) 
| *//gen \-c light\_blue  perlin(1,x,y,z,0.03,1,0) \< THRESHOLD //gen \-c magenta    voronoi(1,x,y,z,0.03) \< THRESHOLD //gen \-c yellow ridgedmulti(1,x,y,z,0.03,1) \< THRESHOLD* |
| :---- |

*(Command 5.4.1)*

You may have noticed throughout the previous examples that each command ended with *\<0.5* which in the context of our examples means that a block is only places where the noise function returns a value less than 0.5.  
We do this as these functions will return a value between 0 and 1, so without any further condition, we would fill every block where the value is not 0\. 

To put this value range to use, what we instead do is give it some condition to meet, effectively acting as a threshold or even density. You can see in the above example that as we increase the maximum value of our noise that additional layers of blocks are added.

Keep in mind that we can also do ***\>**Threshold* (in contrast to ***\<**Threshold*). When using it this way you can think of it like a barrier. Only sufficiently large values may pass, so the higher the threshold, the less comes through. Depending on what we have and we want to achieve, we choose one or the other.

![](../.gitbook/assets/noise_functions/noise\_threshold2.gif) 
| *//gen \-c light\_blue  perlin(1,x,y,z,0.03,1,0) \> THRESHOLD //gen \-c magenta    voronoi(1,x,y,z,0.03) \> THRESHOLD //gen \-c yellow ridgedmulti(1,x,y,z,0.03,1) \> THRESHOLD* |
| :---- |

![](../.gitbook/assets/noise_functions/noise\_greater.gif) 

![](../.gitbook/assets/noise_functions/noise\_less.gif) 

If we instead fill in each new layer with stained glass you can see how these layers stack up together.

This method is what was used in one of the previous examples [Command 2.3.3](../generate/type_data.md), to shade in the selection based on the noise function output.

Thresholds are not limited to a set value, we can make it be any condition we want, for instance we could make this threshold increase as the Y-level increases.

![](../.gitbook/assets/noise_functions/noise\_normalized.gif) 
| *//gen light\_blue  perlin(1,x,y,z,3,1,0) \> (y+1)\*(...)  //gen magenta    voronoi(1,x,y,z,3) \> (y+1)\*(...) //gen yellow ridgedmulti(1,x,y,z,3,1) \> (y+1)\*(...)* |
| :---- |

*(Command 5.4.2)*

What we are doing here is using normalized coordinates and then increasing the Y value by 1\. This is because **0..2** is easier to work with than **\-1..1** for this example.   
Then we multiply our Y-level threshold by some value to squish it down towards the bottom.

You can see in the above example that as we reduce the number we squish by, that the noise starts to become more pronounced as you go up in the selection, while the lower section gets denser.

If we additionally set y to a constant value we get a height map.

![](../.gitbook/assets/noise_functions/noise\_heightmap.gif) 
| *//gen light\_blue  perlin(1,x,0,z,3,1,0) \> (y+1)\*(...)  //gen magenta    voronoi(1,x,0,z,3) \> (y+1)\*(...) //gen yellow ridgedmulti(1,x,0,z,3,1) \> (y+1)\*(...)* |
| :---- |