# Three-dimensional Injection

This code allows one to turn any 2D expression into a 3D one; basically, it places any 2D projection into 3D space.

### Instructions

1. In your code, change `x'` to `xi` and `y'` into `zi` (not `yi`!).
2. Paste the following code at the end of your code:

<details>
  <summary>View code:</summary>
  
```

yi = 0;

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

zoom = 1;  #Size of projection

h = 0;

v = 1;

s = 1;

######## Calculations (don't worry about these) ###########

x1 = xi*cos(r1)-zi*sin(r1); z1 = xi*sin(r1)+zi*cos(r1);
y2 = yi*cos(r2)-z1*sin(r2); z2 = yi*sin(r2)+z1*cos(r2);
x3 = x1*cos(r3)-y2*sin(r3); y3 = x1*sin(r3)+y2*cos(r3);
x' = zoom*x3*if(proj,1,(d/(d+y3)));  #Horizontal output
y' = zoom*z2*if(proj,1,(d/(d+y3)));  #Vertical output

#####################3D by Chrnan6710######################

```

</details>

Because 2D expressions have no depth, the `yi` coordinate was added in order to open up that dimension.
