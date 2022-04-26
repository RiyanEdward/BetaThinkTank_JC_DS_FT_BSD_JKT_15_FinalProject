# BetaThinkTank_JC_DS_FT_BSD_JKT_15_FinalProject

### Created By : Beta ThinkTank
Repository ini merupakan salah satu proses dari program Bootcamp Data Science Purwadhika Digital School ini, dan disusun oleh tim Beta ThinkTank yang ber anggotakan :
1. Cristopher Gani
2. Riyan Rafif
3. Rifqi Manufi

Dataset source : https://www.kaggle.com/olistbr/brazilian-ecommerce?select=olist_products_dataset.csv

## Who, What, How?
Olist is a Brazilian company engaged in E-commerce. The company is currently planning to improve sales performance by determining the marketing methods provided to customers with different needs, characteristics or behaviors. The company has a dataset of every transaction in this E-commerce. we as data scientists at the Olist company have a role to provide insight and recommendations from the dataset, so that the company can continue to grow.
The company wants to improve sales performance with effective and efficient marketing methods, so Customer Segmentation is needed. Therefore, the steps we need to do first are business understanding, data cleaning and preparation, data overview, EDA and insight, model and evaluation, business insight and recommendations.

## Business Understanding
In the business understanding step, we want to understand the business problems that the company has and determine the purpose of the results of this analysis.
  To understand the business problem, we conducted a cohort analysis, which is a method used to analyze and evaluate changes in the behavior of a certain group of people, involving general demographic features over a certain period of time.
