---
layout: post
title:  "Predict Future Sales Week 3"
date:   2020-12-19
desc: ""
keywords: "machine learning"
categories: [MACHINELEARNING]
tags: [MACHINELEARNING]
icon: icon-html
---

## Current Competition:
* Predict futures sales
* Timeline: 2 months（01/20/2021）
* Goal: Top 3%
* Current progress(leaderboard): 0.911 pls(Top 20%)



## DOING
* ETA: 12/28/20
* Follow the summary from "2nd place summary - Predict Future Sales" notebook and recreate the 
    1. Two step model(classification --> regression) ... no improvement
    2. More features
        * Sliding windows ... mean/quantile/std within the time(5, 7, 12) windows of item_cnt_month for shop/item 
        * Mean encoding ... mean of item_cnt_month for shop/item(using 32 months for train, 33 months validation, ? for test) 
        * Item name (Tfidf text feature) ... ["item_id", "item_name"]??
        * Cleaning:
          * Fix category in "Predict Future Sales Top 11 Solution"(link)[https://www.kaggle.com/szhou42/predict-future-sales-top-11-solution]
          * Subtype?
        *  Ideas from (1st place solution - Part 1 - "Hands on Data")[https://www.kaggle.com/kyakovlev/1st-place-solution-part-1-hands-on-data/]
          * item_id
            1. Release date
            2. Days on sale
            3. Neighbors (items with id 1000 and 1001 could be somehow similar)
          * shop_id
            1. Opening month (possible opening sales)
            2. Closed Month (possible stock elimination)
          * Price
            1. Price category (1/10/20/etc) ... obviously items with smaller price have greater volumnes
            2. Discount and Discount duration
            3. Price lag (shows discount)
            4. Price correction (rub/usd pair)
            5. Shop Revenue
          * Dates
            1. Weekends and holidays sales (to correct monthly sales)
            2. Number of days in month (to correct monthly sales)
          * Shop info ... structure: shop_name shop city | shop type | shop name
          * Item info ... structure: item name [category feature](additional feature)
          * Category info ... structure: section name - subsection
          * Test set:
            1. Item/shop pairs that are in train
            2. items without any data
            3. items that are in the train
    3. Error analysis
      * Calculated rmse for all shops, rmse for all items and rmse for all shop-item combines.
    4. Ensemble
      * TBD

## Result:
* __Current baseline model: 0.911 (public score)__
    * model: single xgb with no hypertuning ... ??
    * completed: 12/28/2020

## Next: 

