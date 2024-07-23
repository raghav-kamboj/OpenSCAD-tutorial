
# Tutorial of OpenSCAD: 
By Raghav & Warjot kaur
---
## Contents:
1. Introduction about OpenSCAD.
2. Downloading and interface familiarisation.
3. Basic 3-D shapes introduction [Cube(), Sphere(), Cylinder()]
4. Transformations [Rotate(), Translate(), Scale(), Mirror()]
5. Modifiers [ Difference, Intersection, Union]
6. Boolean operation
7. Facets
8. The mini project

## 1. Introduction about OpenSCAD:
OpenSCAD is a software for creating 3D CAD models. It is different from other 3D modeling software in that it is script-based.

### What is CAD?

CAD stands for Computer-Aided Design. It's a technology that allows engineers, architects, and designers to create detailed drawings and models of objects or buildings on a computer. Instead of drawing by hand, they use special software that helps them design things more accurately and efficiently.

CAD software lets you create 2D drawings or 3D models of almost anything you can imagine, from simple objects like furniture to complex structures like skyscrapers or even parts for machines. It's like a virtual drafting table where you can sketch out your ideas, add measurements, test different designs, and see how everything fits together—all without having to physically build anything until you're sure it's exactly what you want.

CAD has revolutionized the way things are designed because it allows designers to make changes easily, collaborate with others over long distances, and simulate how their designs will work in real life. It's a powerful tool that's used across many industries, including engineering, architecture, manufacturing, and even in fields like fashion and animation.

## 2. Downloading and Interface Familiarisation:

