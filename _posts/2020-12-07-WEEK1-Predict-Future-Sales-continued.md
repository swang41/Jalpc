---
layout: post
title:  "Predict Future Sales Week 1 continued"
date:   2020-12-08
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
* Next step: [read](https://www.kaggle.com/c/competitive-data-science-predict-future-sales/discussion/74835)


## Notebooks

__Summary:__
* [2nd place summary - Predict future sales](https://www.kaggle.com/c/competitive-data-science-predict-future-sales/discussion/190784)
* [1st place solution gratitudes](https://www.kaggle.com/c/competitive-data-science-predict-future-sales/discussion/74835)

__EDA:__
* [Time series Basics : Exploring traditional TS](https://www.kaggle.com/jagangupta/time-series-basics-exploring-traditional-ts)
* [Model stacking, feature engineering and EDA](https://www.kaggle.com/dimitreoliveira/model-stacking-feature-engineering-and-eda)
* [1st place solution part 1](https://www.kaggle.com/kyakovlev/1st-place-solution-part-1-hands-on-data)

__Features ideas and Ensemble:__
* [Future Sales 3](https://www.kaggle.com/gordotron85/future-sales-xgboost-top-3)
* [Predict Future Sales Top 11 Solution](https://www.kaggle.com/szhou42/predict-future-sales-top-11-solution#Exploratory-Data-Analysis)
* [Feature Engineer and Model Ensemble](https://www.kaggle.com/anqitu/feature-engineer-and-model-ensemble-top-10)
* [Feature engineering, xgboost](https://www.kaggle.com/dlarionov/feature-engineering-xgboost)
* [Dance with Ensemble" Sharing Thread](https://www.kaggle.com/c/avito-demand-prediction/discussion/59880)


## DONE

* __Regenerate my baseline from scratch(hold-out validation)__
    1. W/features: shop_id, item_id, date_num_block.
    2. Lag ... Lagged item_cnt_month for month/shop/item
    3. Date ... Month
    4. Price ... Average and variance of price for month/shop/item

Note: Switching to google colab from kaggle notebook for more consistent performance. 

## Result:

* __Current baseline model: 0.986(public score)__
    * model: xgb
    * completed: 12/13/2020

## Next: 

1. Re-implement the "Future Sale 3" notebook
    * [Future Sales 3](https://www.kaggle.com/gordotron85/future-sales-xgboost-top-3)
    * ETL: by 12/20/2020
