### *Applying a palette* {#applying-a-palette}

An easy way of mapping a color palette that does not involve running several replace commands, is using the following deform command. It fetches your palette from somewhere in your world.

Just to reiterate, the problem we want to solve is: When running //generate commands that use the data field output, we get a bunch of differently colored wool. What we want to do is replace every piece of wool with *our* choice of block, one block for each color of wool.

![](../.gitbook/assets/generate/palette\_conversion.png)

And so we made a deform command that applies our whole color palette at once.

| *//deform \-r t=0;d=0;queryAbs(x,y,z,t,d);if(t\!=35)return 0;  x=??; y=??; z=??; x+=d* |
| :---- |

*(Command 2.3.4)*

To use it, you just need to:

1. Place your palette of blocks along the x-axis (east to west) in a row.  
2. Find out the coordinates of the first block (the one with the lowest x value).  
3. Put the coordinates into *(Command 2.3.4)* \- *replacing* the question marks (yes, delete them and replace them yourself). Meaning you get something like *//deform \-r t=0;d=0;queryAbs(x,y,z,t,d);if(t\!=35)return 0;  x=369;y=169;z=59; x+=d* but with the coordinates of the palette in *your* world of course. (See pic below for an example)  
4. Now you can select the output of your //generate command containing the colored wool and run the command.

![](../.gitbook/assets/generate/palette\_coords.png)

Here you can see us mapping the color palette from above on the output of the following noise function command *(Command 2.3.5)*.

| ![](../.gitbook/assets/generate/palette\_noise1.png) | ![](../.gitbook/assets/generate/palette\_noise2.png) |
| :---: | :---: |

| *//generate \-c 35 r=ridgedmulti(2,x,y,z,.02,3); data=r\*15.9; 4\*r\<2-y* |
| :---- |

*(Command 2.3.5)*  
*Talking about noise…*
