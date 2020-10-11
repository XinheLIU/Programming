# [Bitwise Operations](https://en.wikipedia.org/wiki/Bitwise_operation)

## Basic Concepts

- how computer save negative numbers
- auti-code: 1 as 0, 0 as 1 for negative numbers
- complement code: anti-code + 1 for negative numbers
- negative numbers stored as complement code

## Common Operations

XOR

```py
x ^ 0 == x
x ^ 1s == ~x # 1s = ~0
x ^ x == 0
x ^ (~x) = 1s
a ^ b ^ c = a ^ (b ^ c) # associative
```

Swap numbers

```py
i = i + j
j = i - j
i = i - j
# or
i = i ^ j;
j = j ^ i;
i = i ^ j;
```

Operations

```py
# odd or even
x & 1 == 1 , x & 1 == 0
# divide by 2
x >> 1
# clear the last ( lowest ) 1
x & (x - 1)
# get the lowest 1
x & - x 
# multiply 7
x << 3 - x
```

Bitwise and String

```py
c ^= 32 # lower case to higher, higher to lower
c |= 32 # to lower case
c &= -33 # to higher case
```