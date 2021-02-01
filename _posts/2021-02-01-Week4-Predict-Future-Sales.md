---
layout: post
title:  "Predict Future Sales Week 4"
date:   2021-02-01
desc: ""
keywords: "machine learning"
categories: [MACHINELEARNING]
tags: [MACHINELEARNING]
icon: icon-html
---

## Current Competition:
* Predict futures sales
* Timeline: 3 months (2/28/2021)
* Goal: Top 3%(300-0.87)
* Current progress(leaderboard): 0.898 pls(Top 12%)

## Two main goals
1. According to previous top 1/2 winner post, the key winning trick in this solution is stratifing the problem: by checking if the item in testset existing in the training set (1st place solution - Part 1 - "Hands on Data")[https://www.kaggle.com/kyakovlev/1st-place-solution-part-1-hands-on-data/]; by focusing on shop with high rsme in validation set(claimed improve their solution from 0.88 to 0.84)[2nd place summary - Predict future sales](https://www.kaggle.com/c/competitive-data-science-predict-future-sales/discussion/190784)
2. Ensemble: Given the fact that, there're only 0.01 improvment with adding/cleaning features, probably it is time to apply ensemble
    * Current full model
    * Reimplement the mean encoding feature by following (antiqu soltion)[https://www.kaggle.com/anqitu/feature-engineer-and-model-ensemble-top-10]


## Result:
* __Current baseline model: ??... ?? (public score)__
    * model: single lgb with no hypertuning 
    * completed: 
## Next: 
