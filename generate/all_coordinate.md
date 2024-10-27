### *All Coordinate Systems* {#all-coordinate-systems}

The generate command additionally gives you the options to have other coordinate systems as well.

| //generate \[-cor\] \<pattern\> \<expression...\> |  |
| ----- | :---- |
| No Argument | Normalized coordinates in the range \[-1,1\]. Origin at center of selection. x,y,z will mostly be decimal numbers, not integers. On the right is an image of how you should think about your selection.  ![](../.gitbook/assets/generate/all\_no.png)|
| \-r | Uses the game's coordinate system, just like an expression mask. So no modification to the coordinates. So if your selection would be //pos1 \-12,71,0 and //pos2 \-4,79,8 then x,y,z would be integers like in the example image.  ![](../.gitbook/assets/generate/all\_r.png)|
| \-c | Origin placed at the center of the selection, but no normalization/scaling. The range of values depends on the size of your selection. So if your selection is 9x9x9 large, then x,y,z will be set to (-4,-3,-2,-1,0,1,2,3,4) as shown in the example image. The larger your selection the larger the ranges. Note: if any dimension of your selection is even e.g. 6x6x6, then x,y,z will be set as something like (-2.5, \-1.5, \-0.5, 0.5, 1.5, 2.5) instead of whole integers, but still preserving the 1 unit \= 1 block ratio. ![](../.gitbook/assets/generate/all\_c.png)|
| \-o | Origin placed at the players position, also no normalization/scaling. Essentially the same as \-c but the origin is not the center of the selection but instead the player's position. |

Pay attention to which coordinate system is used in the following examples. Sometimes it is more useful to run //g with normalized coordinates and sometimes with \-c.