[openscad.org](http://openscad.org)

Go to the site and click on downloads. After clicking the download button you will enter the site (https://openscad.org/downloads.html). Here you will get different files to download as per your system. If it's a Windows system, then scroll down to Windows; if Linux/Mac, then scroll to it and download the files and install them. After installing, you will have a simple as well as a little bit complex interface. Don't worry, we will make you familiar with the interface. So let's begin!


### Interface Familiarisation:

- **Text Editor**: In OpenSCAD, you use a text editor just like when you write a story or a letter. Instead of words, you write commands that describe shapes and how they fit together. For example, you might type `cube([10, 20, 30]);` to create a cube that's 10 units wide, 20 units tall, and 30 units deep.
- **Viewing Area**: There's a window where you can see what your designs look like in 3D. As you type commands in the text editor, this window updates to show your model from different angles. It's like seeing a preview of what you're creating.
- **Console Area**: Below the text editor and viewing window, there's a place where messages and information about your design show up. If there's a mistake in your commands, this area tells you what went wrong so you can fix it.

So, imagine writing instructions in a notebook (text editor) to build a toy, and as you write, you can look through a magic window (viewing area) to see how your toy is coming along. If something doesn't work right, a friendly helper (console area) tells you what needs fixing. That's how OpenSCAD helps you create cool 3D models with just words and a window!

## 3. Basic 3-D Shapes:

There are four basic 3-D shapes in OpenSCAD: Cube(), Sphere(), Cylinder().

We will discuss each shape one by one. So let's begin!

1. **Cube()**
   ```scad
   cube(size, center);
   // or
   cube([cube_size, cube_size, cube_size]);
   ```

2. **Sphere()**
   ```scad
   sphere(r=radius);
   ```

3. **Cylinder()**
   ```scad
   cylinder(r=radius, h=height);
   ```

Now open the software and write the code, placing the numeric values where required. For example:
```scad
cylinder(r=10, h=10);
```

Congratulations! You made your first 3D figure.

### A little advanced syntax:
1. `cylinder(r=radius, h=height, center=true/false, $fn=facets);`
2. `cylinder(r1, r2, h);` or `cylinder(d1, d2, h);`
   - `r1`: bottom radius
   - `r2`: top radius

## 4. Transformations:
In OpenSCAD, transformations (often abbreviated as "transforms") are operations used to modify the position, orientation, and scale of objects within the 3D space. These transformations allow you to manipulate and arrange shapes to create complex models. There are several types of transformations commonly used in OpenSCAD:

1. **Translate**
   ```scad
   translate([x, y, z])
   ```
   Moves an object from its current position to a new position specified by [x, y, z] coordinates.

   Example:
   ```scad
   translate([10, 20, 0])
   cube([20, 30, 40]);
   ```
   This moves a cube with dimensions 20x30x40 units to the position [10, 20, 0].

2. **Rotate**
   ```scad
   rotate([x, y, z])
   ```
   Rotates an object around the [x, y, z] axes by the specified angle in degrees.

   Example:
   ```scad
   rotate([0, 0, 45])
   cube([20, 20, 20]);
   ```
   This rotates a cube by 45 degrees around the z-axis.

3. **Scale**
   ```scad
   scale([x, y, z])
   ```
   Resizes an object by scaling it along the [x, y, z] axes by the specified factors.

   Example:
   ```scad
   scale([1.5, 1, 0.5])
   cube([20, 30, 40]);
   ```
   This scales a cube to be 1.5 times wider, the same height, and half as deep.

4. **Mirror**
   ```scad
   mirror([x, y, z])
   ```
   Reflects an object across the [x, y, z] axes.

   Example:
   ```scad
   mirror([1, 0, 0])
   cube([20, 20, 20]);
   ```
   This mirrors a cube across the x-axis.

## 5. Modifiers:
Modifiers in OpenSCAD are operations used to alter the appearance or geometry of objects without changing their fundamental position, orientation, or scale in 3D space. A commonly used modifier is `color()`:

### The color() Modifier:
The `color()` modifier in OpenSCAD is used to assign a color to objects or shapes within your 3D models. It allows you to visually distinguish different parts of your design or create more realistic renderings.

```scad
color("color_name" or [r, g, b, a])
```
- **"color_name"**: A string specifying a named color, such as "blue", "red", "green", etc.
- **[r, g, b, a]**: An array specifying the color using RGBA values, where r, g, b are red, green, and blue components (0-1), and a is alpha transparency (optional, 0-1).

### Examples:

1. **Using Named Colors:**
   ```scad
   color("blue")
   cube([20, 20, 20]);
   ```
   This example colors a cube blue.

2. **Using RGBA Values:**
   ```scad
   color([1, 0.5, 0, 0.8])
   sphere(r=15);
   ```
   This example colors a sphere in orange with 80% opacity.

## 6. Boolean Operation:
Boolean operations allow you to combine shapes in various ways to create complex geometries.

1. **Union**
   ```scad
   union() {
       cube([20, 20, 20]);
       translate([30, 0, 0])
       sphere(15);
   }
   ```
   The `union()` operation combines multiple shapes into a single object by merging their volumes.

2. **Difference**
   ```scad
   difference() {
       cube([20, 20, 20]);
       translate([10, 10, 0])
       sphere(15);
   }
   ```
   The `difference()` operation creates a new shape by subtracting one or more objects from a base object.

3. **Intersection**
   ```scad
   intersection() {
       cube([20, 20, 20]);
       translate([10, 10, 10])
       sphere(15);
   }
   ```
   The `intersection()` operation creates a new shape that represents the overlapping volume of multiple objects.

## 7. Facets ($fn)
Facets (`$fn`) control the number of sides or segments used to approximate circular shapes (like spheres, cylinders, and circles) in OpenSCAD. The higher the number of facets, the smoother and more rounded the shape appears.

### Syntax and Usage:
- **Global Setting**: `$fn` is a global variable that sets the number of segments for all subsequent shapes that rely on it.
- **Default Value**: If not specified, the default value of `$fn` is typically 12.

### Example:
```s
$fn = 50;
sphere(r=20);
```
This example sets `$fn` to 50 before creating a sphere with a radius of 20 units. The sphere will appear smoother due to the increased number of segments used to approximate its surface.

## 8. The Mini Project:
### The Making of a Car

```scad
$fa = 1;
$fs = 0.4;
wheel_radius = 8;
base_height = 8;
top_height = 10;
track = 40;
body_roll = 0;
wheels_turn = 20;

rotate([body_roll, 0, 0]) {
// Car body base
cube([60, 20, base_height], center=true);
// Car body top
translate([5, 0, base_height/2 + top_height/2 - 0.001])
cube([30, 20, top_height], center=true);
}

// Front left wheel
translate([-20, -track/2, 0])
rotate([0, 0, wheels_turn])
sphere(r=wheel_radius);

// Front right wheel
translate([-20, track/2, 0])
rotate([0, 0, wheels_turn])
sphere(r=wheel_radius);

// Rear left wheel
translate([20, -track/2, 0])
rotate([0, 0, 0])
sphere(r=wheel_radius);

// Rear right wheel
translate([20, track/2, 0])
rotate([0, 0, 0])
sphere(r=wheel_radius);

// Front axle
translate([-20, 0, 0])
rotate([90, 0, 0])
cylinder(h=track, r=2, center=true);

// Rear axle
translate([20, 0, 0])
rotate([90, 0, 0])
cylinder(h=track, r=2, center=true);
```
---

## Thank you
