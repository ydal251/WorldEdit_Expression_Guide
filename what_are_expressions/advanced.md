Now, before going into //generate and noise functions, we want to mention a few additional tools and concepts that we will not cover in detail, but instead, leave them to you to discover on your own. Feel free to [skip](../generate/generate.md) this section for now if you’re a beginner.

## **More Advanced Tools** {#more-advanced-tools}

### *Distorting space* {#distorting-space}

* You can distort space by manipulating the x,y,z variables through for example

| Distortion Type | Equation | Example | 
| :----- | :----: | :----: | 
| Offsetting:  | x+=5; z-=0.5; | [Example](../appendix_a.md#appendix-a-cylinder-offset) |
| Stretching or compressing: | x\*=5; y/=3; | [Example](../appendix_a.md#appendix-a-cylinder-stretched) |
| Rotating: | rotate(x,z,pi/2); | [Example](../appendix_a.md#appendix-a-cylinder-rotated) |
| Custom distortions: | x+=sin(pi\*x); y+=3x; | [Example](../appendix_a.md#appendix-a-cylinder-distorted-2)  |
| Distortions by noise: | z+=voronoi(1,x,y,z,1); | [Example](../appendix_a.md#appendix-a-cylinder-distorted-1)  |

### *Deform Command* {#deform-command}

Its syntax is  
//deform \[-cor\] \<expression...\>  
The expression is executed for each block and is expected to modify the variables x, y and z to point to a new block to fetch. Essentially: x,y,z goes in; x,y,z goes out (while before we only had: x,y,z goes in; true/false goes out). (The \-cor part is explained [later](../generate/all-coordinate.md). You can ignore it for now.)

| *//deform \-r x+=4* |
| :---- |

*(Command 1.6.1)*

This command would for example move your build by 4 blocks along the x-axis.

Think of it this way: When a block positioned at coordinates **10,10,10** will run the expression, whatever values x,y,z are set to after evaluating the expression is where the block should fetch its pattern from. So for the mentioned command, it will become whatever pattern is placed at coordinates **14,10,10**. And the block at **14,10,10** will become whatever pattern was placed **18,10,10** and so on, resulting in moving everything in your selection.

Hence, *(Command 1.6.2)* will fill your selection with whatever block is placed at coordinates **100,100,100**, as every time the expression is evaluated, **x,y,z** are set to **100,100,100**.

| *//deform \-r x=100;y=100;z=100* |
| :---- |

*(Command 1.6.2)*

### *Control Structures and Loops* {#control-structures-and-loops}

Expressions support

* (Do) While Loops  
* For Loops  
* If-else Statements  
* Switch Statements

We won't go into how they work at this time, but there are countless sources on the internet that do, for example [this one](https://www.w3schools.com/java/java_conditions.asp). They are all in the Java language format.

### *Megabuf* {#megabuf}

WorldEdit provides two buffers you can read from and write to any numerical values. One is global, gmegabuf, storing values even after a command finishes running, while the other is local, megabuf, storing values only for the execution of the current command and cleared once a command has finished running.

| These functions provide access to local and global buffers to store values |  |
| ----- | :---- |
| **(g)megabuf(index)** | Returns the value of the buffer at the given index. |
| **(g)megabuf(index, value)** | Sets the value of the buffer at the given index. |

![](../.gitbook/assets/what\_are\_expressions/advanced\_megabuf.gif)

There is also a function that can search the buffers for the closest point stored in them to a given point. See [this example](../appendix_a.md#appendix-a-voronoi) of megabuf() and closest().

| (g)closest(x, y, z, index, count, stride) | Finds the index of the closest set of x,y,z values (as in, three consecutive buffer values) to the given x,y,z values within count iterations and stride space between each iteration, starting at the given index value. |
| :---- | :---- |