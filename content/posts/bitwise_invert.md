---
title: "Bitwise_invert"
date: 2023-01-29T23:40:47+08:00
summary:  Write a function invert(x, p, n) that returns x with the n bits 
# weight: 1
# aliases: ["/first"]
tags: [""]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Desc Text."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/<path_to_repo>/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

## Description

Write a function invert(x,p,n) that returns x with the n bits that begin at position p inverted 
(i.e., 1 changed into 0 and vice versa), leaving the others unchanged.
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
