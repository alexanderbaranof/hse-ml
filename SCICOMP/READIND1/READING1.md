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

X | Y | (1) X AND Y |(2) X OR Y  | XOR(X, Y) = (2) AND NOT (1)
--|---|-------------|------------|-------------------------
0 | 0 |      0      |      0     |     0
0 | 1 |      0      |      1     |     1
1 | 0 |      0      |      1     |     1
1 | 1 |      1      |      1     |     0


Exercise: Prove De Morgan's theorem, NOT(X OR Y) = NOT(X) AND NOT(Y), by completing the table and checking the last two columns are the same.

X | Y | (1) NOT X | (2) NOT Y |NOT (X OR Y)| (1) AND (2)
--|---|-----------|-----------|-------|---------
0 | 0 |     1     |     1     |   1   |    1
0 | 1 |     1     |     0     |   0   |    0
1 | 0 |     0     |     1     |   0   |    0
1 | 1 |     0     |     0     |   0   |    0


Exercise: using truth tables, check these three equations

NOT(X) = NAND(1, X) = NOT(1 AND X)

X | Y | NOT(X) | (1) 1 AND X | NOT (1) = NAND(1, X)
--|---|--------|-------------|-------------------
0 | 0 |    1   |       0     |         1
0 | 1 |    1   |       0     |         1
1 | 0 |    0   |       1     |         0
1 | 1 |    0   |       1     |         0


AND(X, Y) = NOT(NAND(X, Y)) = NOT(NOT(X AND Y))

X | Y | (1) X AND Y | NOT NOT (1) = NOT(NAND(X, Y))
--|---|-------------|------------------------
0 | 0 |      0      |           0
0 | 1 |      0      |           0
1 | 0 |      0      |           0
1 | 1 |      1      |           1


OR(X, Y) = NAND(NOT(X), NOT(Y))) = NOT(NOT(X) AND NOT(Y))

X | Y | (1) NOT X | (2) NOT Y |( 1) AND (2) = NAND(NOT(X), NOT(Y))) | X OR Y
--|---|-----------|-----------|-------------------------------|--------
0 | 0 |     1     |     1     |                0              |   0
0 | 1 |     1     |     0     |                1              |   1
1 | 0 |     0     |     1     |                1              |   1
1 | 1 |     0     |     0     |                1              |   1


Exercise: write similar formulas expressing NOT, AND, and OR in terms of NOR

NOT(X) = NOR(0,X)

X | A = 0 OR X | NOT A | NOT X
--|------------|-------|-------
0 |     0      |1      |1
1 |     1      |0      |0



AND(X,Y) = NOR(NOR(0,X),NOR(0,Y)))

X | Y | (1) NOR(0,X) | (2) NOR(0,Y) | NOR((1),(2)) | X AND Y
--|---|--------------|--------------|----------|---------
0 | 0 |1             |1             |0         |0
0 | 1 |1             |0             |0         |0
1 | 0 |0             |1             |0         |0
1 | 1 |0             |0             |1         |1



OR(X,Y) = NOR(NOR(0, NOR(0, X)), NOR(0, NOR(0, Y)))

X | Y | (1) NOR(0,X) | (2) NOR(0,Y) | (3) NOR(0, (1)) | (4) NOR(0, (2)) | NOR((3), (4))
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


X | Y | (1) AND(0, X) | (2) AND(0, Y) | AND((1), (2)) | OR(X, Y)
--|---|---------------|---------------|-----------|----------
0 | 0 |0              |0              |0          |0
0 | 1 |0              |0              |0          |1
1 | 0 |0              |0              |0          |1
1 | 1 |0              |0              |0          |1


OR(X,Y) = AND(AND(0, X), AND(1, Y))

X | Y | (1) AND(0, X) | (2) AND(1, Y) | AND((1), (2)) | OR(X, Y)
--|---|---------------|---------------|-----------|----------
0 | 0 |0              |0              |0          |0
0 | 1 |0              |1              |0          |1
1 | 0 |0              |0              |0          |1
1 | 1 |0              |1              |0          |1


OR(X,Y) = AND(AND(1, X), AND(1, Y))

X | Y | (1) AND(1, X) | (2) AND(1, Y) | AND((1), (2)) | OR(X, Y)
--|---|---------------|---------------|-----------|----------
0 | 0 |0              |0              |0          |0
0 | 1 |0              |1              |0          |1
1 | 0 |1              |0              |0          |1
1 | 1 |1              |1              |1          |1



### Binary numbers as lists of boolean values

Exercise: Without listing explicitly, how many possible 8-bit binary numbers are there?

2^7 = 256

Exercise: Convert X = 110 to decimal.

0 \* 2^0 + 1 \* 2^1 + 1 \* 2^2 = 6

Exercise: Convert 11 to binary.

11 // 2 = 5 -> 11 - 10 =  1

5 // 2 = 2 -> 5 - 4 = 1

2 // 2 = 1 -> 2 - 2 = 0

1 // 2 = 0 -> 1 - 0 =  1

11 (decimal) = 1011 (binary)

Exercise: Convert these powers of 2 into binary: 2, 4, 8, 16, 32. What do you notice?

2 = 10

4 = 100

8 = 1000

16 = 10000

32 = 100000

Just one more digit is added

