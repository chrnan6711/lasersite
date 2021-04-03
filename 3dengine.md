# Three-dimensional Engine

This expression allows for the projection of points in three-dimensional space. The projection can be rotated around various axes, zoomed in and out, and placed a set distance from the "camera".

### Code

<details>
  <summary>View code</summary>
  
```
#########Make sure to use rectangular grid 20x20!########## 

###################### Coordinates ########################

xi = lerp((index%7)/7,-3,4);           #Left-right

yi = lerp((floor(index/7)%7)/7,-3,4);  #Back-front

zi = lerp((floor(index/49)%7)/7,-3,4); #Down-up

######################## Angles ###########################

xr = 0; #Tumble forward

yr = 0; #Counter-clockwise from front

zr = 0; #Counter-clockwise from top

#Specify order of application: (r1, then r2, then r3)

r1 = yr; r2 = xr; r3 = zr;

####################### Parameters ########################

proj = 0;   #0 for perspective, 1 for parallel

#0 has foreshortening (realism), 1 retains parallelism

d = 10;     #Distance from projection (perspective only)

zoom = 30;  #Size of projection

h = 70*sqrt(xi^2 + yi^2 + zi^2);

v = if(index < 343,1,0);

s = 1;

######## Calculations (don't worry about these) ###########

x1 = xi*cos(r1)-zi*sin(r1); z1 = xi*sin(r1)+zi*cos(r1);
y2 = yi*cos(r2)-z1*sin(r2); z2 = yi*sin(r2)+z1*cos(r2);
x3 = x1*cos(r3)-y2*sin(r3); y3 = x1*sin(r3)+y2*cos(r3);

x' = zoom*x3*if(proj,1,(d/(d+y3)));  #Horizontal output

y' = zoom*z2*if(proj,1,(d/(d+y3)));  #Vertical output

#################Expression by Chrnan6710##################
```
</details>

Currently, the code displays a 7x7x7 cube in perspective projection (realistic) with cyclic hue as distance from the origin increases.

### Parameters

- `xi`, `yi`, and `zi` are the left-right, forward-backward, and top-bottom coordinate inputs respectively, like `x'` and `y'`.

- `xr`, `yr`, and `zr` are the angles of rotation in radians (2π radians = 180 deg). The y-rotation is applied first, then x, then z.

- `r1`, `r2`, and `r3` specify the order in which the axes of rotation are applied. This is necessary because three-dimensional rotation is non-commutative (order matters).

- `proj` determines projection style; 0 enables perspective (realistic) projection and 1 enables parallel projection (think Roller Coaster Tycoon 2).

- `d` determines the distance of the origin in three-dimensional space from the "camera".

- `zoom` resizes the projection.
