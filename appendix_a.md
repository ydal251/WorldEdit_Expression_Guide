# Appendix A \- Collection of Example Commands  {#appendix-a---collection-of-example-commands}

#### *In //generate the variables x,y,z will be in the range \[-1,1\]. You can confirm that with the following command.*  {#appendix-a-generate}

![](.gitbook/assets/appendix\_a/appendixa\_plane1.png)

| *//g stone (y==1) \|\| (y==-1)* |
| :---- |

#### *Plane of blocks whose relative x coordinate equals their relative y coordinate.* {#appendix-a-plane}  


![](.gitbook/assets/appendix\_a/appendixa\_plane2.png)

| *//g 41 x==y* |
| :---- |

#### *Diagonal Plane of blocks whose relative x,y,z coordinates add up to 0[^14] (inaccurate due to rounding errors).* {#appendix-a-diagonal-plane} 
[^14]: Hexagon occurs due to the plane being clipped by a cuboid selection

![](.gitbook/assets/appendix\_a/appendixa\_plane3.png)

| *//g 57 x-y+z==0* |
| :---- |

#### *Allowing tolerance by going from (...)==0 to abs(...)\<0.01.*  {#appendix-a-diagonal-plane-tolerance} 
 
![](.gitbook/assets/appendix\_a/appendixa\_plane4.png)

| *//g 57 abs(x-y+z)\<0.01* |
| :---- |

#### *Octahedron*  {#appendix-a-octahedron}  

![](.gitbook/assets/appendix\_a/appendixa\_octahedron.png)

| *//g cobblestone (abs(x)+abs(y)+abs(z) \<= 1\)* |
| :---- |

#### *Selection Outline*  {#appendix-a-selection-outline}   
If we sum up two coordinate components, only these edges can sum up to 2\.   

![](.gitbook/assets/appendix\_a/appendixa\_outline.png)

| *//g diamond\_block x=abs(x); y=abs(y); z=abs(z); return (x+y==2 \|\| x+z==2 \|\| y+z==2)* |
| :---- |

#### *Cylinder (along y axis) with a variable for the radius.*  {#appendix-a-cylinder-y}  

![](.gitbook/assets/appendix\_a/appendixa\_cyl1.png)

| *//g 95:3 radius=0.5; return (x\*x \+ z\*z \< radius^2)* |
| :---- |

#### *Cylinder (along z axis)*  {#appendix-a-cylinder-z}  

![](.gitbook/assets/appendix\_a/appendixa\_cyl2.png)

| *//g 95:3 radius=0.5; return (x\*x \+ y\*y \< radius^2)* |
| :---- |

#### *Sphere*  {#appendix-a-sphere}   

![](.gitbook/assets/appendix\_a/appendixa\_sphere1.png)

| *//g 95:0 radius=0.75; return (x\*x \+ y\*y \+ z\*z \< radius^2)* |
| :---- |

#### *Sphere with a radius larger than the selection*  {#appendix-a-sphere-clipped}  

![](.gitbook/assets/appendix\_a/appendixa\_sphere2.png)

| *//g 95:0 radius=1.1; return (x\*x \+ y\*y \+ z\*z \< radius^2)* |
| :---- |

#### *Fluffy Ball*  {#appendix-a-fluffy-ball}  

![](.gitbook/assets/appendix\_a/appendixa\_sphere3.png)

| *//g 95:6 radius=0.75; return ((x\*x \+ y\*y \+ z\*z) \+ random()/8 \< radius^2)* |
| :---- |

#### *Torus with major radius 0.7 and minor radius 0.3*  {#appendix-a-torus-1}  

![](.gitbook/assets/appendix\_a/appendixa\_torus1.png)

| *//g 95:0 major\_r=0.7; minor\_r=0.3; (major\_r-sqrt(x\*x+z\*z))^2+y^2 \< minor\_r^2* |
| :---- |

#### *Torus with inner radius 0.1 and outer radius 0.9*  {#appendix-a-torus-2}  

![](.gitbook/assets/appendix\_a/appendixa\_torus2.png)

| *//g 95:0 major\_r=0.9; minor\_r=0.1; (major\_r-sqrt(x\*x+z\*z))^2+y^2 \< minor\_r^2* |
| :---- |

#### *Double Cone*  {#appendix-a-double-cone}  

![](.gitbook/assets/appendix\_a/appendixa\_doublecone.png)

| *//generate light\_blue x\*x+z\*z-y\*y\<0* |
| :---- |

#### *Hollow Rounded Hourglass*  {#appendix-a-hourglass}  

![](.gitbook/assets/appendix\_a/appendixa\_hourglass.png)

