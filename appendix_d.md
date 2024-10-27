# Appendix D \- Expression Operators & Functions Key {#appendix-d---expression-operators-functions-key}

## **Operators** {#operators}

|  | Operator | Description | Example |
| :---: | :---: | ----- | ----- |
|  |  |  |  |
| Comparators[^18] | **\==** | Equals \- Return true when the two values are equal | [Command 1.3.1](what_are_expressions/basics/expanding.md) |
| Comparators | **\!=** | Not equal \- Return true when the two values are not equal |  |
| Comparators | **\~=** | Near \- Returns true when the values are nearly equal |  |
| Comparators | **\>** | Greater than \- Return true when greater than a value (**x\>10** returns true where **x** is above 10, false when 10 or below) | [Command 1.3.2, 1.3.3](what_are_expressions/basics/expanding.md)  |
| Comparators | **\>=** | Greater or equal \- Return true when greater than or equal to a value (**x\>=10** returns true where **x** is 10 or above, false when below 10\) |  |
| Comparators | **\<** | Less than- Return true when less than a value (**x\<10** returns true where **x** is below 10, false when 10 or above) |  |
| Comparators | **\<=** | Less or equal \- Return true when less than or equal to a value (**x\<=10** returns true when **x** is 10 or lower, false when above 10\) |  |
|  |  |  |  |
| Arithmetic[^19] | **\+** | Addition \- Add the given value (**x+3**) | [//calc](what_are_expressions/basics.md)|
| Arithmetic | **\-** | Subtraction \- Subtract the given value (**x-3**) |  |
| Arithmetic | **\*** | Multiplication \- Multiple by a given value (**x\*3**) |  |
| Arithmetic | **/** | Division \- Divide by a given value (**x/3**) |  |
| Arithmetic | **^** | Power \- Raise the value to a given power (**x^2**) |  |
| Arithmetic | **%** | Modulo \- Return the remainder when dividing a value by the given modulus (**10%3** returns 1\) | [Command 1.3.5](what_are_expressions/basics/expanding.md)|
|  |  |  |  |
| Logic[^20] | **&&** | Logical AND \- Return true when both expressions are true  ( **(x\<16) && (x%2==0)** ) | [Command 1.4.1, 1.4.2](what_are_expressions/basics/operators.md)|
| Logic | **\|\|** | Logical OR \- Return true when either expression is true  ( **(x==0) \|\| (x\>16)** ) |  |
|  |  |  |  |
| Assignment[^21] | **\=** | Assign \- Simply assign the value on the right to the variable on the left (**x=6**) | [Command 1.5.1](what_are_expressions/basics/variables.md) |
| Assignment | **\+=** | Add & Assign \- **x+=5** is short for **x=x+5** |  |
| Assignment | **\-=** | Subtract & Assign \- **x-=10** is short for **x=x-10** |  |
| Assignment | **\*=** | Multiple & Assign \- **x\*=2** is short for **x=x\*2** |  |
| Assignment | **/=** | Divide & Assign \- **x/=4** is short for **x=x/4** |  |
| Assignment | **%=** | Modulo & Assign \- **x%=3** is short for **x=x%3** |  |
| Assignment | **^=** | Power & Assign \- **x^=2** is short for **x=x^2** |  |
|  |  |  |  |
| Bitwise[^22] | **\<\<** | Left-shift \- Shift bits to the left (**8\<\<2** returns 32\. Shortened to 8-bits, 8 in binary is 0000 1000\. Shifted 2 to the left gives 0010 0000, which is 32\) |  |
| Bitwise | **\>\>** | Right-shift \- Shift bits to the right (**8\>\>2** returns 22\. Shortened to 8-bits, 8 in binary is 0000 1000\. Shifted 2 to the right gives 0000 0010, which is 2\) |  |
|  |  |  |  |
| Prefix[^23] | **\-x** | Negate \- Inverts the value of **x**, short for **x\*-1** |  |
| Prefix | **\~x** | Bitwise complement \- Inverts the bits of the value (**\~1** returns **\-2**. This is because 1 is 0000 … 0001 in binary, and when flipped returns the signed value 1111 … 1110\) |  |
| Prefix | **\!x** | Logical complement \- Returns true when the value is false, or false when the value is true (**\!0** returns **1 (True)**, **\!1** returns **0 (False)**) |  |
| Prefix | **\++x** | Pre-increment \- Increments the value before assigning it to a variable (**x=++i** where **i=0** increments **i** by **1** and sets **x** to equal **i**, in this case **1**) |  |
| Prefix | **\--x** | Pre-decrement \- Decrements the value before assigning it to a variable (**x=--i** where **i=0** decrements **i** by **1** and sets **x** to equal **i**, in this case \-**1**)  |  |
|  |  |  |  |
| Postfix[^24] | **x\!** | Factorial \- Multiplies the value by all integers lower than in (**4\!** is equal to **4x3x2x1** which is **24**) |  |
| Postfix | **x++** | Post-increment \- Increments the value after assigning it to a variable (**x=++i** where **i=0** sets **x** to equal **i**, in this case still  **0** and increments **i** by **1**, thus setting **i** to **1**) |  |
| Postfix | **x--** | Post-decrement \- Decrements the value after assigning it to a variable (**x=--i** where **i=0** sets **x** to equal **i**, in this case still  **0** and increments **i** by **1**, thus setting **i** to **\-1**) |  |
|  |  |  |  |
| Ternary Infix[^25] | **(a) ? x : y** | Ternary Infix \- Checks if the output of the condition **(a)** is **True**, if so it will return **x**, otherwise it returns **y**. Same as an **if/else** statement, but **x** and **y** can only be single expressions. ( **val=(1\>0)?2:4** will set **val** to equal **2** as the condition **(1\>0)** returns True, 1 is indeed greater than 0\. **val=(1\<0)?-1:2^2** will set **val** to equal **4** as the condition **(1\<0)** returns False, 1 is not less than 0\. In this case we set **val** to the expression **2^2** which is **4** ) | [Command 6.1.1](applied_examples/voronoi.md#goal) |

[^18]: These operators compare their operands and return 1 for true and 0 for false
[^19]: Various binary arithmetic operators for all decimal and integer numbers
[^20]: These operators return true or false depending on two expressions
[^21]: These operators take a variable on the left and assign a value to them
[^22]: These operators take a value and treat them as 64-bit signed integers
[^23]: These operators come before the value/variable they will apply to (x used as example)
[^24]: These operators come after the value/variable they will apply to (x used as example)
[^25]: This operator returns one of two values based on results a condition

## **Functions** {#functions-1}

|  | Function | Description | Example |
| :---: | :---: | ----- | ----- |
|  |  |  |  |
| Math[^26] | **abs(a)** | Returns the absolute value of a number.**abs(-1)** returns **1** | [Command 1.3.5](what_are_expressions/basics/expanding.md) |
| Math | **acos(a)** | Returns the arc cosine of a value; the returned angle is in the range 0.0 through pi. Value must be between \-1 and 1\.**acos(-1)** returns **piacos(0)** returns **pi/2acos(1)** returns **0** |  |
| Math | **asin(a)** | Returns the arc sine of a value; the returned angle is in the range \-pi/2 through pi/2. Value must be between \-1 and 1\.**asin(-1)** returns \-**pi/2asin(0)** returns **0asin(1)** returns **pi/2** |  |
| Math | **atan2(x,y)** | Returns the angle theta from the conversion of rectangular coordinates (x, y) to polar coordinates (r, theta). | [Polar Coordinates](appendix_a.md#appendix-a-polar-coordinates-1) |
| Math | **atan(a)** | Returns the arc tangent of a value; the returned angle is in the range \-pi/2 through pi/2. |  |
| Math | **cbrt(a)** | Returns the cube root of a value. |  |
| Math | **ceil(a)** | Returns the smallest (closest to negative infinity) value that is greater than or equal to the argument and is equal to a mathematical integer. |  |
| Math | **cos(a)** | Returns the trigonometric cosine of an angle. | [Cylinder Distorted](appendix_a.md#appendix-a-cylinder-distorted-3) |
| Math | **cosh(a)** | Returns the hyperbolic cosine of a value. |  |
| Math | **exp(a)** | Returns Euler’s number e raised to the power of a value. |  |
| Math | **floor(a)** | Returns the largest (closest to positive infinity) value that is less than or equal to the argument and is equal to a mathematical integer. | [Polar Coordinates](appendix_a.md#appendix-a-polar-coordinates-2) |
| Math | **ln(a)** | Returns the natural logarithm (base e) of a value. | [Galaxy Spiral](appendix_a.md#appendix-a-galaxy) |
| Math | **log(a)** | Returns the natural logarithm (base e) of a value. |  |
| Math | **log10(a)** | Returns the base 10 logarithm (base e) of a value. |  |
| Math | **max(a,b,c)** | Returns the greatest of the values. (supports 2 and 3 arguments) | [Noise Function](appendix_a.md#appendix-a-noise-polar-coordinates) |
| Math | **min(a,b,c)** | Returns the smallest of the values. (supports 2 and 3 arguments) | [Alien Spire Terrain](appendix_a.md#appendix-a-alien-spire-terrain) |
| Math | **rint(a)** | Returns the number that is closest in value to the argument and is equal to a mathematical integer. |  |
| Math | **round(a)** | Returns the closest number to the argument |  |
| Math | **sin(a)** | Returns the trigonometric sine of an angle. | [Sine Wave](appendix_a.md#appendix-a-sine-1) |
| Math | **sinh(a)** | Returns the hyperbolic sine of a value. |  |
| Math | **sqrt(a)** | Returns the correctly rounded positive square root of a value. | [Displaying r Through Height](appendix_a.md#appendix-a-r-height) |
| Math | **tan(a)** | Returns the trigonometric tangent of an angle. |  |
| Math | **tanh(a)** | Returns the hyperbolic tangent of a value. |  |
|  |  |  |  |
|  Additional[^27]  | **rotate(x, y, angle)** | Rotates the given coordinate pair by the given angle, in radians. To use degrees instead of radians simply multiply the angle in degrees by **(pi/180)** | [Cylinder Rotated](appendix_a.md#appendix-a-cylinder-rotate) |
| Additional | **swap(x, y)** | Swaps the contents of the 2 given variables. Given **x=1** and **y=0**, then **swap(x,y)** sets **x** to **0** and **y** to **1** |  |
| Additional | **random()** | Returns a random number between 0 and 1.0 | [Command 2.1.3](generate/normalized.md) |
| Additional | **randint(max)** | Returns a random integer between 0 and **max**.Value input must be an integer \>0 | [Spiral Generation Brush](appendix_a.md#appendix-a-spiral-brush) |
| Additional | **perlin(seed, x, y, z, frequency, octaves, persistence)** | Generates perlin noise with the given parameters. Returns a value between 0.0 and 1.0 based on input values. | [Functions](/using_noise_functions/functions.md) |
| Additional | **voronoi(seed, x, y, z, frequency)** | Generates voronoi noise with the given parameters. Returns a value between 0.0 and 1.0 based on input values. | [Functions](using_noise_functions/functions.md) |
| Additional | **ridgedmulti(seed, x, y, z, frequency, octaves)** | Generated ridged multi fractal noise with the given parameters. Returns a value between 0.0 and 1.0 based on input values. | [Functions](/using_noise_functions/functions.md) |
|  |  |  |  |
| :---: | :---: | :---- | :---- |
| Block Query[^28] | **query(x, y, z, type, data)** | Returns true if the block at the given coordinates has the given legacy id and data value. If type or data are variables, the id and data of the block will be assigned to that variable. |  |
| Block Query | **queryRel(dx, dy, dz, type, data)** | Like query, except with an offset from the currently evaluated block coordinates. |  |
| Block Query | **queryAbs(xp, yp, zp, type, data)** | Like query, except with absolute world coordinates. | [Command 2.3.4](generate/palette.md) |
|  |  |  |  |
| Buffer[^29] | **(g)megabuf(index)** | Returns the value of the buffer at the given index. | [Megabuf](what_are_expressions/advanced.md#megabuf) |
| Buffer | **(g)megabuf(index, value)** | Sets the value of the buffer at the given index. |  |
| Buffer | **(g)closest(x, y, z, index, count, stride)** | Finds the index of the closest set of x,y,z values (as in, three consecutive buffer values) to the given x,y,z values within count iterations and stride space between each iteration, starting at the given index value. |  |

[^26]: These functions perform some mathematical operation on the given value(s)
[^27]: These functions perform a special operation
[^28]: These functions can be used to query the values of another block
[^29]: These functions provide access to local and global buffers to store values
