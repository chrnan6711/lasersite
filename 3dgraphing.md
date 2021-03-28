# Three-dimensional Graphing

This expression allows for the graphing of real functions with two-dimensional variables.

### Variables

All variables are explained in the second section of the expression.

```

xi = lerp((index%(res+1))/res,-100,100)/(10*scale);
yi = lerp(floor(index/(res+1))/res,-100,100)/(10*scale);

#########################################################

#Parameters:

res = 15;
#Amount of plotted points in x and y directions

scale = 1;
#The "zoom" of the function, larger = farther in

axis = 1;
#Amount of plotted points in each direction of the axes

cs = 0.5;
#Color scale, larger number = more colors across z

zr = projectionTime/3; 
#Rotation around z-axis in radians

xr = 0.5;
#Rotation around x-axis in radians

z = 0;
#Equation: z = f(xi,yi)

#########################################################

axisn = 2(axis/scale) + 1;

xa = lerp((index-(400-3*axisn))/(axisn-1),-100,100);
ya = lerp((index-(400-2*axisn))/(axisn-1),-100,100);

x' = if(index > (400-(3*axisn+1)) & index < (400-2*axisn),

cos(zr)*xa,

if(index > (400-(2*axisn+1)) & index < (400-axisn),

sin(zr)*ya,

if(index > (400-(axisn+1)),

0,

xi*10*scale*cos(zr) - yi*10*scale*sin(zr)

)));

y' = if(index > (400-(3*axisn+1)) & index < (400-2*axisn),

sin(xr)*sin(zr)*xa,

if(index > (400-(2*axisn+1)) & index < (400-axisn),

sin(xr)*-cos(zr)*ya,

if(index > (400-(axisn+1)),

cos(xr)*lerp((index-(400-axisn))/(axisn-1),-100,100),

sin(xr)*(xi*10*scale*sin(zr) + yi*10*scale*cos(zr)) + 10*scale*z*cos(xr)

)));

h = if(index > (400-(3*axisn+1)) & index < (400-2*axisn),0,if(index > (400-(2*axisn+1)) & index < (400-axisn),120,if(index > (400-(axisn+1)),240,

if(index < (res+1)^2,lerp(cs*z+0.5,280,320),300)

)));

s = 1;

v = if(index > 400-(3*axisn+1),1,if(index < (res+1)^2,1,0));

# Expression by Chrnan6710

```