| *//generate \-h 95:3 x\*x+z\*z-y\*y \+ abs(y)^20 \< 0.01* |
| :---- |

#### *Single Cone*  {#appendix-a-cone}  

![](.gitbook/assets/appendix\_a/appendixa\_cone1.png)

| *//generate light\_blue x\*x+z\*z-(y/2-.5)^2\<0* |
| :---- |

#### *Upside down cone*  {#appendix-a-inverted-cone}  

![](.gitbook/assets/appendix\_a/appendixa\_cone2.png)

| *//generate light\_blue x\*x+z\*z-(y/2+.5)^2\<0* |
| :---- |

#### *Sine Wave along x axis displayed through height*  {#appendix-a-sine-1}  

![](.gitbook/assets/appendix\_a/appendixa\_sine1.png)

| *//g quartz\_block sin(2\*pi\*x) \> y* |
| :---- |

#### *Sine Wave along both x and z axes displayed through height*  {#appendix-a-sine-2}    

![](.gitbook/assets/appendix\_a/appendixa\_sine2.png)

| *//g quartz\_block sin(2\*pi\*x) \+ sin(2\*pi\*z) \> 2\*y* |
| :---- |

#### *Sine Wave along both x and y axes displayed through z axis*  {#appendix-a-sine-3}   

![](.gitbook/assets/appendix\_a/appendixa\_sine3.png)

| *//g quartz\_block sin(2\*pi\*x) \+ sin(2\*pi\*y) \< 2\*z* |
| :---- |

#### *Sine Wave with a higher frequency and lower amplitude*  {#appendix-a-sine-4}    

![](.gitbook/assets/appendix\_a/appendixa\_sine4.png)

| *//g quartz\_block sin(4\*pi\*x) \+ sin(4\*pi\*y) \< 7\*z* |
| :---- |

#### *Cylinder offset  *  {#appendix-a-cylinder-offset}

![](.gitbook/assets/appendix\_a/appendixa\_cyl3.png)

| *//g 95:2 x+=0.5; r=0.3; return (x\*x+z\*z \< r^2)* |
| :---- |

#### *Cylinder stretched*  {#appendix-a-cylinder-stretched}  

![](.gitbook/assets/appendix\_a/appendixa\_cyl4.png)

| *//g 95:2 x+=0.5; z/=3; r=0.3; return (x\*x+z\*z \< r^2)* |
| :---- |

#### *Cylinder rotated using the rotate() function.*  {#appendix-a-cylinder-rotated}  

![](.gitbook/assets/appendix\_a/appendixa\_cyl5.png)

| *//g 95:2 rotate(x,y,pi/7); rotate(y,z,0.2); r=0.3; return (x\*x+z\*z \< r^2)* |
| :---- |

#### *Cylinder distorted with noise*  {#appendix-a-cylinder-distorted-1}  

![](.gitbook/assets/appendix\_a/appendixa\_cyl6.png)

| *//g 95:2 perl=perlin(1,x,y,z,1,1,1)/3; x+=perl; z+=perl; r=0.3; return (x\*x+z\*z \< r^2)* |
| :---- |

#### *Cylinder distorted on the x axis by a sine wave along the y axis.*  {#appendix-a-cylinder-distorted-2}    

![](.gitbook/assets/appendix\_a/appendixa\_cyl7.png)

| *//g 95:2 x+=sin(2\*pi\*y)/2; r=0.3; return (x\*x+z\*z \< r^2)* |
| :---- |

#### *Cylinder distorted on the z axis by a sine wave along the y axis.*  {#appendix-a-cylinder-distorted-3}    

![](.gitbook/assets/appendix\_a/appendixa\_cyl8.png)

| *//g 95:2 z+=cos(2\*pi\*y)/2; r=0.3; return (x\*x+z\*z \< r^2)* |
| :---- |

#### *Cylinder distorted on both the x and z axes by a sine and cosine waves along the y axis.*  {#appendix-a-cylinder-distorted-4}     

![](.gitbook/assets/appendix\_a/appendixa\_cyl9.png)

| *//g 95:2 x+=sin(2\*pi\*y)/2; z+=cos(2\*pi\*y)/2; r=0.3; return (x\*x+z\*z \< r^2)* |
| :---- |

#### *Previous distorted Cylinder is actually the same as the following rotate call.*  

![](.gitbook/assets/appendix\_a/appendixa\_cyl9.png)

| *//g 95:2 x+=sin(2\*pi\*y)/2; z+=cos(2\*pi\*y)/2; r=0.3; return (x\*x+z\*z \< r^2)* |
| :---- |
 

#### *Polar Coordinates used for the data output field.*  {#appendix-a-polar-coordinates-1}  
//g 251 theta=(atan2(x,z)/2/pi+0.5); data=theta\*15.9; y==0  

