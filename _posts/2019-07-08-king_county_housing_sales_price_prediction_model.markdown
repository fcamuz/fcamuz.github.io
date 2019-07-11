---
layout: post
title:      "King County Housing Sales Price Prediction Model"
date:       2019-07-08 16:03:33 -0400
permalink:  king_county_housing_sales_price_prediction_model
---


I have done my first linear regression model project. It was a long journey starting from learning Python and its libraries  to combining them with data analysing methods. I have used OSEMN methodoly to complete this project.  OSEMN is an acronym that represents Obtain, Scrub, Explore, Model, and iNterpret steps. Let me explain each step briefly.

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



Most articles that I have read says that the magic happens in the modeling part. However, I have figured that the real magic happens after a good data wrangling session. Othervise your magic wand might turn your model in to a frog instead of a dragon.

I will share my data scrubbing journey with you.  It took me 1 week to complete this part. It finally made sense to me why so many people use  same dataset to do the same task which is price prediction but receives completely different results. 

The hardest part for me figuring out where to start and what to do next.  I finally came up with an order after so many trial and fail sessions. Here is the roadmap that I have used in data scrubbing and feature engineering before jumping in to modelling. 

### Unnecessary colums

Get rid of unnecessary columns for your model.   I deleted id column.

### Null Values

I use .isna()  method to see if the value is null in the row.  Also .isna().sum() gives the total number of null values in each columns. 

view, waterfront and yr_renovated have null values.   

I have used .value_counts()  method and histogram plot to see their unique values and their counts and also their distribution.  I also use .unique() to see the list of unique values in columns.

for view and waterfront, most of the values are zero. So, converting all null values in to "0" does not hurt the model. I filled all the null values with 0s.

for yr_renovated, it is a similar case. Too many 0s and some years indicating the year of renovation for the house. When I plot histiogram, total number of zeros are about 30 times more than total number of renovated house. So again, it is vice decision to convert null values in to ''0" . Also for the years renovated, I convert all the year values in to '1' indicating the house was renovated. It will save a lot of extra features that will go through the modeling.  

### Place Holders

sq_basement has a '?' for 454 value. to fix this, I have used a holistic approach to see if the other columns would have infirmation to fill these values.  I made and assumption that,  sq_basement is the differenec between sqft_living and sqft_above. I checked this assumption on the available data and confirmed that it is correct so, I filled the entire colums as: sq_basement values = sqft_living -  sqft_above. 

Then I plotted and saw the number of 0s are so big  again for the sake of keeping the number of features small, I converted the data 0s and 1s indicating the house has a basement or not.  

### Correlation

I checked correlation matrix to see if there is any column that I need to drop. There was strong correlation between sqft_above, bathrooms and sqft_living. I will drop sqft_above because sqft_living might be more handy for further analysis


I also checkd the correlation  of all features with the "price" and sorted. 

df.corr()['price'].sort_values(ascending=False)

The correlation between price and zipcode is negative, so I want to drop zipcode as well.
​
### Binning ( yr_built, lat, long  )

I created 5 bins to create 4 categories for yr_built.  I used for loop to create 10 bins for latitude and longtitude. 

### Data Types
I converted nine features to category type.  
'yr_built','condition','long','lat','waterfront','floors','view', 'bedrooms','sqft_basement'
I put them in to a list and do this task in a loop.

### One-Hot-Encoding

Using the same list, i created dummies, added them to a dataframe and dropped the original columns. The new data frame is df_cat representing categorical features.

### Scaling & Normalization

I used quantile transformation from sklearn.preprocessing library for continues features to fix skewness and scaling them.

'price','sqft_living','sqft_lot','sqft_living15','sqft_lot15'

I also created a different dataframe for transformed features so that I can still have access to the original data in the original dataframe. 

Please note that I have done the Exploaration step right after place holders part. You do not want to do a lot of feature engineering before doing the exploation step because you can get much better insight from the raw data.  

So, I hope this post help you for figuring out your road map for data scrubbing step in your project. 

Thanks for reading. 

