## **Voronoi Edge Pattern** {#voronoi-edge-pattern}

### *Goal* {#goal}

What would be interesting to achieve is a Voronoi edge pattern using the inbuilt Voronoi noise function. By default this function gives us patterns like this   

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_goal1.png)

| *//gen \-c white v=voronoi(123,x,y,z,0.03);data=v\>0.5?3:10* |
| :---- |

*(Command 6.1.1)*

But what if we instead wanted a pattern that was more like the Voronoi cell patterns that you may have come across before?

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_goal2.png)

*If you have access to Arceon then you could use the inbuilt **\#vor\[\]\[\]** pattern.*

### *Method* {#method}

The problem we have with using the inbuilt Voronoi function is that it effectively merges cells together, making the edge hard to find.  
A method for approximating this edge was given some time ago by MelonBP by taking two iterations of the same Voronoi function, with 1 offset by some value on its coordinates, and then subtracting them from each other (returning the absolute value).

We can take this approach and expand upon it to get the edges as defined as we need.

### *Step-by-step* {#step-by-step}

First let’s implement MelonBP’s method. We take our two Voronoi functions below:

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_step1.png)

| *//gen \-r white v1=voronoi(123,x,y,z,0.03);v1\>0.5* |
| :---- |

*(Command 6.1.2)*

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_step2.png)

| *//gen \-r white v2=voronoi(123,x+1,y+1,z+1,0.03);v2\>0.5* |
| :---- |

*(Command 6.1.3)*

And we can then subtract one from the other to start to see the edges:

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_step3.png)

| *//gen \-r white v1=voronoi(123,x,y,z,0.03); v2=voronoi(123,x+1,y+1,z+1,0.03);v1-v2* |
| :---- |

*(Command 6.1.4)*

Applying the **abs()** function to show the negative values too:  

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_step4.png)

| *//gen \-r white v1=voronoi(123,x,y,z,0.03); v2=voronoi(123,x+1,y+1,z+1,0.03);abs(v1-v2)* |
| :---- |

*(Command 6.1.5)*

This expression is a little hard to read and manipulate, so we can add in some variables to allow us to easily change those parameters:

| *//gen \-r white s=123;f=0.03;o=1; v1=voronoi(s,x,y,z,f);v2=voronoi(s,x+o,y+o,z+o,f);abs(v1-v2)* |
| :---- |

*(Command 6.1.6)*

So we can now easily modify that “**o**” offset variable to manipulate the thickness. For example, increasing it from 1 to 2:

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_step5.png)

For general texturing this is probably good enough, but if we want to achieve a cleaner result we will likely need more iterations of the function.

One way to do this would be to take your core Voronoi function and subtract from it an iteration with the X-Axis offset, one with the Y-Axis offset, one with the Z-axis offset, and finally one run with all coordinates offset. Since we would be subtracting 4 variations from the original run, we should also multiply that by 4\.

| *//gen \-r white  s=123;f=0.03;o=1; core=voronoi(s,x,y,z,f); xOff=voronoi(s,x+o,y,z,f); zOff=voronoi(s,x,y,z+o,f); yOff=voronoi(s,x,y+o,z,f); coreOff=voronoi(s,x+o,y+o,z+o,f); abs(4\*core-xOff-yOff-zOff-coreOff)* |
| :---- |

*(Command 6.1.7)*

This will run relatively slowly due to the number of functions it runs per block, but the results are quite clean:  

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_step6.png)

This pattern is optimized for 3D so let’s see how it looks:

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_3d.png)

In these implementations you will find little to no gaps, but it does take quite a long time to run so the results may not always be worthwhile.

If we only need a flat pattern, we can remove the Y offsets from the command:

| *//gen \-r white  s=123;f=0.03;o=1; core=voronoi(s,x,y,z,f); xOff=voronoi(s,x+o,y,z,f); zOff=voronoi(s,x,y,z+o,f); coreOff=voronoi(s,x+o,y,z+o,f); abs(3\*core-xOff-zOff-coreOff)* |
| :---- |

*(Command 6.1.8)*  
Going back to the simpler, quicker method by MelonBP, we can take this and use it as a mask to assist in texturing:  

![](../.gitbook/assets/applied\_examples/voronoi/voronoi\_terrain.png)

| *//replace \[=s=123;f=0.03;o=1; v1=voronoi(s,x,y,z,f);v2=voronoi(s,x+o,y+o,z+o,f);abs(v1-v2)\] &\[grass\_block\] mossy\_cobblestone* |
| :---- |

*(Command 6.1.9)*

In the above example we use the expression mask **\[=...\]** combined with a mask for grass **&\[grass\_block\]** to add in strands of mossy cobblestone to our terrain.