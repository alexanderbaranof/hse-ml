# Computer Architecture I

## Ideas of electronics


### Interlude: review of logic



Exercise: Compute the truth table for NOT:

X | NOT X
--|-------
0 |   1
1 |   0


Exercise: Compute the truth table table for AND.
X | Y | X AND Y
--|---|--------
0 | 0 |   0
0 | 1 |   0
1 | 0 |   0
1 | 1 |   1

Exercise: Compute the truth table for exclusive-or, defined by the formula:

XOR(X, Y) = (X OR Y) AND NOT (X AND Y)

X | Y | A = X AND Y | B = X OR Y | NOT A | XOR(X, Y) = B AND NOT A
--|---|-------------|------------|-------|-------------------------
0 | 0 |      0      |      0     |   1   |     0
0 | 1 |      0      |      1     |   1   |     1
1 | 0 |      0      |      1     |   1   |     1
1 | 1 |      1      |      1     |   0   |     0


Exercise: Prove De Morgan's theorem, NOT(X OR Y) = NOT(X) AND NOT(Y), by completing the table and checking the last two columns are the same.

X | Y | A = X OR Y | B = NOT X | C = NOT Y | NOT A | B AND C
--|---|------------|-----------|-----------|-------|---------
0 | 0 |      0     |     1     |     1     |   1   |    1
0 | 1 |      1     |     1     |     0     |   0   |    0
1 | 0 |      1     |     0     |     1     |   0   |    0
1 | 1 |      1     |     0     |     0     |   0   |    0


Exercise: using truth tables, check these three equations

NOT(X) = NAND(1, X) = NOT(1 AND X)

X | Y | NOT(X) | A = 1 AND X | NOT A = NAND(1, X)
--|---|--------|-------------|-------------------
0 | 0 |    1   |       0     |         1
0 | 1 |    1   |       0     |         1
1 | 0 |    0   |       1     |         0
1 | 1 |    0   |       1     |         0


AND(X, Y) = NOT(NAND(X, Y)) = NOT(NOT(X AND Y))

X | Y | A = X AND Y | B = NOT A | NOT B = NOT(NAND(X, Y))
--|---|-------------|-----------|------------------------
0 | 0 |      0      |     1     |           0
0 | 1 |      0      |     1     |           0
1 | 0 |      0      |     1     |           0
1 | 1 |      1      |     0     |           1


OR(X, Y) = NAND(NOT(X), NOT(Y))) = NOT(NOT(X) AND NOT(Y))

X | Y | A = NOT X | B = NOT Y | C = A AND B | NOT C = NAND(NOT(X), NOT(Y))) | X OR Y
--|---|-----------|-----------|-------------|-------------------------------|--------
0 | 0 |     1     |     1     |      1      |                0              |   0
0 | 1 |     1     |     0     |      0      |                1              |   1
1 | 0 |     0     |     1     |      0      |                1              |   1
1 | 1 |     0     |     0     |      0      |                1              |   1


Exercise: write similar formulas expressing NOT, AND, and OR in terms of NOR

NOT(X) = NOR(0,X)

X | A = 0 OR X | NOT A | NOT X
--|------------|-------|-------
0 |     0      |1      |1
1 |     1      |0      |0



AND(X,Y) = NOR(NOR(0,X),NOR(0,Y)))

X | Y | A = NOR(0,X) | B = NOR(0,Y) | NOR(A,B) | X AND Y
--|---|--------------|--------------|----------|---------
0 | 0 |1             |1             |0         |0
0 | 1 |1             |0             |0         |0
1 | 0 |0             |1             |0         |0
1 | 1 |0             |0             |1         |1



OR(X,Y) = NOR(NOR(0, NOR(0, X)), NOR(0, NOR(0, Y)))

X | Y | A = NOR(0,X) | B = NOR(0,Y) | C = NOR(0, A) | D = NOR(0, B) | NOR(C, D)
--|---|--------------|--------------|---------------|---------------|----------
0 | 0 |1             |1             |0              |0              |0
0 | 1 |1             |0             |0              |1              |0
1 | 0 |0             |1             |1              |0              |0
1 | 1 |0             |0             |1              |1              |1


Exercise: why NOT and OR can't be expressed in terms of AND? Explain.


This can easily be demonstrated by trying to write a truth table


NOT(X) = AND(0,X) 

X | NOT(X) | AND(0,X)
--|--------|---------
0 |1       |0
1 |0       |0

NOT(X) = AND(1,X)

X | NOT(X) | AND(1,X)
--|--------|---------
0 |1       |0
1 |0       |1

OR(X,Y) = AND(AND(0, X), AND(0, Y))


X | Y | A = AND(0, X) | B = AND(0, Y) | AND(A, B) | OR(X, Y)
--|---|---------------|---------------|-----------|----------
0 | 0 |0              |0              |0          |0
0 | 1 |0              |0              |0          |1
1 | 0 |0              |0              |0          |1
1 | 1 |0              |0              |0          |1


OR(X,Y) = AND(AND(0, X), AND(1, Y))

X | Y | A = AND(0, X) | B = AND(1, Y) | AND(A, B) | OR(X, Y)
--|---|---------------|---------------|-----------|----------
0 | 0 |0              |0              |0          |0
0 | 1 |0              |1              |0          |1
1 | 0 |0              |0              |0          |1
1 | 1 |0              |1              |0          |1


OR(X,Y) = AND(AND(1, X), AND(1, Y))

X | Y | A = AND(1, X) | B = AND(1, Y) | AND(A, B) | OR(X, Y)
--|---|---------------|---------------|-----------|----------
0 | 0 |0              |0              |0          |0
0 | 1 |0              |1              |0          |1
1 | 0 |1              |0              |0          |1
1 | 1 |1              |1              |1          |1