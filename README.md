# dada
Dimension-Aware Data Analysis - a programming language that enforces dimensional homogeneity

Dada is a language designed to improve the safety and algorithmic correctness of scientific computing by enforcing dimensional similarity and scale awareness at compile time, i.e. it checks that expressions are physically possible via dimensional analysis and that the arguments of the expression are within valid bounds.

It is a purely functional language with a lisp-like syntax intended to clearly separate function code and compiler hints to generate simple code at runtime with maximum safety.


**Examples:**
```
(defun calc-velocity (<x:m> <t:s> ==> <m/s>)
     (/ x t))
```
This simple example describes a function that calculates a velocity from position (meters, dimension [L]) and time (seconds, dimension [t]) arguments and returns an appropriate value (meters/second, dimensions [L][-t]). This is dimensionally sound, and the only bound on the function would be that `t` cannot equal zero.

```
(defun calc-area (<x:m> <y:in> ==> <m^2>)
     (* x y))
```
This describes a function that calculates an area from from two length scales, one in meters and one in inches, and then returns an area in square meters. The conversion between USCS and SI units can be handled at compile time by emitting code to convert `y` to the appropriate units.