From the results of the cohort analysis, we can see that a group of new users almost every month no more than 1% who make purchases again in the following month, except in December 2016 and even then because the number of new customers in that month is only 1 person and that person makes a purchase. back in the following month.
Of the 91,445 customers, 94% do not make repeat purchases.
![cohortAnalysis](https://user-images.githubusercontent.com/94157150/162120110-9fda69bb-3ceb-4363-bced-8bf983b2d734.png)

## Goals and Strategy
After knowing the business problem, we can target our goals, namely:
1. Increase repurchasing and also to minimize potential lost customers.
2. Perform customer segmentation using RFM analysis and create a clustering model to predict the targeted cluster.
3. Provide insights and recommendations that can help the business team and marketing team to improve repurchasing.

## Data Overview
The Olist Ecommerce data that we analyze comes from Kaggle, this data consists of 8 different data sets. After we do the process of merging or merging between datasets according to the instructions from this schema data set, there are 44 columns and 119,143 rows.
![alt text](https://i.imgur.com/HRhd2Y0.png)

## Data Preprocess and Cleaning
 Now we enter the process of data cleaning and data preprocessing, at this stage we will clean the data, select the columns to use and prepare the data for clustering purposes.
 the following is the cleaning and preprocessing process:
 1. Handling Missing values ​​-> Drop, because the missing values ​​between the columns are correlated and the data type of the missing value is a timestamp data type so it is difficult to fill in the missing value.
 2. Check & remove Duplicate -> 15,256 -> Drop, because it can interfere with the customer's payment value.
 3. Handling outliers -> No treatment is carried out, because we think that in this dataset the outliers can provide good insight, not interfere with the analysis.

## Data Selected
After merging the datasets, we select 20 columns from customer data, payment data, seller data and location data. Although to do market segmentation we only need data related to customers, here we decided to enter seller and location data to be able to provide additional insight to us.
<img width="661" alt="Screen Shot 2022-04-07 at 12 17 21" src="https://user-images.githubusercontent.com/94157150/162125544-1260511c-c4c2-499b-b0a9-9dc4452d82bb .png">


## Data Overview and EDA
After going through the cleaning process, our data is ready to be used, at the Overview, EDA and Insight data stages, we will describe the results of the analysis we have done.

### Sales Overview

![Sales Overview](https://user-images.githubusercontent.com/94157150/162125819-1bd59c0e-db5a-4320-9874-87ffc3e67aa4.jpeg)

In this sales overview, we can see purchase traffic based on the day and hour, from this heatmap it shows that the highest purchase traffic on ecommerce olist is on weekdays from 10 am to 4 pm, even though at 5 pm to night the purchase traffic is still pretty high. We can assume that the cause of purchase traffic on weekends is lower than weekdays because on Saturdays and Sundays people prefer to shop at offline stores.
Next we can see the number of transactions, and the number of payments each month from this data is directly proportional, the trend of the two data is positive. The largest number of transactions and payments were both in November 2017.
The payment methods available are boleto, cc, debit, and vouchers. 74% of the payment methods used are credit cards.

The average review score given by the customer to the seller is quite good with an average score of 4.1 out of 5. This shows that basically the majority of customers are quite satisfied with the goods they buy.

If we look at the number of customers and the number of sellers, it can be assumed that each seller only gets 32 customers. The total payment transactions are 15.1 million reals, and the total of all products is 30.2 thousand. If we look again at the majority of payment methods using credit cards, as many as 50.5% of customers at olist make payments in installments.

### State
![Geolocation](https://user-images.githubusercontent.com/94157150/162126806-e48c3cd2-3f1c-4cdc-983b-1f8d300a8522.jpeg)

This is a map of the location of the seller state and customer state. We can see from the seller and the customer the population is mostly in Sao Paulo. From our analysis results show that 64% of transactions place orders between different states. Maybe it happened because the goods they wanted were not available in their area even though it could not be validated because there was no data that specifically explained what products were purchased but only in the form of categories.

### Delivery
![Delivery Overview](https://user-images.githubusercontent.com/94157150/162127719-f492bb36-739e-44f7-ada1-de3f4579e47e.jpeg)

Next, we analyze the shipping data, the most shipping routes are from saopaulo to saopaulo, but according to the previous state data, 7 out of 10 shipping routes are mostly to different states.
When viewed from the delivery time, 7 out of 10 fastest delivery times are deliveries to the same state. While the 10 longest delivery times are deliveries to different states, there is even a delivery time that reaches 138 days. The average duration of delivery is 9 days while the estimate is 21 days, maybe the length of delivery time and estimates also support our previous analysis results that 64% of shipments are interstate because if the goods are available in their area, they will choose to go to the store physical rather than having to wait a long time, what's more, the estimate given is on average 2 times longer than the average actual delivery.
Our analysis shows that deliveries that do not match the estimates reach 98.7%, although the proportion of deliveries that are longer than the estimate is only 6.6%, but there are 74% estimates that are more than 7 days compared to the actual. Estimated delivery that is too long can cause a decrease in buyer interest even though the delivery time can be much faster.

### Categories
![Best Category Product](https://user-images.githubusercontent.com/94157150/162127812-acbbcdfe-9f98-4b03-a965-ac018798654d.jpeg)

These are the 35 categories with the highest sales, the majority of these categories are goods that are not repurchased in the near future, while in this data only for a period of 22 months. This may be the cause of 94% of customer lists in this data not making repeat purchases. If it is related to the previous analysis that 64% of transactions are carried out between states, causing the delivery time to be long, for goods whose purchases are repeatable such as food, drinks, or items that are needed as soon as possible, making customers hesitate to shop at olis . So it is possible that the goods purchased at Olist are goods that are not available in the area or are difficult to find, making them willing to wait a long time.


## Model
  Next, create a model for customer segmentation and evaluation of the model. Clustering is made to group customers based on their behavior so that we can determine which group will be our main target to increase sales in this e-commerce.
First of all we have to prepare the data before creating the model, starting from creating the RFM feature, then combining it with the features that we have selected from the dataframe, going to the scaling stage using a standard scaler and reducing the dimensions of the data using PCA with N component 2.

We made the first 4 models, namely using selected features with the KMeans model, the second is RFM Segmentation, the third is RFM features with the KMeans model, the last model is combining the selected features with RFM features with the kmeans model.
The selected features are:
* order_item_id
*price
*freight_value
*Payment_value
* payment_sequential
* payment_installments

We chose the fourth model, which is a model that uses optional features and RFM features, the number of clusters chosen is 4 because the results of the clustering can interpret our goals. Sillhouette score of this model is 0.74

## Clustering Results
![WhatsApp Image 2022-04-07 at 12 21 31 PM](https://user-images.githubusercontent.com/94157150/162128041-d9252b16-af16-4c89-8ee8-dfaad4718f4b.jpeg)

This is the result of the clustering. The first cluster is Big Spender, which is a group of customers who buy goods with a small quantity, a little frequency, but make a fairly large payment, on average from this cluster also make installments when buying goods.
The second is Hibernating, which is a group of customers who buy goods with a small quantity, a small frequency, and a small amount of payment.
The third is Loyal Customers, namely groups of customers who buy goods in large quantities, the frequency is also a lot, with a moderate amount of payment.
The last one is Need attention, which is a group of customers who buy goods with moderate quantity, frequency and amount of payment.

From the results of clustering, we know that the cluster with the highest proportion of 89% is Hibernating, so that the cluster is our target segment and is supported by the connectedness of the problems resulting from the cohort analysis which shows 94% of customers do not make repeat purchases. According to F.F Reichheld (1996) "a company is very important to satisfy and retain existing customers because finding new customers can cost up to five times greater than the cost to satisfy and retain customers".

## Business Insight, recommendation
From the results of the analysis and clustering results, also based on Frederick Reichheld's statement, we should make improvements to the problems of delivery and availability of goods in each state to withdraw the hibernating cluster, before trying to create a campaign to attract new users who will later have the same experience with old user.

1. Recommendations For business team

For the business team, we recommend making improvements in the shipping sector by partnering with quality shipping services so that the estimation and delivery speed are better. The second is to make warehousing in various states because in addition to faster delivery, warehousing can also make the availability of goods more evenly distributed in each state.
We also recommend asking for user feedback, such as a short survey on what needs to be changed to get a better experience when making transactions.

2. Recommendations for the marketing team

First, we suggest that the marketing team create a campaign to increase the number of sellers by providing education and benefits when they entrust their business to Olist. Because by increasing the number of sellers, it is hoped that the availability of goods will be more evenly distributed so that the delivery of goods will be faster and can withdraw the hibernating cluster. The second is doing A/B testing for hibernating clusters by comparing the behavior of the cluster by providing sales promotions such as 0% installments because 50% of customers make transactions in installments. We can also provide free shipping promos so that the delivery time can be considered.

## Conclusion
from the problem that 94% of customers at olist do not repurchase, we have provided recommendations aimed at our target cluster, namely the agar hibernating cluster. The expected goal, of course, is to increase repurchasing by attracting back buying interest from the hibernating cluster. To see the impact of our recommendations and analysis, we can use the A/B testing method and analyze the results of feedback provided by customers.
