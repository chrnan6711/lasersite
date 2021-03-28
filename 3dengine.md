# Three-dimensional Engine

This expression allows for the projection of points in three-dimensional space. The projection can be rotated around various axes, zoomed in and out, and placed a set distance from the "camera".

### Variables

`xi`, `yi`, and `zi` are the coordinate inputs, like `x'` and `y'`.

`xr`, `yr`, and `zr` are the angles of rotation in radians (2π radians = 180 deg). The y-rotation is applied first, then x, then z. I am working on a new version which allows one to change the order, since three-dimensional rotations are noncommutative.

`proj` determines projection style; 0 enables perspective (realistic) projection and 1 enables parallel projection.

`d` determines the distance of the origin in three-dimensional space from the "camera".

`zoom` resizes the projection.

```

###################### Coordinates ########################

xi = 0;           #Left-right

yi = 0;  #Back-front

zi = 0; #Down-up

######################## Angles ###########################

xr = 0; #Tumble forward

yr = 0; #Counter-clockwise from front

zr = 0; #Counter-clockwise from top

#Order of application is yr, xr, zr

####################### Modifiers #########################

proj = 0;   #0 for perspective, 1 for parallel projection

#0 has foreshortening (realism), 1 retains parallelism

d = 10;     #Distance from projection (perspective only)

zoom = 30;  #Size of projection

h = 70*sqrt(xi^2 + yi^2 + zi^2);

v = if(index < 343,1,0);

s = 1;

######## Calculations (don't worry about these) ###########

cx = cos(xr); cy = cos(yr); cz = cos(zr);
sx = sin(xr); sy = sin(yr); sz = sin(zr);

x' = zoom*((xi*cy-zi*sy)*cz-(yi*cx-(xi*sy+zi*cy)*sx)*sz)*if(proj,1,(d/(d+((xi*cy-zi*sy)*sz+(yi*cx-(xi*sy+zi*cy)*sx)*cz)))); #Horizontal output

y' = zoom*(yi*sx+(xi*sy+zi*cy)*cx)*if(proj,1,(d/(d+((xi*cy-zi*sy)*sz+(yi*cx-(xi*sy+zi*cy)*sx)*cz)))); #Vertical output

#########Make sure to use rectangular grid 20x20!########## 

#################Expression by Chrnan6710##################

```