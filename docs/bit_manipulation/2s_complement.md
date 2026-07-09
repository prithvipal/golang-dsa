# 2's Complement

There are two steps to find 2's complement. Let us learn find 2's complement by taking `5` as an example.

Banary of `5` is `101`. Considering this in bit width as 8, it banari will be `00000101` 
**1. Find 1's complement:** The 1's complement can be done by inverting every bit. 

```
00000101
-----------------
11111010
```

**2. Add 1 to the inverted number**
```
11111010
      +1
-----------
11111011      
```

## 2's converts number into negative

When you perform 2's complement on my number, it convert it into negative of te number.

To understand this, we need to know the most significant bit is used to determine negative or positive. If most significant bit is set i.e. `1` then it is negative number. If it is not set i.e `0` then it is positive number.


Considering bit width is 8 for `5`, its binary is `00000101`. Then we perform 2's complement on it, it become `11111011`. 

Let us convert `11111011` into decimal number and see what is the decimal value of it.

As we discussed above that when most significant bit is set then it will be used as negative number.

```
1             1       1      1       1       0        1       1
2^7*(-1) + 2^6*1 + 2^5*1 + 2^4*1 + 2^3*1 + 2^2*0 + 2^1*1 + 2^0*1
-128     +  64   +  32   +   16  +   8   +  0    +   2   +   1
-128+122 = -5
```