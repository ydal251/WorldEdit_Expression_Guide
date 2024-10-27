## **Functions** {#functions}

perlin( [seed](parameters.md#seed) , [x , y , z](parameters.md#coordinates) , [frequency](parameters.md#frequency) , [octaves](parameters.md#octaves-&-persistence) , [persistence](parameters.md#octaves-&-persistence) )

ridgedmulti( [seed](parameters.md#seed) , [x , y , z](parameters.md#coordinates) , [frequency](parameters.md#frequency) , [octaves](parameters.md#octaves-&-persistence) )

voronoi( [seed](parameters.md#seed) , [x , y , z](parameters.md#coordinates) , [frequency](parameters.md#frequency) )

When using any of these functions with some combination of valid inputs, the function will return a value between 0 and 1 for each point that your expression runs on.

We can use this property to determine some kind of [**threshold**](../using_noise_functions/parameters.md#threshold) for our functions to set blocks.
