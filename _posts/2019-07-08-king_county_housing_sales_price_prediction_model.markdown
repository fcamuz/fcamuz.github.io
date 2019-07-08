---
layout: post
title:      "King County Housing Sales Price Prediction Model"
date:       2019-07-08 16:03:33 -0400
permalink:  king_county_housing_sales_price_prediction_model
---


I have done my first linear regression moel project. It was a long journey starting from learning Python and its libraries  to combining them with data analysing methods. I have used OSEMN methodoly to complete this project.  OSEMN is an acronym that represents Obtain, Scrub, Explore, Model, and iNterpret steps. Let me explain each step briefly.

### Obtain
This step requires understanding the problem, collecting and obtaining the data that you need.

### Scrub
During this stage, the main task is clean and filter the data. You might need to change some data formats to standardised all accros the dataset. Take care of null values, placeholders etc. In this step, you might also derivate new columns from the current data to make better use of them in your model. Most of the time exploring anf scrubbing goes simultanously. After dealing with null values and placeholders, you wou;d want to do the exploring. Although scaling and normalisation is as a part of the scrubbing step, it is more accurate to do exploring part before doing all those. Also feature enginering is also part of scrubbing step which selecting the columns that will be ussed in your model. So before eliminating the columns, they must be used in the exploration step.

### Explore
This step focuses on exploring the data you have. Understand each columns, inspect the datatypes, be comfortable with the dataset. Exploring dataset should bring up some meanngful businnes questions and answering them by using the data. Those questiona might be given to you or it might be just up to you to make sense out of the dataset you have. You will have to be able to gain some data visualisation which can help you identify patterns and trends in your data.

### Model
This step includes building your model, iterating with different features to get better accuracy, validate with different validation techniques and train your model.

### Interpret
Interpreting data is one of the most important steps. It refers to presenting your data, the bussines question that needs to be answered, the answer with the visualisation and accountable insights that is found through the process. Interpereting data means creating a clear, easy to understand story from your results for your non-technical audience.


# Data Scrubbing 
Most articles tha I have read says that the magic happens in the modeling part. However, I have figured that the real magic happens after a good data wrangling session. Othervise your magic wand might turn you a frog instead of an awesome dragon.

I will share my data scrubbing journey with you.  It took me 1 week to complete this part. It finalley made sense to me that so many people use  same dataset to do the same task whic is price prediction but receives completely different results. 

Here is how I have done data scrubbing and  feature engineering before jumping on to modelling. 

[https://github.com/fcamuz/dsc-1-final-project-online-ds-sp-000/blob/master/Data%20scrubbing%20.ipynb](http://)












