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
1. According to previous top 1/2 winner post, the key winning trick in this solution is stratifing the problem: by checking if the item in testset existing in the training set [1st place solution - Part 1 - "Hands on Data"](https://www.kaggle.com/kyakovlev/1st-place-solution-part-1-hands-on-data/); by focusing on shop with high rsme in validation set(claimed improve their solution from 0.88 to 0.84) [2nd place summary - Predict future sales](https://www.kaggle.com/c/competitive-data-science-predict-future-sales/discussion/190784)
   * Snapshot from kyakolev:
   ```
   We have 3 types of products in the test set:

   Products that have some "sales history" - these are (let's call it) NORMAL items - we can use lags features/price history/etc -> all possible features for normal time series data.

   Items that have some history but we do not have any "item/shop" match in the train data -> good example here -> "digital" items. You can find that only one shop is selling digital items, but we cannot be so sure about other items/shop pairs. Probably we can find items that we don't need to do any prediction and set 0 for them (if not -> mark it as normal items and do normal prediction).

   Items that we have no history at all. There are three options -
   3.1. This is a new item -> NEW RELEASE (we don't need time series features) -> we need to predict future sales based on the type of the product and shop overall "specialty" (how many similar products were sold there) and other "categorical" features and time series features for item category but NOT for certain Item.
   3.2. This is an old item -> OLD RELEASE, but nobody wants to buy it. Probably you can do some FE from the name of the item or category. These are totally random sales -> that depend only "how far Venus from Mars in 3/4 part of June in the year 1968" -> it is very hard to do predictions here, but we are lucky that most of such cases are close to 0.
   3.3 Products that were not included in the train set but have some history. It is hard to recognize such products -> so I decided to remove this option.

   Hope it helps. I wish to say more, but I don't want to ruin LB (still 7 moths to go).
   ```
   * Snapshot from Hoan Dao
   ```
   After we train a model with preprocessed data and make predictions on the validation set, we calculated rmse for all shops, rmse for all items and rmse for all shop-item combines. Based on error analysis, we got an objective idea about which one causes high loss to our models. Then we find the way to track and analyze these items or ensemble highest-rmse shops presented in the section Ensemble below.
   As a result, we filtered the shops causing high loss to our models such as shop_id = [9, 20, 25, 31, 42,…]. However the shops with id = 9, 20 did not appear in the test set. So we dropped these shops from the train and validation set, just training the shops in the test set.

   Override submission: after the error analysis stage, we are able to obtain the highest rmse shops (>1.0). We train and predict particularly this shop's data. Then overriding the submission file into the submission of the trained model of the full dataset. This technique helps us so much at the beginning of the competition, since the LB score could be 0.842.
   ```
2. Ensemble: Given the fact that, there're only 0.01 improvment with adding/cleaning features, probably it is time to apply ensemble
    * Current full model
    * Reimplement the mean encoding feature by following (antiqu soltion)[https://www.kaggle.com/anqitu/feature-engineer-and-model-ensemble-top-10]


## Result:
* __Current baseline model: ??... ?? (public score)__
    * model: single lgb with no hypertuning 
    * completed: 
## Next: 
