---
layout: post
title:  "4.10 Rectangle Intersection"
date:   2020-11-09
desc: "Find a intersection for two given rectangles"
keywords: "Coding"
categories: [PYTHON]
tags: [python]
icon: icon-html
---

Problem: Write a program which tests if two rectangles have a nonempty intersection. If the intersection is nonempty, return the rectangle formed by their intersection.

```
Input:
  rect1 - (1, 1), (4,3) ... (x1_d, y1_d, x1_u, y1_u)
  rect2 - (2, 1), (3,4) ... (x2_d, y2_d, x2_u, y2_u)
Expect return their interaction if it isn't empty.
  
  def inside(vetex, rect):
    x1, y1 = vetex
    x_d, y_d, x_u, y_u = rect
    return x_d < x1 and x1 < x_u and y_d < y1 and y1 < y_u
  
  def intersect(rect1, rect2):
    x1_d, y1_d, x1_u, y1_u = rect1
    x2_d, y2_d, x2_u, y2_u = rect2
    if inside((x1_d, y1_d):
      intersect = ((x1_d, y1_d), (min(x1_u, x2_u), min(y1_u, y2_u)))
    elif inside((x1_d, y1_u)):
      intersect = ((x1_d, max(y1_d, y2_u), min(y1_u, y2_u)))
```
