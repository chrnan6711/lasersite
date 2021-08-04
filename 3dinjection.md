# Three-dimensional Injection

This code allows one to turn any 2D expression into a 3D one; basically, it places a 2D projection into 3D space.

### Instructions

1. In your code, change `x'` to `xi` and `y'` into `zi` (not `yi`!).
2. Paste the following code at the end of your own code:

<details>
  <summary>View code:</summary>
  
```

yi = 0;

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

h = 0;

v = 1;

s = 1;

######## Calculations (don't worry about these) ###########

a1 = d2*cos(r1)-d3*sin(r1); a2 = d2*sin(r1)+d3*cos(r1);
b1 = d1*cos(r2)-a2*sin(r2); b2 = d1*sin(r2)+a2*cos(r2);
c1 = a1*cos(r3)-b1*sin(r3); b3 = a1*sin(r3)+b1*cos(r3);
x' = zoom*c1*if(proj,1,(d/(d+b3)));  #Horizontal output
y' = zoom*b2*if(proj,1,(d/(d+b3)));  #Vertical output

#####################3D by Chrnan6710######################

```

</details>

3. Consult the [three-dimensional engine page](3dengine.md) for further instructions.

Because 2D expressions have no depth, there is no `yi` coordinate by default; hence, the injection adds one for you.