![](.gitbook/assets/appendix\_a/appendixa\_polar1.png)

| ** |
| :---- |

#### *Polar Coordinates with alternating function*  {#appendix-a-polar-coordinates-2}   
//g 251 theta=(atan2(x,z)/2/pi+0.5); data=floor(theta\*15.9)%2; y==0  

![](.gitbook/assets/appendix\_a/appendixa\_polar2.png)

| ** |
| :---- |

#### *Displaying r through height*  {#appendix-a-r-height}  
//g 95 r=sqrt(x\*x+z\*z); r\>y+1  

![](.gitbook/assets/appendix\_a/appendixa\_polar3.png)

| ** |
| :---- |

#### *Displaying theta through height*  {#appendix-a-theta-height}   
//g 95 theta=(atan2(x,z)/2/pi+0.5); 2\*theta\>y+1  

![](.gitbook/assets/appendix\_a/appendixa\_polar4.png)

| ** |
| :---- |

#### *Displaying [r=theta](https://www.desmos.com/calculator/psbskzjkki)*  
//g 95 theta=(atan2(x,z)/2/pi+0.5); r=sqrt(x\*x+z\*z); y==0 && abs(r-theta)\<0.02  

![](.gitbook/assets/appendix\_a/appendixa\_polar5.png)

| ** |
| :---- |

#### *Displaying r-theta through height*  
//g 251 theta=(atan2(x,z)/2/pi+0.5); r=sqrt(x\*x+z\*z); 1-abs(r-theta)\>y+1;  

![](.gitbook/assets/appendix\_a/appendixa\_polar6.png)

| ** |
| :---- |

#### *Calling a noise function with polar coordinates*  {#appendix-a-noise-polar-coordinates}   
//g 251 theta=(atan2(x,z)/2/pi+0.5); r=sqrt(x\*x+z\*z); d=max(0,1-r); data=ridgedmulti(2,theta,0,0,5,3)\*d\*15; y==0  

![](.gitbook/assets/appendix\_a/appendixa\_polar7.png)

| ** |
| :---- |

#### *Generate any N-sided polygon. Change "N=5" to the number of sides you want.*  {#appendix-a-polygon}  
//generate red\_wool N=5; a=atan2(x,z); r=(cos(pi/N))/cos(a-((2\*pi)/N)\*floor((N\*a+pi)/(2\*pi))); (x^2+z^2)\<r^2

![](.gitbook/assets/appendix\_a/appendixa\_polygon1.png) ![](.gitbook/assets/appendix\_a/appendixa\_polygon2.png)

| ** |
| :---- |

#### *Using megabuf to create custom Voronoi cell patterns*  {#appendix-a-voronoi}  
Generate points (2D):  
//calc n=96; for(i=0;i\<=n\*3;i+=3){gmegabuf(i+10,1-(2\*random())); gmegabuf(i+11,0); gmegabuf(i+12,1-(2\*random()));}

(Alternatively) Generate points (3D):  
//calc n=96; for(i=0;i\<=n\*3;i+=3){gmegabuf(i+10,1-(2\*random())); gmegabuf(i+11,1-(2\*random())); gmegabuf(i+12,1-(2\*random()));}

Colour the pattern  
//g white\_concrete v=(gclosest(x,y,z,10,96,3)-10)/3+1; data=v%16; switch(floor(v/16)){ case 0: a=0;break; case 1: a=251;break; case 2: a=252;break; case 3: a=95;break; case 4: a=171;break; default: a=35}; type=a==0?type:a  

![](.gitbook/assets/appendix\_a/appendixa\_megabuf.png)

| ** |
| :---- |

#### *Galaxy-like spiral with central bar*  {#appendix-a-galaxy}  

![](.gitbook/assets/appendix\_a/appendixa\_galaxy.png)

| *//g \-c white if(sqrt(x^2+z^2+y^2)\>=32) rotate(x,z,2/(0.03\*(log(sqrt(x^2+z^2)))));(abs(x)\<=16\*(abs(z))/96&\&perlin(123,x,y,z,0.085,1,0)-0.5)\|\|perlin(123,x,y,z,0.17,1,0)-0.9* |
| :---- |

#### *Faster Voronoi Edge  

![](.gitbook/assets/appendix\_a/appendixa\_voronoi.png)

| *//g 251 \-r c=0;v=0;for(i=1,4){v1=v; v=voronoi(1,x+(i%2\!=0)\*(i-2),0,z+(i%2==0)\*(i-2),.03);c+=v1\!=v;  if(c\>1){break}}c\>1* |
| :---- |

#### *Spiral generation brush*  {#appendix-a-spiral-brush}  

