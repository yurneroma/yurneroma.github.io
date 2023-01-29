---
title: "Bitwise_invert"
date: 2023-01-29T23:40:47+08:00
---

## Description

Write a function invert(x,p,n) that returns x with the n bits that begin at position p inverted (i.e., 1 changed into 0 and vice versa), leaving the others unchanged.

input unsigned x = 0b00000100;
output res =  0b000001010;

## solution

![](/img/Bitwise%20Operators%20-6.jpg)

## code

``` c
#include <stdio.h>

unsigned invert(unsigned x, int p, int n) {
  // 1. clear n bits of x to zero
  unsigned a = x & ~(~(~0 << n) << (p + 1 - n));
  unsigned invert_nbits = ~(x >> (p + 1 - n)) & ~(~0 << n);

  return a | invert_nbits << (p + 1 - n);
}

void print(unsigned x) {
  for (int i = 8; i >= 0; --i) {
    printf("%d", (x >> i) & 1);
  }
  printf("\n");
}

int main() {
  unsigned x = 0b00000100;
  unsigned res = invert(x, 3, 3);
  print(res);
}
```
