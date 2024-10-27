## **Shaped Terrain** {#shaped-terrain}

### *Understanding* {#understanding}

Before we go into the actual example let’s experiment with, expand on, and fully understand what we came up with in [Bounded Terrain](bounded_terrain.md).

In *(Command 6.3.3)* we used the expression *max(abs(x),abs(y),abs(z))* as a threshold for noise terrain. Now, there is nothing stopping us from putting *any* expression we want in there. Let’s revisit the three [Example Expressions](../generate/normalized.md) from the generate section and just observe what happens if we put them as the threshold.

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding1.png)

| *//g 95:3 thresh=(x+y+z)/23+0.5; perlin(1,x,y\*3,z,2,1,1)\>thresh* |
| :---- |

*(Command 6.4.1)*

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding2.png)

| *//g light\_blue thresh=x\*x+z\*z; perlin(1,x,y\*3,z,2,1,1)\>thresh*  |
| :---- |

*(Command 6.4.2)*

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding3.png)

| *//g light\_blue thresh=abs(x)+abs(y)+abs(z)-1; perlin(1,x,y\*3,z,2,1,1)\>thresh*  |
| :---- |

*(Command 6.4.3)*  
The noise terrain takes the shape of the expressions\! Isn’t that cool? Let’s try to understand what exactly is going on in detail by using a simpler expression for the threshold, *(y+1)/2*, and display the value our noise functions returns through the data output *data=perl\*6.99*.

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding4.png) ![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding5.png)

| *//g light\_blue thresh=(y+1)/2; perl=perlin(1,x,y\*3,z,2,1,1); data=perl\*6.99; perl\>thresh* |
| :---- |

*(Command 6.4.4)*

On the left is the output of *(Command 6.4.4),* the right is the same but every block is placed.   
*Do you see how one could get from the right image to the left image?*

Our noise functions return values between 0 and 1\. The threshold *(y+1)/2* is 0 at the bottom of the selection and 1 and the top. Thus, the higher we are within the selection the “stricter” our threshold becomes. At the top, we only see red blocks. This is where the noise function returned values close to 1\. The lower we go the more “layers” of the noise function are allowed through. See how in the left image, the lower we go the more layers/colors are introduced?



To phrase it more generally:  
As our threshold becomes smaller we get more. As our threshold becomes larger we get less.  
And this can happen gradually, across every direction, and at any rate.

*This* is how all of these commands can create such transitions between air and terrain.

*Scroll up again and try to visualize this effect in your head for the three previous examples\! This is an important page to understand to be able to get the rest of the examples\!*  
Let us take a look at one more expression for our threshold. The expression *x\*x+y\*y+z\*z* represents euclidean distance (squared) which when visualized like in *(Command 6.3.4)* turns out to be just spheres.

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding\_ball1.png)

| *//g 35 data=(x\*x+y\*y+z\*z)\*14.99; (x\*x+y\*y+z\*z)\<1*  |
| :---- |

*(Command 6.4.5)*

Thus, using it as the threshold will result in our terrain being concentrated in the center of our selection like a sphere.  

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding\_ball2.png)

| *//g light\_blue thresh=(x\*x+y\*y+z\*z); perlin(1,x,y,z,6,1,1)\>thresh*  |
| :---- |

*(Command 6.4.6)*

Now, what if we find the result too broken up? What if we want it to be even closer to a perfect sphere? What we would need is a way to make the threshold expression “transition” to 1 later and faster. Something like this  

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding\_graph.png)

This way, the transition between air and terrain will be squished into the outer parts of the sphere.  
The function in the diagram is x8. This is what happens when we apply it to our threshold expression:

| (x\*x+y\*y+z\*z)^0.5 | (x\*x+y\*y+z\*z)^2 | (x\*x+y\*y+z\*z)^8 |
| :---: | :---: | :---: |
| ![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding\_exponent1.png) | ![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding\_exponent2.png) | ![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_understanding\_exponent3.png) |

   
As you can see, we can use powers to control the “strength” of our thresholds and therefore how strongly the terrain adheres to the threshold's shape.  
Keep in mind though that you can, yet again, put in *any* function you want. In this case, it was x8, but it also could’ve been like 1-cos(πx)2 or whatever.

Finally, using what we’ve learned, let’s create an actual epic piece of terrain.

### *Goal* {#goal-3}

Generate floating rocks in the formation of a torus.  

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_goal.png)

### *Method* {#method-3}

First, we’ll combine noise functions to create a neat baseline for our terrain. Secondly, we’ll conveniently happen to know the formula for a torus. And finally, we’ll combine these to make our noise take the shape of a torus, even if only roughly.

### *Step-by-Step* {#step-by-step-3}

First, the baseline noise function. There is no real technical know-how of doing this. It’s mostly trial-and-error until something looks nice. It’s really just throwing random mathematical operations onto noise functions or not. Go wild\!  
For this example I found myself coming back to taking a weighted average of three noise functions:

