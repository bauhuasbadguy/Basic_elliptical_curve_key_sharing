## README ##

In this repo I have some examples of eliptic curve cryptography. 

Eliptic curve cryptography involves moving arround a field defined by an eliptic curve. This may be used in two ways. Either Alice and Bob wish to exchange keys in which they use the eliptic curve field in order to generate a shared key using the eliptic curve Diffie-Hellman (ECDH) algorithm or else Bob wishes to get a signature from Alice in which case they will use the Eliptic Curve Digital Signature (ECDS) algorithm. Only the key sharing algorithm will be discussed here because I'm lazy.

A brief rundown of these algorithms is below

### ECDH ###

In this system Alice and Bob will agree on a curve to use, the domain of the curve and the starting point for the algorithm. For example when working with the curve y<sup>2</sup>=x<sup>3</sup> + &alpha;x + &beta; they must decide on the values of &alpha; and &beta; as well as the domain, p. Next they must decide their starting point G. Now Alice and Bob will both calculate n*G where n is their private keys. They will send the results to one another and then repeat with each other's ending points as the start point in order to get a shared end point which they will use as their final shared key.


### The mathematics of eliptic fields ###

In order to do these things however we must understand the mathematics of eliptic curves over finite fields. Since this is the hardest part of understanding eliptic curve cryptography (and also the most interesting) we will discuss it in detail here.

In order to add points together 

<image src='./curve_drawing_addition.png'></image>

We now have two equations (for the ) A and B

y<sup>2</sup> = x<sup>3</sup> + Ax + B --- (A)

y = m * x + c --- (B)

By solving these equations we arrive at equation C

x<sub>3</sub> = m<sup>2</sup> - x<sub>1</sub> - x<sub>2</sub> --- (C)

in order to find the value of the point x_3 and then we will use equation D in order to find the value of y<sub>3</sub>

-y<sub>3</sub> = m(x<sub>3</sub> - x<sub>2</sub>) + y<sub>2</sub> --- (D)

by solving these equations within the prime field p we end up with the sum of these two points (x<sub>3</sub>, y<sub>3</sub>)

If we want to add a point to itself, in effect double it, we draw a line tangent to our point and find the point (x<sub>3</sub>, y<sub>3</sub>) as shown below.

<image src='./curve_drawing_doubling.png'></image>

Since we have ways of doubling and adding we can perform multiplication of a point by a scalar by using the russian peasant multiplication algorithm.

This is a simple algorithm for performing multiplication which is described in full in reference #6


# NOTE FIX REPO NAME SPELLING #

### Sources ###

* http://www.crypto-textbook.com/
* http://arstechnica.com/security/2013/10/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/
* https://en.wikipedia.org/wiki/Elliptic_curve_cryptography
* https://hackernoon.com/what-is-the-math-behind-elliptic-curve-cryptography-f61b25253da3
* https://www.math.brown.edu/~jhs/Presentations/WyomingEllipticCurve.pdf
* https://www.basic-mathematics.com/russian-peasant-multiplication.html