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

#Specify order of rotation application: (Ex: xi, yi, zi)

d1 = zi; d2 = xi; d3 = yi;

r1 = 0;  # Rotation around d1 axis

r2 = 0;  # Rotation around d2 axis

r3 = 0;  # Rotation around d3 axis

####################### Parameters ########################

proj = 0;   #0 for perspective, 1 for parallel

#0 has foreshortening (realism), 1 retains parallelism

d = 10;     #Distance from projection (perspective only)

zoom = 30;  #Size of projection

h = 70*sqrt(xi^2 + yi^2 + zi^2);

v = if(index < 343,1,0);

s = 1;

######## Calculations (don't worry about these) ###########

a1 = d2*cos(r1)-d3*sin(r1); a2 = d2*sin(r1)+d3*cos(r1);
b1 = d1*cos(r2)-a2*sin(r2); b2 = d1*sin(r2)+a2*cos(r2);
c1 = a1*cos(r3)-b1*sin(r3); b3 = a1*sin(r3)+b1*cos(r3);
x' = zoom*c1*if(proj,1,(d/(d+b3)));  #Horizontal output
y' = zoom*b2*if(proj,1,(d/(d+b3)));  #Vertical output

#################Expression by Chrnan6710##################
```
</details>

Currently, the code displays a 7x7x7 cube in perspective projection (realistic) with cyclic hue as distance from the origin increases.

### Parameters

- `xi`, `yi`, and `zi` are the left-right, forward-backward, and top-bottom coordinate inputs respectively, like `x'` and `y'` but in three dimensions.

- `d1`, `d2`, and `d3` specify the order in which the rotation is applied. Set each equal to an axis in your preferred order. For example, if you want to first rotate around the x-axis, then y, then z, set `d1 = xi`, `d2 = yi`, and `d3 = zi`. 
   - Positive rotation about the x-axis is tumbling forward, positive rotation about the y-axis is turning counter-clockwise from the front, and positive rotation about the z-axis is turning counter-clockwise from the top.

- `r1`, `r2`, and `r3` are the angles of rotation in radians (2π radians = 180 deg). `r1` is applied to the `d1` axis, then `r2` to `d2`, and then `r3` to `d3`.
  
- `proj` determines projection style; 0 enables perspective (realistic) projection and 1 enables parallel projection (think Roller Coaster Tycoon 2).

- `d` determines the distance of the origin in three-dimensional space from the "camera" (your view). If it is set lower than the distance of some points, strange artifacts will appear, so be careful.

- `zoom` resizes the projection.
