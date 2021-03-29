# Three-dimensional vector graphics

This javascript program allows one to create three-dimensional vector graphics through interpolation between vertices. It asks for the desired amount of vertices, the desired amount of edges, the coordinates of the vertices, and the desired connections between vertices.

The resulting expression uses my [three-dimensional engine](3dengine.md) which I plan on improving, so this will likely be updated.
<details>
  <summary>View code</summary>

```
let vcnt = prompt("Amount of vertices?");
let ecnt = prompt("Amount of edges?");
let eden = Math.floor((400-vcnt)/ecnt);
let output = "";

let x = []; //Array of x coordinates
let y = []; //Array of y coordinates
let z = []; //Array of z coordinates
let e1 = []; //Array of connection starts
let e2 = []; //Array of connection ends

for(i = 1; i <= vcnt; i++)
	{
  	x[i] = prompt("X-coordinate for vertex #"+i).toString();
    y[i] = prompt("Y-coordinate for vertex #"+i).toString();
    z[i] = prompt("Z-coordinate for vertex #"+i).toString();
  } //Gets coordinates
  
for(i = 1; i <= ecnt; i++)
	{
  	e1[i] = prompt("Connect which vertex to another? (Connection number "+i+")");
    e2[i] = prompt("Connect it to which vertex? (Connection number "+i+")")
  } //Gets connections
  
let xi = "xi = ";
let yi = "yi = ";
let zi = "zi = "; //Sets up xi, yi, zi
  
for(i = 1; i <= vcnt; i++)
	{
  	xi = xi+"if(index == "+(400-i)+","+x[i]+",";
    yi = yi+"if(index == "+(400-i)+","+y[i]+",";
    zi = zi+"if(index == "+(400-i)+","+z[i]+",";
  } //Sets coordinates of vertices

for(i = 1; i <= ecnt; i++)
	{
  	xi = xi+"if(index < "+i*eden+",lerp(index/"+eden+" - "+(i-1)+","+x[e1[i]]+","+x[e2[i]]+"),";
    yi = yi+"if(index < "+i*eden+",lerp(index/"+eden+" - "+(i-1)+","+y[e1[i]]+","+y[e2[i]]+"),";
    zi = zi+"if(index < "+i*eden+",lerp(index/"+eden+" - "+(i-1)+","+z[e1[i]]+","+z[e2[i]]+"),";
  } //Inputs connections
  
xi = xi+"0";
yi = yi+"0";
zi = zi+"0"; //Vertices not included put at origin
  
for(i = 1; i <= parseInt(vcnt) + parseInt(ecnt); i++)
	{
  	xi = xi+")";
    yi = yi+")";
    zi = zi+")";
  } //Close if statements
  
xi = xi+";";
yi = yi+";";
zi = zi+";";

console.log(output+xi+"\n\n"+yi+"\n\n"+zi);
```

</details>
