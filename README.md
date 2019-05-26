Triangulation from distance differences
=======================================


The Problem
-----------

```
+----------------------------+
|                            |
|   A                   A    |
|                            |
|                            |
|             ?              |
|                            |
|                            |
|                            |
|                            |
|              A             |
|                            |
+----------------------------+
```

 Given three points of known position and the _difference_ between the distances from each to a fourth point, find it's position is space.

Example
-------

```
 +-----------+
 |           |
 |     A     |
 |           |
 |           |
 | A   ?   A |
 |           |
 +-----------+
 ```

 Positions of the three points: {(0,0), (2,0), (1,2)}
 
 Position of the fourth _unknown_ point: (0,1)
 
 So the three _unknown_ distances would be:
 d1 = |p1-p?| = 1
 d2 = |p2-p?| = 1
 d3 = |p3-p?| = 2
 
 Which would result in the following input to our problem:
 D31 := d3 - d1 = 1
 D32 := d3 - d2 = 1

Algorithm
---------

The algorithm takes in the positions of the three points and a pair of differences (which two doesn't matter since they can be transformed into each other) and returns the position of the unknown point.

Solution
--------

Without loss of generality, the problem's complexity can be reduced by choosing the coordinate system such that one point is the origin and a second one is on the x axis, so only the x-value of the second point and the position of the third is non-zero.

The resulting set of equations to solve is:

x²+y² = (t+a+b)²
(x-x2)²+(y)² = (t+b)²
(x-x3)²+(y-y3)² = t²

for {x,y,t} (though t is of no interest to us).

Which is solvable using [the magic of wolfram alpha](https://www.wolframalpha.com/input/?i=solve%5B%7B(x)%5E2%2B(y)%5E2%3D%3D(t%2Ba)%5E2,+(x-p)%5E2%2B(y)%5E2%3D%3D(t%2Bb)%5E2,+(x-q)%5E2%2B(y-r)%5E2%3D%3Dt%5E2%7D,%7Bx,y,t%7D%5D), giving us some very long and ugly equations for x, y (and t). All that remains is to translate those into code and we are done.


Implementation
--------------

In the subfolder [c/](c/) is a c implementation of the solution.
