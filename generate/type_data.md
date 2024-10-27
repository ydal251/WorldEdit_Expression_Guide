### *Type and Data Output* {#type-and-data-output}

While previously we only returned true or false to indicate *whether* a block should be placed or not, //generate has two more optional outputs: type and data. These two values specify *which* block to place. Now you might say that that’s the same thing as the pattern argument of the command. But remember, the expression is evaluated for each block separately. So we can make expressions that choose the pattern on a per-block basis.

If you are familiar with [Legacy Block Ids](https://minecraft.fandom.com/wiki/Java_Edition_data_values/Pre-flattening) you know that all blocks from 1.12 and before are assigned a unique number (type) and possible different states of that block as well (data). Looking at [this sheet](https://static.wikia.nocookie.net/minecraft_gamepedia/images/8/8c/DataValuesBeta.png/revision/latest?cb=20190723062041) we can for example see that Magenta Stained Glass has type=95 and data=2. That means if we set the type and data variables accordingly we generate Magenta Stained Glass[^7].

![](../.gitbook/assets/generate/type\_stone.gif)

| *//generate stone type=95;data=2;true* |
| :---- |

*(Command 2.3.1)*

Note that because we set the two variables, we overwrite the provided stone pattern.

Now because these are just variables, we can assign *any* expression we want to them, finally being able to choose which pattern to use on a per-block basis.

![](../.gitbook/assets/generate/type\_generate.gif)

| *//generate 251 x=(x+1)/2;data=x\*15;true* |
| :---- |

*(Command 2.3.2)*

Here we use concrete (251) as our pattern. The color variations are accessed with the data variable. White is 0, orange is 1, and so on. We suggest you open the [block ids sheet](https://static.wikia.nocookie.net/minecraft_gamepedia/images/8/8c/DataValuesBeta.png/revision/latest?cb=20190723062041).

First, let’s observe a few quirks. If we only do *data=x;true* there was a slice of Black Glazed Terracotta on the right. This happened because at that slice x equaled \-1 and so WorldEdit interpreted *data=-1* as using type=250 instead. Note, the reason why we only had *one* slice, is because the type and data variables are always rounded down before they are used to choose the block. So data=3.75 is the same as data=3. That’s also why we only saw one slice of orange concrete too.

Now let’s think about why we need to do *x=(x+1)/2* and *x\*15*. We know that with //g, x will be between or equal to \-1 and 1\. But if we want to display all colors of concrete, we need to set data in a range of 0 to 15\. We can achieve this by mapping \[-1,1\] to \[0,1\] with *(x+1)/2* and then scaling \[0,1\] to \[0,15\] with *x\*15*. 

This way of using the data output to color your generated structure is something you should remember, as it's an easy and flexible way to color. We can actually use this to recreate the [visualizations](#bookmark=id.k2uk9akc8u4s) from before:

| //g 35 data= (x+y+z+3)/6 \*15.99;1 | //g 35 data= (x\*x+z\*z)/2 \*15.99;1 | //g 35 data= (abs(x)+abs(y)+abs(z))/3\*15.99;1 |
| ----- | ----- | ----- |
| ![](../.gitbook/assets/generate/type\_cube1.png) | ![](../.gitbook/assets/generate/type\_cube2.png) | ![](../.gitbook/assets/generate/type\_cube3.png) |

The only differences come from mapping the output values to the range \[0,16) instead of \[-1,1\]. These blocks can now easily be replaced using e.g. //replace commands, to whatever color palette you want.

If you use this palette for example  

![](../.gitbook/assets/generate/type\_cube4.png)

Then after those 16 replace commands, the middle expression will look like this:

Or what’s even more interesting: Displaying the provided noise functions in this way:

![](../.gitbook/assets/generate/type\_cube5.png)

| *//generate 35 data=ridgedmulti(1,x,y,z,1.6,1)\*15.99;1* |
| :---- |

*(Command 2.3.3)*[^8]

[^7]: Unfortunately, we can only assign numbers to these variables, meaning we can not directly generate blocks from newer versions as they do not have an assigned id.
[^8]: Here we also used 9 replace commands after generating.