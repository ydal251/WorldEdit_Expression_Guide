# Appendix B \- Noise Function Parameter Gifs {#appendix-b---noise-function-parameter-gifs}

## **Noise Parameters** {#noise-parameters}

### *Seed (SEED,x,y,z,1,1,1)* {#seed-(seed,x,y,z,1,1,1)}

![](.gitbook/assets/appendix\_b/appendixb\_seed.gif)

| *//generate \-c light\_blue  perlin(SEED,x,y,z,0.03,1,0) \> 0.5 //generate \-c magenta    voronoi(SEED,x,y,z,0.03) \> 0.5 //generate \-c yellow ridgedmulti(SEED,x,y,z,0.03,1) \> 0.5* |
| ----- |

### *Frequency (1,x,y,z,FREQ,1,1)* {#frequency-(1,x,y,z,freq,1,1)}

![](.gitbook/assets/appendix\_b/appendixb\_frequency.gif)

| *//generate \-c light\_blue  perlin(1,x,y,z,FREQUENCY,1,0) \> 0.5 //generate \-c magenta    voronoi(1,x,y,z,FREQUENCY) \> 0.5 //generate \-c yellow ridgedmulti(1,x,y,z,FREQUENCY,1) \> 0.5* |
| ----- |

### *Octaves (1,x,y,z,1,OCT,1)* {#octaves-(1,x,y,z,1,oct,1)}

![](.gitbook/assets/appendix\_b/appendixb\_octaves.gif)

| *//generate \-c light\_blue  perlin(1,x,y,z,0.02,OCTAVES,0) \> 0.5 \- //generate \-c yellow ridgedmulti(1,x,y,z,0.02,OCTAVES) \> 0.5* |
| ----- |

### *Persistence  (1,x,y,z,1,1,PERSISTENCE)* {#persistence-(1,x,y,z,1,1,persistence)}

![](.gitbook/assets/appendix\_b/appendixb\_persistance.gif)

| *//generate \-c light\_blue perlin(1,x,y,z,0.02,8,PERSISTENCE) \> 0.5 – \-* |
| ----- |

## **Coordinates** {#coordinates-1}

### *Constant axis (x,0,z)* {#constant-axis-(x,0,z)}

![](.gitbook/assets/appendix\_b/appendixb\_axis.gif)

| *//generate \-c light\_blue  perlin(123,x,y,z,0.03,1,0) \> 0.5 //generate \-c magenta    voronoi(123,x,y,z,0.03) \> 0.5 //generate \-c yellow ridgedmulti(123,x,y,z,0.03,1) \> 0.5* |
| :---- |

### *Offset (x,y+2,z)* {#offset-(x,y+2,z)}

![](.gitbook/assets/appendix\_b/appendixb\_offset.gif)

| *//generate \-c light\_blue  perlin(1,x,y+(...),z,0.03,1,0) \> 0.5 //generate \-c magenta    voronoi(1,x,y+(...),z,0.03) \> 0.5 //generate \-c yellow ridgedmulti(1,x,y+(...),z,0.03,1) \> 0.5* |
| :---- |

### *Stretch (x,y/2,z)* {#stretch-(x,y/2,z)}

![](.gitbook/assets/appendix\_b/appendixb\_stretch.gif)

| *//generate \-c light\_blue  perlin(1,x,y/(...),z,0.03,1,0) \> 0.5 //generate \-c magenta    voronoi(1,x,y/(...),z,0.03) \> 0.5 //generate \-c yellow ridgedmulti(1,x,y/(...),z,0.03,1) \> 0.5* |
| :---- |

### *Compress (x,y\*2,z)* {#compress-(x,y*2,z)}

![](.gitbook/assets/appendix\_b/appendixb\_compress.gif)

| *//generate \-c light\_blue  perlin(1,x,y\*(...),z,0.03,1,0) \> 0.5 //generate \-c magenta    voronoi(1,x,y\*(...),z,0.03) \> 0.5 //generate \-c yellow ridgedmulti(1,x,y\*(...),z,0.03,1) \> 0.5* |
| :---- |

## **Threshold** {#threshold-1}

### *\<* {#<}

![](.gitbook/assets/appendix\_b/appendixb\_less.gif)

| *//generate \-c light\_blue  perlin(1,x,y,z,0.03,1,0) \< THRESHOLD //generate \-c magenta    voronoi(1,x,y,z,0.03) \< THRESHOLD //generate \-c yellow ridgedmulti(1,x,y,z,0.03,1) \< THRESHOLD* |
| :---- |

### *\>* {#>}

![](.gitbook/assets/appendix\_b/appendixb\_greater.gif)

| *//generate \-c light\_blue  perlin(1,x,y,z,0.03,1,0) \> THRESHOLD //generate \-c magenta    voronoi(1,x,y,z,0.03) \> THRESHOLD //generate \-c yellow ridgedmulti(1,x,y,z,0.03,1) \> THRESHOLD* |
| :---- |

### *y-Dependent* {#y-dependent}

![](.gitbook/assets/appendix\_b/appendixb\_ydependent.gif)

| *//generate light\_blue  perlin(1,x,y,z,3,1,0) \> (y+1)\*(...)  //generate magenta    voronoi(1,x,y,z,3) \> (y+1)\*(...) //generate yellow ridgedmulti(1,x,y,z,3,1) \> (y+1)\*(...)* |
| :---- |

### *Heightmap* {#heightmap}

![](.gitbook/assets/appendix\_b/appendixb\_heightmap.gif)

| *//generate light\_blue  perlin(1,x,0,z,3,1,0) \> (y+1)\*(...)  //generate magenta    voronoi(1,x,0,z,3) \> (y+1)\*(...) //generate yellow ridgedmulti(1,x,0,z,3,1) \> (y+1)\*(...)* |
| :---- |

### *Rainbow \>* {#rainbow->}

![](.gitbook/assets/appendix\_b/appendixb\_rainbowgreater.gif)

| *//gen \-c light\_blue\_stained\_glass  perlin(1,x,y,z,0.015,2,0.5) \> THRESHOLD  //gen \-c magenta\_stained\_glass    voronoi(1,x,y,z,0.015) \> THRESHOLD //gen \-c yellow\_stained\_glass ridgedmulti(1,x,y,z,0.015,2) \> THRESHOLD* |
| :---- |

### *Rainbow \<* {#rainbow-<}

![](.gitbook/assets/appendix\_b/appendixb\_rainbowless.gif)

| *//gen \-c light\_blue\_stained\_glass  perlin(1,x,y,z,0.015,2,0.5) \< THRESHOLD  //gen \-c magenta\_stained\_glass    voronoi(1,x,y,z,0.015) \< THRESHOLD //gen \-c yellow\_stained\_glass ridgedmulti(1,x,y,z,0.015,2) \< THRESHOLD* |
| :---- |