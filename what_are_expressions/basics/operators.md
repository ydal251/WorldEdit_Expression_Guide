### *Logical Operators (Multiple Conditions)* {#logical-operators-(multiple-conditions)}

There are two important Logical Operators that we can use to either check where two conditions return true, or to check where either condition returns true. These are logical AND (**&&**) as well as logical OR (**||**).  
Expanding upon our previous example, if we want to prevent the stone from being placed above the 16th layer, we can add an extra condition.

![](../../.gitbook/assets/what\_are\_expressions/operators\_operators.gif)

| *//replace \[=y\>=65+8&\&y\<65+16\] stone* |
| :---- |

*(Command 1.4.1)*

Here we have taken two conditions, the first where we evaluate for *y\>=65+8* and the second where we evaluate for  *y\<65+16*. For each block in our selection, this expression will return **true** if both conditions are true, and **false** if either is not true, so the Y-level must be at or above **73** and less than **81**.

As your expressions get longer, you may find them harder to read. To help with this I strongly recommend breaking up the command into sections with parentheses. For the above command (*Command 1.4.1*) we are looking for two conditions so it reads well to have them visually separated using these brackets[^4].

| *//replace \[=(y\>=65+8)&&(y\<65+16)\] stone* |
| :---- |

*(Command 1.4.2)*

[^4]: Do note that brackets also control order of operation for mathematical equations. So 1+1*2 equals 3, but (1+1)*2 equals 4 as you calculate the part in brackets first.