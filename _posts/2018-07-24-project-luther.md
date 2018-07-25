---
layout: post
title: No Result is NOT Meaningless
--- 
## Introduction

In this project, I wanted to answer the following question:

**Can we predict Amazon User Ratings of Smartphones based on their specs?**

## Target & Features

The target variable is *Amazon User Ratings*.
The features are:
* price (not really a feature, but to make it more interesting)
* screen size
* phone weight
* battery capacity
* ram
* memory/storage
* camera quality (fps)

## Approach

1. Web scraped Amazon and an additional smartphone specs site.
2. Clean, wrangle and transform data (aka. feature engineering)
3. train-test-split
4. Cross validation/ kFold
5. Fit different models:
	* Linear Regression/OLS
	* Lasso
	* Polynomial Regression
	* RandomForest Regressor

## Results

The table shown below is a summary of R-squared scores.

|---|---|---|
|Model|Train|Test|
|---|---|---|
|Linear Reg.|0.0414|-0.0756|
|---|---|---|
|OLS|0.0414|0.0765|
|---|---|---|
|Lasso|0.00112|-0.0238|
|---|---|---|
|Polynomial (d=4)|0.999|-8.03e^11|
|---|---|---|
|RandomForest Reg.|0.0524|-0.0323|
|---|---|---|
