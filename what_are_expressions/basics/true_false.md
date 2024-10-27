### *True & False* {#true-&-false}

A mask defines which blocks should be affected by a given command. Some blocks are part of the mask and the rest are not. This is exactly what we are doing when we’re providing an expression mask.  
The expression will return whatever it has calculated by the end point and if it returns **True** then the block passes the check, is considered part of the mask, and will be modified by the rest of the command, if **False** then it will not.

![](../../.gitbook/assets/what\_are\_expressions/basics\_true.gif)

| *//replace \[=1\] green* |
| :---- |

*(Command 1.1.1)*

![](../../.gitbook/assets/what\_are\_expressions/basics\_false.gif)

| *//replace \[=0\] yellow* |
| :---- |

*(Command 1.1.2)*

In these examples we have given just a single number **‘1’** or **‘0’** for the expression to return. These are synonymous with **True** or **False** respectively.

Because (*Command 1.1.1)* returns **1**/**True** then every block in our selection passes the mask and will be replaced with green.

However, in (*Command 1.1.2)* we are returning **0**/**False** for every block, meaning they do not pass the mask check and will not be modified.

You can think of this like a standard replace command where you want to replace one block type with another.

| *//replace stone air* |
| :---- |

*(Command 1.1.3)*

This command replaces any stone blocks with air. So where the block is stone that’s the equivalent of **True** and **False** for any other block.