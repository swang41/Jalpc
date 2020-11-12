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
  
  def intersect(rect1, rect2):
     def inside(vetex, rect):
      x1, y1 = vetex
      x_d, y_d, x_u, y_u = rect
      return x_d < x1 and x1 < x_u and y_d < y1 and y1 < y_u
      
    x1_d, y1_d, x1_u, y1_u = rect1
    x2_d, y2_d, x2_u, y2_u = rect2
    if inside((x1_d, y1_d):
      intersect = ((x1_d, y1_d), (min(x1_u, x2_u), min(y1_u, y2_u)))
    elif inside((x1_d, y1_u)):
      intersect = ((x1_d, max(y1_d, y2_d), (min(x1_u, x2_u), y2_u)))
    elif inside((x1_u, y1_d)):
      intersect = ((max(x1_d, x2_d), y1_d), (x1_u, min(y1_u, y2_u)))
    elif inside((x1_u, y1_u)):
      intersect = ((max(x1_d, x2_d), max(y1_d, y2_d)), (x1_u, y1_u))
    else:
      interset = None
    return intersect
```

Based on the observation above, the intersect coordinates: the bottom-left will be the max of two left-bottom coords and top-right will be the min of two top-right coords if the intersect exists.

In order to have intersect, according to the solution from the book, one rect's bottom-left x coord need to be the left of the other rect's top-right x coord, the other rect's bottom-left need to be the left of the one rect's top-right x coord. Same rules applies to y coords.

```
Rectangle = collections.namedtuple('Rectangle', ('x', 'y', 'w', 'l'))

def intersect(r1, r2):
  def is_intersect(r1, r2):
    return (r1.x < r2.x + r2.w and r1.x + r1.w > r2.x and r1.y < r2.y + r2.l and r1.y + r1.l > r2.y)
  
  if is_intersect(r1, r2):
    return Rectangle(max(r1.x, r2.x), max(r1.y, r2.y), min(r1.x+r1.w, r2.x+r2.w) - max(r1.x, r2.x), min(r1.y+r1.l, r2.y+r2.l) - max(r1.y, r2.y))
  else:
    return Rectangle(0, 0, 0, 0)
```

Variant 1: Given four points in the plane, how would you check if they are the vertices of a rectangle.

Variant 2: How would you check if two rectangles, not necessarily aligned with the X and Y axes, intersect.