* perlin(1, x, 2\*y, z, 2, 2, 2);  
* 1-ridgedmulti(1, x, y, z, 2, 2);  
* voronoi(1, x, y, z, 3);

Like this:

| *//g 35 perl \= perlin(1,x,2\*y,z,2,2,2);  rm \= 1-ridgedmulti(1,x,y,z,2,2);  vor \= voronoi(1,x,y,z,3);  noise \= (1\*perl \+ 2\*rm \+ 2\*vor) / 5;  data \= noise\*15.99; true*  |
| :---- |

*(Command 6.4.7)*

*noise \= (1\*perl \+ 2\*rm \+ 2\*vor) / 5;* is where I take the weighted average.

This combination of noise functions, displayed in black & white[^13], looks like this:  

[^13]: With the palette from the generate chapter.

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_cube1.png)

This is how it would look like with a simple constant threshold *noise\>0.5*:

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_cube2.png)

Now that we’ve got that, let’s continue with the torus. To spare us all the mathematics we’re just gonna tell you that the formula for a torus is

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_torus1.png)

| *//g 35 torus=((0.7-sqrt(x\*x+y\*y))^2+z\*z)/0.2^2; torus\<1* |
| :---- |

*(Command 6.4.8)*

Whereby here 0.7 is the major radius and 0.2 the minor radius of the torus.

What’s important about this formula is that it’ll return 0 for the inner parts of the torus and increase to and past 1 as move further out and away from the torus. This is where our threshold gradient will come from: Inner parts will have a low threshold while the outer parts a large one. 

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_torus2.png)

Simply using this as the threshold (*noise \> torus* instead of *noise \> 0.5*) results in:

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_torus3.png)

| *//g 35  perl \= perlin(1,x,2\*y,z,2,2,2);  rm \= 1-ridgedmulti(1,x,y,z,2,2);  vor \= voronoi(1,x,y,z,3);  noise \= (perl+2\*rm+2\*vor)/5;  torus \= ((0.7-sqrt(x\*x+y\*y))^2+z\*z)/0.2^2;  noise \> torus;* |
| :---- |

*(Command 6.4.9)*

Alright\! This already looks somewhat nice. However, it is not really what we want yet. The shape is dominated by the torus a bit too much right now. Remember the example of taking the threshold to the eighth power to make the noise more like a perfect sphere? We can do the opposite too by taking the threshold to the power of some value smaller than 1, like: *torus^0.2*. This alone, however, will thin out our shape drastically so we need to counteract that by increasing the torus thickness from *0.2* to e.g. *0.4*.   

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_torus4.png)

| *//g 35  perl \= perlin(1,x,2\*y,z,2,2,2);  rm \= 1-ridgedmulti(1,x,y,z,2,2);  vor \= voronoi(1,x,y,z,3);  noise \= (perl+2\*rm+2\*vor)/5;  torus \= ((0.7-sqrt(x\*x+y\*y))^2+z\*z)/0.4^2;  noise\>torus^0.2;* |
| :---- |

*(Command 6.4.10)*

While taking our threshold to the power of a certain value is helpful, you can do all kinds of operations, really, but we’ll leave it at that for now.

This is what x0.2 looks like by the way:

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_graph.png)

One last thing we can do now is coloring. Because we used variables throughout this whole command, we can easily make a color pass using them. As mentioned before, things like this have no real science to them. The following expression for example is the result of throwing whatever I have into it and just trial-and-error in general.

|  *color \= ((1-torus) \+ perl \+ rm \+ 2\*vor) / 5;*  |
| :---- |

Finally, using this color palette for the coloring  

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_palette.png)

and putting some crimson roots across flat areas afterward leaves us with:

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_textured1.png)

| *//g 35 perl \= perlin(1,x,2\*y,z,2,2,2);  rm \= 1-ridgedmulti(1,x,y,z,2,2);  vor \= voronoi(1,x,y,z,3);  noise \= (perl+2\*rm+2\*vor)/5;  torus \= ((0.7-sqrt(x\*x+y\*y))^2+z\*z)/0.4^2; color \= ((1-torus)+perl+rm+2\*vor)/5;  data \= color\*15.99;  noise \> torus^0.2* |
| :---- |

*(Command 6.4.11)*

Here's another example for a different set of parameters and a different threshold output function, but the same command:  

![](../.gitbook/assets/applied\_examples/shaped\_terrain/shaped\_textured2.png)

| *//g 35 perl \= perlin(2,x,y,z,1,2,1); rm \= 1-ridgedmulti(7,x,y,z,3,1); vor \= voronoi(6,x,y,z,4); noise \= (perl+rm+vor)/3;  color \= (perl+2\*rm+2\*vor)/5; torus \= ((0.7-sqrt(x\*x+y\*y))^2+z\*z)/0.4^2;  thresh \= 1-(torus^(-0.29)\*0.1);  data=color\*15.99; noise\>thresh* |
| :---- |

*(Command 6.4.12)*