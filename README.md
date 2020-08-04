# Yelp: Predicting Restaurants' Success Based on Foot Traffic and Attribute Patterns.
The purpose of the **json_to_csv** notebook is to gather data from the [Yelp website](https://www.yelp.com/dataset), and convert it into a more usable format. The original dataset is nearly 10GB of JSON files. Since for the scope of this project we are only interested in restaurant data, we are going to convert the files into csv format, and make relevant merges and deletions, in order to make the analysis more memory-efficient. These files will be utilized in the next notebook for exploratory data analysis and modeling. <br>
The purpose of the **EDA** notebook is exploratory data analysis. Data is cleaned, preprocessed, and the sample space is reduced to first U.S. restaurants only, and then Las Vegas restaurants. Here we discover trends and patterns in our data, as well as creating some visuals to illustrate them. In this notebook I dive into feature engineering as well. <br>
In the **Modeling** notebook we work on some predictive modeling. Here we dive into Logistic regression, KNN, SVM and Random Forest. <br>
**Note:** code for the SVM chapter is borrowed from [@jasontdean]('http://jasontdean.com/python/Yelp.html')
**************************************
Yelp Dataset comes with 5 json files: business, checkin, user, review and tip. We convert them into the csv files. for further cleaning and EDA. <br>
*************************************
**Glossary of df names:** <br>
* **df_business:** yelp's business.json. Contains business_id, name, geo info, stars, review count, attributes, categories and hours. Also exists as *'business_yelp.csv'*.
* **restaurant_df:** created by me, filtered for restaurants that are open. Contains same columns as business, minus the hours. Also exists in csv: *'restaurant_bus_yelp.csv'*.
* **df_user:** yelp's user.json. Not yet filtered for restaurants! Nearly 2 million users listed, so it will have to be merged with other df in order to distinguish restaurants. Also exists as *'user_yelp.csv'*.
* **review.json:** currently *work in progress*. Might not use for this project. It's nearly 6GB. Definitely needs to be reduced and normalized.
* **df_checkin:** yelp's checkin.json. With "total" column added.
* **restaurant_checkin_df** restaurant_df + df_checkin, merged on business_id. Also exists as 'restaurant_checkin.csv'.
* **df_tip:** yelp's tip.json. Contains user_id, business_id, text of the tip, date	and compliment_count.
*************************************
**Note:** Not all the df's mentioned above will be used in the analysis. In fact, the df that we use for modeling will be created in the EDA notebook. The df's from the glossary are just here for exporatory purposes. <br>

The data needed some cleaning, filtering and merging. <br> 
***************************************************************************************************************
**First**, I created the **restaurant_df** out of the business.json file. Eliminated businesses that aren't restaurants, and only kept the restaurants that are open. This file exists as *'restaurant_bus_yelp.csv'*. <br>
***************************************************************************************************************
**Next**, I created the **restaurant_checkin_df** by merging restaurant_df with df_checkin on business_id. This file exists as *'restaurant_checkin.csv'*. It contains business, geolocation, attribute and foot traffic info for 43,039 restaurants.