Exercise: Convert these numbers into binary: 1, 3, 7, 15, 31 (they are all 2^n - 1 for some n). What do you notice?

1 = 1

3 = 11

7 = 111

15 = 1111

31 = 11111

These numbers consist only of the digit 1 because they are one less than the power of two


Exercise: check that these numbers all have the same 3-bit representation: 3 = 11 = 17, 0 = 8 = 16, 2 = 10 = 18.


3 = \*\*011\*\*

11 = 1\*\*011\*\*

17 = 10001

3 = 11 != 17



0 = \*\*000\*\*

8 = 1\*\*000\*\*

16 = 10\*\*000\*\*

0 = 8 = 16


2 = \*\*010\*\*

10 = \*\*010\*\*10

18 = 10\*\*010\*\*

2 = 10 = 18


### Binary arithmetic as logical operations

Exercise: complete the table by converting 2 into single-bit binary:

X0 | Y0 | Z0
---|----|----
0  | 0  | 0
1  | 0  | 1
0  | 1  | 1
1  | 1  | 0

Exercise: do the same for single-bit multiplication: write down the table of binary numbers for X0, Y0, and the binary representation of their product Z0, and find the logical operation which matches. We say this operation implements single-bit multiplication.

X0 | Y0 | Z0
---|----|----
0  | 0  | 0
1  | 0  | 0
0  | 1  | 0
1  | 1  | 1

AND is implements single-bit multiplication


### Digital Logic

Exercise: Using A and B as the inputs, and OUT as the output, explain how this circuit acts as NAND(A,B); for each entry in the truth table, follow the explanation above. True is "high energy" and False is "low energy".

A | B | NAND(A,B)
--|---|----------
0 | 0 | 1
0 | 1 | 1
1 | 0 | 1
1 | 1 | 0

Exercise: Using A and B as the inputs, and OUT as the output, explain how this circuit acts as NAND(A,B); for each entry in the truth table, follow the explanation above. True is "high energy" and False is "low energy".

 A |  B | NAND(A,B) |                                                                  |
---|----|-----------|------------------------------------------------------------------|
0  | 0  | 1         | both gates were without power, so there was a loss of power |
1  | 0  | 1         | one of the gates was without power, so energy was lost|
0  | 1  | 1         | oone of the gates was without power, so energy was lost|
1  | 1  | 0         | both gates were energized, so there was no loss of power|


## Networking

### Name resolution and Routing

Exercise: show that every IPv4 can be represented by four 8bit unsigned integers, and that every 8bit unsigned integer is between 0 and 255.

IPv4 is 32-bit number and 32 = 4 \* 8.
IPv4 has the following format XXXXXXXX.XXXXXXXX.XXXXXXXX.XXXXXXXX
Each number can be from 00000000 to 11111111.

Exercise: how many IPv4 addresses are there? Is it enough? Explain.

2^32 = 4294967296 addresses. 
This number of addresses is not enough since there are a large number of network clients. For example, people started to use not only personal computers, but also the internet of things

Exercise: use ping in a terminal to resolve a domain name. Copy-paste the command you used, and the result.

Command: ping -c 5 hse.ru

alexanderbaranof@192 HSE-ML % ping -c 5 vk.com


PING vk.com (93.186.225.208): 56 data bytes


64 bytes from 93.186.225.208: icmp_seq=0 ttl=55 time=12.951 ms


64 bytes from 93.186.225.208: icmp_seq=1 ttl=55 time=19.805 ms


64 bytes from 93.186.225.208: icmp_seq=2 ttl=55 time=19.740 ms


64 bytes from 93.186.225.208: icmp_seq=3 ttl=55 time=18.173 ms


64 bytes from 93.186.225.208: icmp_seq=4 ttl=55 time=20.217 ms

--- vk.com ping statistics ---
5 packets transmitted, 5 packets received, 0.0% packet loss


round-trip min/avg/max/stddev = 12.951/18.177/20.217/2.704 ms


### Bandwidth, latency, reliability

Exercise: The Multipath TCP project aims to allow TCP packets to be split across multiple network links and reassembled at the destination. For example, if you were uploading a 100 megabyte file to a server from your phone, it would allow you to send 75 megabytes by WiFi and 25 megabytes by cellular automatically. How should the ratio be chosen if you want to minimise transmission time? Minimise cellular bandwidth use? Explain.

To answer this question, let's find out the speed of mobile Internet and wi-fi. The normal speed of mobile Internet is 40 megabits per second, and wi-fi speed is 400 megabits per second. Therefore, the data must be divided into 11 parts, where 10 parts will be uploaded via wi-fi and one part via the mobile network. The key idea is to divide the data in proportion to the speed ratio.

To minimize data over the mobile network, you must either not use it or send a portion of the data less than the proportion of the speed.

Exercise: UDP is popular for streaming media; explain why.

UDP is faster because it does not require checking that the packet has been delivered to the recipient. This can affect a fragment of an image or sound. For example there can be interference in the picture sometimes. But in general this does not affect the overall quality of the transmitted content.

Exercise: Read the Wikipedia articles on multicast and anycast routing. Why is anycast good for content delivery networks, and why is multicast good for live-streaming? What are some other uses for these?

Anycast sends the data to the nearest recipient. This makes content delivery faster.

Multicast allows you to send one large file at a time, for example, rather than sending it every time to every computer. This makes it suitable for sending streams in real time.