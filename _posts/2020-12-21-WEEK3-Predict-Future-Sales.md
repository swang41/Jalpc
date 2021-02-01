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
* Timeline: 3 months (2/28/2021)~~2 months（01/20/2021）~~
* Goal: Top 3%(300)
* Current progress(leaderboard): 0.911 pls(Top 20%)

## Main Findings:
* Found a error in the function used to generate lag feature(which has been hard coded the join key as shop/item/date) ... 0.91 --> 0.901 
* Found the sliding window std feature generated earlier is empty
* Found lightgbm not only more efficient but actually give better score with more features ... 0.901 --> 0.898

## Item tried in details
* Actual: 1/17/2021 ~~ETA: 12/28/20~~
* Followed the summary from "2nd place summary - Predict Future Sales" notebook and recreate the 
    1. __Two step model(classification --> regression) ... no improvement__
        * Classification: whether a shop/item/date_block_num has a sale or not
        * Regression: how many sale for a shop/item/date_block_num
        * Comment: Using same feature set but just switch the target format didn't help instantly in this case while combine them both. probably require other adjusmtnet in order to make it work.
    2. More features
        * Sliding windows ... mean/quantile/~~std~~ within the time(5, 7, 12) windows of item_cnt_month for shop/item [x]
        * Mean encoding ... mean of item_cnt_month for shop/item(using 32 months for train, 33 months validation, ? for test)[WILL BE ADDED(follow)[https://www.kaggle.com/anqitu/feature-engineer-and-model-ensemble-top-10]] 
        * Item name (Tfidf text feature) [x] ... not really improve the main model overall
        * Cleaning:
          * Fix category in "Predict Future Sales Top 11 Solution"(link)[https://www.kaggle.com/szhou42/predict-future-sales-top-11-solution] [x]
        *  Ideas from (1st place solution - Part 1 - "Hands on Data")[https://www.kaggle.com/kyakovlev/1st-place-solution-part-1-hands-on-data/]
          * item_id
            1. Release date
            2. Days on sale
            3. Neighbors (items with id 1000 and 1001 could be somehow similar) [x]
                * add right/left one item sales as neigborhood sales
          * shop_id
            1. Opening month (possible opening sales)
            2. Closed Month (possible stock elimination)
          * Price
            1. Price category (1/10/20/etc) ... obviously items with smaller price have greater volumnes
            2. Discount and Discount duration [x]
            3. Price lag (shows discount) [x]
            4. ~~Price correction (rub/usd pair)~~
            5. Shop Revenue [x]
          * Dates
            1. Weekends and holidays sales (to correct monthly sales)
            2. Number of days in month (to correct monthly sales)
          * Shop info ... structure: shop_name shop city | shop type | shop name
          * Item info ... structure: item name [category feature](additional feature)
          * Category info ... structure: section name - subsection
          * Test set:
            1. Item/shop pairs that are in train ??
            2. items without any data ??
            3. items that are in the train ??
    3. Error analysis
      * Calculated rmse for all shops, rmse for all items and rmse for all shop-item combines.
      * __Comment: shop 9/20/25/... has the largest rmse with two possible cause, shop 9/20 are seasonaly shop while 9 has 6 month interval and  20 has 12 month interval. other shops have large sale volumne. __

## Result:
* __Current baseline model: 0.898 ... top12% (public score)__
    * model: single lgb with no hypertuning 
    * completed: 1/17/2022

## Next: Two main goal
1. According to previous top 1/2 winner post, the key winning trick in this solution is stratifing the problem: by checking if the item in testset existing in the training set (1st place solution - Part 1 - "Hands on Data")[https://www.kaggle.com/kyakovlev/1st-place-solution-part-1-hands-on-data/]; by focusing on shop with high rsme in validation set(claimed improve their solution from 0.88 to 0.84)[2nd place summary - Predict future sales](https://www.kaggle.com/c/competitive-data-science-predict-future-sales/discussion/190784)
2. Ensemble: Given the fact that, there're only 0.01 improvment with adding/cleaning features, probably it is time to apply ensemble
    * Current full model
    * Reimplement the mean encoding feature by following (antiqu soltion)[https://www.kaggle.com/anqitu/feature-engineer-and-model-ensemble-top-10]

