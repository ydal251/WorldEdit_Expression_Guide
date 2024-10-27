### *Assigning Variables* {#assigning-variables}

Expressions can get very long. To help with readability, we are able to store and recall values using variables. Variables can be named however you want (there are a few exceptions). Here’s a simple example of assigning (*myVar=65*) and using it as a variable (*y\>=myVar+8*).

![](../../.gitbook/assets/what\_are\_expressions/variables\_short.gif)

| *//replace \[=myVar=65;y\>=myVar+8\] stone* |
| :---- |

*(Command 1.5.1)*

Separate assignments with a semicolon. It’s not unusual to have a sequence of expressions of just assigning variables. Remember that the last value in a sequence is always returned.  
It often helps to give your variables names that describe themselves. Having well-named variables will help everyone else and your future self to read and understand your commands. 

This is especially important for parameters, e.g. [like here](../../appendix_a.md#appendix-a-cylinder-y). Though the importance of using variables and more descriptive names only grows with the complexity and size of the command. 

Here’s a potentially overly excessive example of naming parts of your expression, where we store the true/false output of *(y\>=65+8)* and *(y\<65+16)* in the variables *lower\_bound* and *upper\_bound* respectively and recall them in the final expression *lower\_bound&\&upper\_bound*. Note that we are not changing the behaviour of the command, only how it reads.

![](../../.gitbook/assets/what\_are\_expressions/variables\_long.gif)

| *//replace \[=lower\_bound=(y\>=65+8);upper\_bound=(y\<65+16);lower\_bound&\&upper\_bound\] stone* |
| :---- |

*(Command 1.5.2)*

If you were able to follow and understand the concepts and examples so far, Congrats\! You already understand the basics of using expressions.