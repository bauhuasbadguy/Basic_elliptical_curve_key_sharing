## README ##

In this repo I have some examples of eliptic curve cryptography. 

Eliptic curve cryptography involves moving arround a field defined by an eliptic curve. This may be used in two ways. Either Alice and Bob wish to exchange keys in which they use the eliptic curve field in order to generate a shared key using the eliptic curve Diffie-Hellman (ECDH) algorithm or else Bob wishes to get a signature from Alice in which case they will use the Eliptic Curve Digital Signature (ECDS) algorithm. 

A brief rundown of these algorithms is below

### ECDH ###

In this system Alice and Bob will agree on a curve to use, the domain of the curve and the starting point for the algorithm. For example when working with the curve y<sup>2</sup>=x<sup>2</sup> + &alpha;x + &beta; they must decide on the values of &alpha; and &beta; as well as the domain, p. Next they must decide their starting point G. Now Alice and Bob will both calculate n&dot;G where n is their private keys. They will send the results to one another and then repeat with each other's ending points as the start point in order to get a shared end point which they will use as their final shared key.

### ECDS ###

### The mathematics of eliptic fields ###

In order to do these things however we must understand the mathematics of eliptic curves over finite fields. Since we are working now with field theory everything gets really complicated. All mathematical operations must now be reconceptualised. We see the complexities of algebra in finite fields when we look at AES and Twofish which also make use of finite fields. 



### Sources ###

* http://www.crypto-textbook.com/
* http://arstechnica.com/security/2013/10/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/
* https://en.wikipedia.org/wiki/Elliptic_curve_cryptography
* https://hackernoon.com/what-is-the-math-behind-elliptic-curve-cryptography-f61b25253da3