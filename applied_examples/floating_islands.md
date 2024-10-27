## **Floating Islands** {#floating-islands}

### *Goal* {#goal-1}

If we wanted to generate a large amount of floating islands, perhaps to build on, then the noise functions are perfect for saving us the time it would take to terraform them manually with WorldEdit/Voxelsniper etc.

So let’s make some cool floating islands\!

### *Method* {#method-1}

Quite simply, we will take some noise functions and combine them to make terrain that looks how we would like it to.

We will need to restrict the generation of this terrain to be in the sky, which we can do by manipulating the threshold to favor terrain in the middle of the world height.

### *Step-by-step* {#step-by-step-1}

Without belaboring each function too much we can use a mixture of perlin() and ridgedmulti() functions to make some interesting terrain. As with the Voronoi pattern, we will use variables to make modifying the results easier.

If we start with just multiplying our noise functions together and comparing them against a set threshold at all points we get:  

![](../.gitbook/assets/applied\_examples/floating_islands/floating\_step1.png)

| *//gen \-r white s=123;f=0.035;m=3;p=0.3; p1=perlin(s,x/m,y,z/m,f,8,p); p2=perlin(s,x/m,y/2,z/m,f,8,p); rm=ridgedmulti(s,x/m,y,z/m,1.5\*f,2); th=0.5; p1\*p2\*rm\>th* |
| :---- |

*(Command 6.2.1)*

In the above example we could easily modify our seed, frequency, scale, and persistence values right at the start and end up with a vastly different output.

Aside from being a bit flat, this already gives us some interesting terrain that we could work with.

However, let’s instead increase the noise density (reduce the threshold) in the middle of the world height and have it reduce from there both up and down.

![](../.gitbook/assets/applied\_examples/floating_islands/floating\_step2.png)

| *//gen \-r white s=123;f=0.035;m=3;p=0.3; p1=perlin(s,x/m,y,z/m,f,8,p); p2=perlin(s,x/m,y/2,z/m,f,8,p); rm=ridgedmulti(s,x/m,y,z/m,1.5\*f,2); y+=64; th=(abs(y-(384/2)))/(384/2); p1\*p2\*rm\>th* |
| :---- |

*(Command 6.2.2)*

Do note that in the above we normalize our Y level to be positive by adding 64, this is just because dealing with positive numbers can be easier.

We get our distance from the middle Y-level by taking the absolute value of **y** minus half of the world height. We can then divide that by half of the world height to get a threshold from 0 to 1 in both directions.

Lastly, to tweak the terrain appearance we can add or subtract from the noise values we have, and to add some gaps to the central terrain we can increase the threshold in the middle by adding to the Y value there.

![](../.gitbook/assets/applied\_examples/floating_islands/floating\_step3.png)

| *//gen \-r white f=0.035;m=3;p=0.3; p1=perlin(123,x/m,y,z/m,f,8,p)\-0.3; p2=perlin(123,x/m,y/2,z/m,f,8,p); rm=ridgedmulti(123,x/m,y,z/m,1.5\*f,2)\+1; y+=64; th=(abs(y-(384/2))\+32)/(384/2); p1\*p2\*rm\>th* |
| :---- |

*(Command 6.2.3)*

With that as our base shape we can do all the texturing we want to make some cool terrain with only a few minutes of effort:

![](../.gitbook/assets/applied\_examples/floating_islands/floating\_textured.png)

Now of course, if you spend more time on it you create some truly epic terrain to go in and add features and structures to.