![](.gitbook/assets/appendix\_a/appendixa\_spiral.gif)

| */br scmd 0 1 0 "/sel cyl;/outset 64 \-h;/shift 1 u;/calc gmegabuf(0,randint(9999))+gmegabuf(1,randint(16));/g \-c 35  i=2{;}t=0.5;m=1;f=0.03;s=gmegabuf(0);data=gmegabuf(1);rotate(x,z,i\*log(x^2+z^2)+(s%360)\*pi/180);voronoi(s,x\*m,1,z\*m,f)\<t"* |
| :---- |

#### *Alien spire terrain*  {#appendix-a-alien-spire-terrain}  

![](.gitbook/assets/appendix\_a/appendixa\_terrain.png)

| *//g \-r white s=123;f=0.0325;m=2.8;p=0.37;((perlin(s,x/m,y,z/m,f,8,p)-0.233)\*(ridgedmulti(s,x/m,y,z/m,2\*f,1)+1))\*perlin(s,x/m,y/2,z/m,f,8,p)\>=(y/(160\*1.5))+min(perlin(s,x/m,1,z/m,f/0.5,6,p\*1)-0.42,0)\*1.8* |
| :---- |

#### *Block extra voxelization    

![](.gitbook/assets/appendix\_a/appendixa\_voxel.png)

| *//deform \-r scale=3;x=scale\*floor(x/scale);z=scale\*floor(z/scale)* |
| :---- |

#### *Revolve at home (Revolves a slice at x=0 and z\>0 around the y-axis)[^15]*  
[^15]: Note that unlike //revolve the center of your selection defines the center of rotation. Also, note that //deform can “bring” in blocks from outside of your selection.

![](.gitbook/assets/appendix\_a/appendixa\_revolve1.png) ![](.gitbook/assets/appendix\_a/appendixa\_revolve2.png)

| *//deform dist=sqrt(x\*x+z\*z)-0.05; x=0; z=dist;* |
| :---- |

#### *Polygonal Revolve at home (Revolves a slice at x=0 and z\>0 around the y-axis)  

![](.gitbook/assets/appendix\_a/appendixa\_revolve3.png) ![](.gitbook/assets/appendix\_a/appendixa\_revolve4.png)

| *//deform N=7; dist=sqrt(x\*x+z\*z); a=atan2(x,z); r=cos(a-((2\*pi)/N)\*floor((N\*a+pi)/(2\*pi)));  x=0; z=dist\*r;* |
| :---- |

#### *Wraps/Rolls up a given flat pattern (positioned at top of selection going to positive z) into a cylinder shape[^16]*  
[^16]: To get the result like in the picture we used //g 95:0 c=y*y+z*z; return 0.94<c && c<1.0 and //gmask 95:0 , a cylindrical mask, beforehand.

![](.gitbook/assets/appendix\_a/appendixa\_roll1.png) ![](.gitbook/assets/appendix\_a/appendixa\_roll2.png)

| *//deform reach=5.55; theta=(atan2(y,z)/2/pi+0.5); y=1; z=1+(theta\*reach);* |
| :---- |

#### *Converts any input shape to voronoi cells. n3 is the amount of cells.*  
//deform n=7;if(\!megabuf(0)){for(i=0,n-1)for(j=0,n-1)for(k=0,n-1)for(l=0,2)gmegabuf(3\*(n\*n\*i+n\*j+k)+l,((\!l)?i:(l?j:k))+random());megabuf(0,1)}a=n/2;c=gclosest(a\*x+a,a\*y+a,a\*z+a,0,n^3,3);x=gmegabuf(c)/a-1;y=gmegabuf(c+1)/a-1;z=gmegabuf(c+2)/a-1;

| ![](.gitbook/assets/appendix\_a/appendixa\_voronoideform1.png) | ![](.gitbook/assets/appendix\_a/appendixa\_voronoideform2.png) |
| :---: | :---: |

#### *Converts any input shape to perfectly hexagonal columns. n controls amount of hexagons*  
//deform n=33;p=.866;x=(x+1)\*n/2;z=(z+1)\*n/2;t=ceil(x\*2)/2;s=t-.5;v=ceil(z/p)\*p;u=v-p;f=2\*t%2;g=rint(v\*p\*4/3)%2;w=((g?s:t)-x)^2+((f?u:v)-z)^2\>((g?t:s)-x)^2+((f?v:u)-z)^2;x=(w==g?t:s)\*2/n-1;z=(w==f?v:u)\*2/n-1;1

| ![](.gitbook/assets/appendix\_a/appendixa\_hexagonalize1.png) | ![](.gitbook/assets/appendix\_a/appendixa\_hexagonalize2.png) |
| :---- | :---- |