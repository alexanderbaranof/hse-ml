# Data Representation I

## Numerical representations

### Binary and hexadecimal representations

Exercise: build a list of all four-digit binary numbers, and compute the corresponding single-digit hexadecimal number.

four-digit binary numbers | single-digit hexadecimal number
--------------------------|---------------------------------
0000                      |0
0001                      |1
0010                      |2
0011                      |3
0100                      |4
0101                      |5
0110                      |6
0111                      |7
1000                      |8
1001                      |9
1010                      |A
1011                      |B
1100                      |C
1101                      |D
1110                      |E
1111                      |F


### Floating point numbers

Exercise: Pretend we use a naïve floating-point format with 5bit mantissa and 3bit exponent (base-2). What is the smallest possible positive number representable? What is the largest positive number representable? The first bit of each is used for sign:

The smallest possible positive number representable: 

[00001][111] = 1 \* 2^0 \* 10^(-3) = 0.001

The largest positive number representable: 

[01111][011] = 15 \* 10^3 = 15000

#### Exercise: use python to check this:

```python
from decimal import Decimal

print(repr(Decimal(0.1)))
```
Output
```
Decimal('0.1000000000000000055511151231257827021181583404541015625')
```

Exercise: what is the best approximation of 0.01?

```python
print(repr(Decimal(0.01)))
```
Output
```
Decimal('0.01000000000000000020816681711721685132943093776702880859375')
```



## Simple data structures: lists, trees, graphs

### Linked lists

Exercise: use diagrams like the above to explain how to delete an item from a linked list.

Before 


---------------       ---------------       ---------------
| x[0] | next |--->---| x[1] | next |--->---| x[2] | NULL | 
---------------       ---------------       ---------------


After 


---------------               ---------------
| x[0] | next |--->---|--->---| x[2] | NULL | 
---------------               ---------------

For the example x0 next should start referring to x2. And the object that is not referenced now can be deleted.


### Trees

Exercise: assemble the numbers 1-10 into binary search trees which are (a) maximally unbalanced to the left, (b) balanced, (c) one step from balanced.

a) maximally unbalanced to the left

                       10
                      /
                     9
                    /
                   8
                  /
                 7
                /
               6
              /
             5
            /
           4
          /
         3
        /
       2
      /
     1



b) balanced

             5
          /     \
         3       8
        / \     / \
       2   4   7   9
      /       /     \
     1       6       10

c) one step from balanced.

           5
          / \
         3   8
        /   / \
       2   7   9
      /   /     \
     1   6       10
        /
       4



### Graphs

Exercise: assemble a directed acyclic graph with the numbers 1-12 by strict divisibility: an edge from A to B if B/A is prime. There are no directed cycles, but some nodes do have multiple paths to them. (These form cycles if you ignore the direction.) Which ones? Explain how to decide if a number will have multiple paths to it.

TODO

Exercise: Identify several maximal spanning trees in the divisibility graph from the previous exercise.

TODO

Exercise: model acquaintance using a graph (vertices are people, an edge between A and B means A knows B). Model it with a directed graph. How are these different?

TODO


## Cryptographic ideas

### Hashing

Exercise: this doesn't mean the file was transferred correctly; why not?

This method may not work if the error blocks are the same size as the original blocks

Exercise: do the same for files with "cat" and "cat2" instead of "hi" and "hi2"

```
$ echo cat > testfile; echo cat2 > testfile2
$ md5sum testfile testfile2
54b8617eca0e54c7d3c8e6732c6b687a  testfile
4307ab44204de40235bad8c66cce0ae9  testfile2
$ sha1sum testfile testfile2
8f6abfbac8c81b55f9005f7ec09e32d29e40eb40  testfile
f476b8741936d51309437ffc5c87081c7b24ffb1  testfile2
$ sha512sum testfile testfile2
644c7b649d31fc3c432534fb80d71a3a5e2b3eb65e737eb15c6e6af96e40c8ee3dcb55fd172e263783e62f8d94f5c99e12a016d581b860700640e45c9c1b87b3  testfile
84c308d32247eb3b590ff27b47d5018551dd6ad3e696b6d61b1e70fed7570522812a2c3353e93db38728f4a10de5156996b144d2b150f1ffe92ba7a301b5bfe2  testfile2
$ b2sum testfile testfile2
0247169dd9d258599e4a4327067f74f3dbd7db0e6d623954212738e62c233b410141a1eab4130073b99a8959e3d52f70da7402ae8d94ca6333126ec3b4e0bca7  testfile
48d92c152ff4c58a948d75f7aaba6ccaf00f8f9beb78e3399fe0f325e758af657c07eb2d83a753f3fe16074b149f46390abce8673c7477f75aae99427c9defa7  testfile2
```


### Symmetric cryptography

Exercise: implement the Caesar cipher in python, which advances each letter of 'M' by 'SEC = n': enc(1, "a") = "b", etc.

```python
import string

def shift(alphabet, step):
        return alphabet[step:] + alphabet[:step]

def caesar(text, step):
    alphabets = str(string.ascii_lowercase) + str(string.ascii_uppercase) + str(string.digits)
    shifted_alphabets = shift(alphabet=alphabets, step=step)
    joined_aphabets = ''.join(alphabets)
    joined_shifted_alphabets = ''.join(shifted_alphabets)
    table = str.maketrans(joined_aphabets, joined_shifted_alphabets)
    return text.translate(table)

print(caesar('sasha', step=4))
Output
wewle
```