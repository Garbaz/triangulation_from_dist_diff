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

 Given three points of known position and the _difference_ between the distances from each to a fourth point, find it's position in space.

A practical example of such a problem would be three beacons sending a signal at the same, but to the reciever unknown, time. The reciever recieves these at different times, therefore, with the speed of the signal (e.g. speed of sound or speed of light) and the difference between the arrival times, the recievers position is to be calculated (Given the location of the beacons are known).

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
 
 d1 = |p1-p?| = 1\
 d2 = |p2-p?| = 1\
 d3 = |p3-p?| = 2
 
 Which would result in the following input to our problem:

 D12 := d1 - d2 = 0\
 D13 := d1 - d3 = 1\
 D23 := d2 - d3 = -1
 
 (Though only two of these values need to be known, since the third can always be calculated from the other two).


Solution
--------

Without loss of generality, the problem's complexity can be reduced by choosing the coordinate system such that one point is the origin and a second one is on the x axis, so only the x-value of the second point and the position of the third is non-zero.

With a=D12 and b=D13-D12 for convenience, the resulting set of equations to solve is:

x²+y² = (t+a+b)²\
(x-x2)²+(y)² = (t+b)²\
(x-x3)²+(y-y3)² = t²

for {x,y,t} (though t is of no interest to us).

Which is solvable using [the magic of wolfram alpha](https://www.wolframalpha.com/input/?i=solve%5B%7B(x)%5E2%2B(y)%5E2%3D%3D(t%2Ba)%5E2,+(x-p)%5E2%2B(y)%5E2%3D%3D(t%2Bb)%5E2,+(x-q)%5E2%2B(y-r)%5E2%3D%3Dt%5E2%7D,%7Bx,y,t%7D%5D), giving us some very long and ugly equations for x, y (and t). All that remains is to translate those into code and we are done.


Implementation
--------------

In the subfolder [c/](c/) is a c implementation of the solution.

**April 2024 Update:** For a current project, I've also implemented the solution to this problem is Rust! See the repo [distance_difference_triangulation](https://github.com/Garbaz/distance_difference_triangulation).
