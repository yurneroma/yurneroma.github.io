---
title: "位运算-用Y的最右n位设置X的从p开始的n位"
date: 2020-09-15T11:30:03+00:00
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
summary: "Write a function setbits(x,p,n,y) that returns x with the n bits "
description: "Desc Text"
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
ShowRssButtonInSectionTermList: false
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

Write a function setbits(x,p,n,y) that returns x with the n bits that begin at
position p set to the rightmost n bits of y, leaving the other bits unchanged.

example:
x = 00001110;
y = 10101011;
n = 3
p = 3

## code

``` c

unsigned setbits(unsigned x, int p, int n, unsigned y) {

  // before "|" symbol,  set n bits of x to zero
  // after "|" symbol, get rightmost n bits of y, clear the other bits of y, and
  // move n bits to  position P
  // bitwise 重要性质:
  // - 0 OR N == N
  // - 0 AND N == 0
  // 1 OR N == N bits 1
  // 1 AND N == N
  return x & ~(~(~0 << n) << (p + 1 - n)) | (y & ~(~0 << n)) << (p + 1 - n);
}

void print(unsigned x) {
  for (int i = 31; i >= 0; --i) {
    printf("%d", (x >> i) & 1);
  }
  printf("\n");
}

int main() {
  unsigned x = 0b00001110;
  unsigned y = 0b10101011;
  int n = 3, p = 3;

  int res = setbits(x, p, n, y);
  print(res);
} 

```

## Solution

![](/img/Bitwise%20Operators%20-2.jpg)
![](/img/Bitwise%20Operators%20-3.jpg)
![](/img/Bitwise%20Operators%20-4.jpg)
![](/img/Bitwise%20Operators%20-5.jpg)
