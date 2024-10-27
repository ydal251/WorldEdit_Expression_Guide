## **Bounded Terrain** {#bounded-terrain}

### *Goal* {#goal-2}

The previous example generated Floating Islands which filled up and went up to the borders of the selection (left screenshot). Let’s say we do not want that. Instead we want an enclosed set of islands restricted by the size of the selection, without any clipping of the terrain (right screenshot).
![](../.gitbook/assets/applied\_examples/bounded\_terrain/bounded\_goal1.png) ![](../.gitbook/assets/applied\_examples/bounded\_terrain/bounded\_goal2.png)
### *Method* {#method-2}

To achieve this we remember that noise functions return values within a range. We can use this to create smooth transitions between filled terrain and air. Recall [Command 5.4.2](../using_noise_functions/parameters.md#threshold) where we made the threshold depend on the current y-level. The higher the y-level, the higher the threshold, the less blocks we let through to generate. But this time we want to have less blocks the closer we are to any border of the selection.  
So we’re gonna create an expression that gets larger the closer we are to the borders of the selection and put *it* as the threshold.

### *Step-by-Step* {#step-by-step-2}

Before we go further let us agree on using normalized coordinates. This will make everything easier. Let’s start with a noise function *perlin(1,x,y\*3,z,2,1,1)* and a constant threshold *\>0.5*.

![](../.gitbook/assets/applied\_examples/bounded\_terrain/bounded\_step1.png)

| *//g light\_blue perlin(1,x,y\*3,z,2,1,1)\>0.5*  |
| :---- |

*(Command 6.3.1)*

The terrain is clipping at the borders. So here’s where we build a dynamic threshold. Blocks close to the center have small coordinate values while blocks near the sides have larger coordinate values. Furthermore, it suffices to have one large component to be close to the borders. So while the block at coordinates (1,1,1) is on the border of our selection, (1,0,0) is on the border of our selection too. So let’s use the maximum of all three x,y,z components, *max(x,y,z)*, to determine the closeness of every block. Also don’t forget that x,y,z can be negative. Meaning we want the maximum of absolute values, *max(abs(x),abs(y),abs(z))*.

![](../.gitbook/assets/applied\_examples/bounded\_terrain/bounded\_cube.png)

| *//g 35 data=max(abs(x),abs(y),abs(z))\*14.99; 1*  |
| :---- |

*(Command 6.3.2)*

If we substitute this expression as the threshold for our noise function, we get:

![](../.gitbook/assets/applied\_examples/bounded\_terrain/bounded\_step2.png)

| *//g light\_blue thresh=max(abs(x),abs(y),abs(z)); perlin(1,x,y\*3,z,2,1,1)\>thresh*  |
| :---- |

*(Command 6.3.3)*

Through making the threshold larger as we get closer to the borders of the selection the terrain successfully “fades out” before reaching it.
