## README ##

In this repo I have an example of elliptic curve cryptography. 

Elliptic curve cryptography involves moving arround a field defined by an elliptic curve. This may be used in two ways. Either Alice and Bob wish to exchange keys in which they use the elliptic curve field in order to generate a shared key using the elliptic curve Diffie-Hellman (ECDH) algorithm or else Bob wishes to get a signature from Alice in which case they will use the elliptic Curve Digital Signature (ECDS) algorithm. Only the key sharing algorithm will be discussed here because I'm lazy.

### ECDH ###

In this system Alice and Bob will agree on a curve to use, the domain of the curve and the starting point for the algorithm. For example when working with the curve y<sup>2</sup>=x<sup>3</sup> + &alpha;x + &beta; they must decide on the values of &alpha; and &beta; as well as the domain, p. Next they must decide their starting point G. Now Alice and Bob will both calculate n*G where n is their private keys. They will send the results to one another and then repeat with each other's ending points as the start point in order to get a shared end point which they will use as their final shared key.

### IMPORTANT NOTE ###

I am some guy in a room. You should never use the code here for real encryption purposes. I hope it will help you understand the principal of elliptic curve key sharing but this has not been checked by anyone with any real expertise or training in cryptography.

### The mathematics of elliptic fields ###

In order to do these things however we must understand the mathematics of elliptic curves over finite fields. Since this is the hardest part of understanding elliptic curve cryptography (and also the most interesting) we will discuss it in detail here.

In order to add points together we draw a line between the two points and find the third intesection point. This is then flipped in the y axis to find the final value of the point.

<p align="center">
<image src='./curve_drawing_addition.png' width="500px;" align="center"></image>
</p>

We now have two equations, A and B, which describe the curve and the line respectively.

y<sup>2</sup> = x<sup>3</sup> + Ax + B --- (A)

y = m * x + c --- (B)

By solving these equations we arrive at equation C

x<sub>3</sub> = m<sup>2</sup> - x<sub>1</sub> - x<sub>2</sub> --- (C)

in order to find the value of the point x_3 and then we will use equation D in order to find the value of y<sub>3</sub>

y<sub>3</sub> = m(x<sub>3</sub> - x<sub>2</sub>) + y<sub>2</sub> --- (D)

by solving these equations within the prime field p we end up with the the point R`, (x<sub>3</sub>, -y<sub>3</sub>), we then flip this in the y axis in order to aquire the final point R (x<sub>3</sub>, y<sub>3</sub>).

If we want to add a point to itself, in effect double it, we draw a line tangent to our point and find the point (x<sub>3</sub>, y<sub>3</sub>) as shown below.

<p align="center">
<image src='./curve_drawing_doubling.png' width="500px;" align="center"></image>
</p>

Since we have ways of doubling and adding we can perform multiplication of a point by a scalar by using the russian peasant multiplication algorithm.

This is a simple algorithm for performing multiplication which is described in full in reference #6.


### Sources ###

* http://www.crypto-textbook.com/
* http://arstechnica.com/security/2013/10/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/
* https://en.wikipedia.org/wiki/Elliptic_curve_cryptography
* https://hackernoon.com/what-is-the-math-behind-elliptic-curve-cryptography-f61b25253da3
* https://www.math.brown.edu/~jhs/Presentations/WyomingEllipticCurve.pdf
* https://www.basic-mathematics.com/russian-peasant-multiplication.html
