---
layout: post
title:  "Predict Future Sales Week 2"
date:   2020-12-13
desc: ""
keywords: "machine learning"
categories: [MACHINELEARNING]
tags: [MACHINELEARNING]
icon: icon-html
---

## Current Competition:
* Predict futures sales
* Timeline: 2 months（01/20/2021）
* Current progress(leaderboard): 0.986 rmse.



## DOING
* ETA: 12/20/20
* Re-implement the "Future Sale 3" notebook
    * [Future Sales 3](https://www.kaggle.com/gordotron85/future-sales-xgboost-top-3)
    * Things to do:
        1. Data Cleanning
            * Same shop but have different id __(USED)__
            * OPTIONAL: Mis-spell in shop name and item category
            * OPTIONAL: Item name cleaning
        2. Features Engineering
            * Extract city/category from shop_name
            * Lag item_cnt_month(mean)
                1. month/shop __(USED)__
                2. month/item __(USED)__
                3. month/shop/item __(USED)__
                4. month/city __(USED)__
                5. month/city/item __(USED)__
                6. month/shop/type __(USED)__
            * price
                1. average price for item
                2. lag price for month/item
                3. delta ... lag_price/avg_price __(USED)__
            * revenue
                1. lag total renveue for month/shop
                2. delta ... lag_revenue/avg_revenue __(USED)__
            * Date:
                1. Month __(USED)__
                2. Days __(USED)__
                3. Months of first item/shop __(USED)__
                4. Months of first item __(USED)__
       3. Basic feature:
            * Item_id __(USED)__
            * Shop_id __(USED)__
            * Date_block_num __(USED)__
Note: Switching to google colab from kaggle notebook for more consistent performance. 

## Result:
* __Current baseline model: ?(public score)__
    * model: single xgb with no hypertuning ... 0.911 pls
    * completed: 12/18/2020

## Next: 
* Re-implement the "top 2..." notebook
    * Two step model(classification --> regression) ... no improvement
    * Error analysis
    * Ensemble
