---
layout: post
title:  "4.9 Check decimal integer is a palindrome"
date:   2020-11-08
desc: "Check if a decimal integer is a palindrome"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Write a program that takes an integer and determines if that integer's representation as decimal string is a palindrome(negative integer isn't palindrome.).

```
def is_palindrome(i_num):
  if i_num < 0:
    return False
  most_left = 1
  while most_left*10 < i_num:
    most_left *= 10
  while most_left > 1:
    if i_num // most_left != i_num % 10:
      return False
    i_num //= 10
    i_num %= most_left
    most_left = most_left//100
  return True
```
