# Problem Statement
# Predicting Coupon Redemption
XYZ Credit Card company regularly helps it’s merchants understand their data better and take key business decisions accurately by providing machine learning and analytics consulting. ABC is an established Brick & Mortar retailer that frequently conducts marketing campaigns for its diverse product range. As a merchant of XYZ, they have sought XYZ to assist them in their discount marketing process using the power of machine learning. Can you wear the AmExpert hat and help out ABC?
Discount marketing and coupon usage are very widely used promotional techniques to attract new customers and to retain & reinforce loyalty of existing customers. The measurement of a consumer’s propensity towards coupon usage and the prediction of the redemption behaviour are crucial parameters in assessing the effectiveness of a marketing campaign.

ABC’s promotions are shared across various channels including email, notifications, etc. A number of these campaigns include coupon discounts that are offered for a specific product/range of products. The retailer would like the ability to predict whether customers redeem the coupons received across channels, which will enable the retailer’s marketing team to accurately design coupon construct, and develop more precise and targeted marketing strategies.

The data available in this problem contains the following information, including the details of a sample of campaigns and coupons used in previous campaigns -
- User Demographic Details
- Campaign and Coupon Details
- Product Details
- Previous Transactions
Based on previous transaction & performance data from the last 18 campaigns, predict the probability for the next 10 campaigns in the test set for each coupon and customer combination, whether the customer will redeem the coupon or not?

# Dataset Description
Here is the schema for the different data tables available. The detailed data dictionary is provided next.
![Schema Diagram][Schema_Diagram.jpg]

- train.csv - Train data containing the coupons offered to the given customers under the 18 campaigns

|Variable 			  |Definition 					  
|---------------------|---------------------------|
id				  | Unique id for coupon customer impression
campaign_id		  | Unique id for a discount campaign
coupon_id		  | Unique id for a discount coupon
customer_id		  | Unique id for a customer
redemption_status | (target) (0 - Coupon not redeemed, 1 - Coupon redeemed)

- campaign_data.csv - Campaign information for each of the 28 campaigns

|Variable 			  |Definition 					  
|---------------------|---------------------------|
campaign_id		  | Unique id for a discount campaign
campaign_type	  | Anonymised Campaign Type (X,Y)
start_date		  | Campaign Start Date
end_date 		  | Campaign End Date

- coupon_item_mapping.csv - Mapping of coupon and items valid for discount under that coupon

|Variable 			  |Definition 					  
|---------------------|---------------------------|
coupon_id		  | Unique id for a discount coupon
item_id	  		  | Unique id for items for which given coupon is valid

- customer_demographics.csv - Customer demographic information for some customers

|Variable 			  |Definition 					  
|---------------------|---------------------------|
customer_id		  | Unique id for a customer
age_range	  	  | Age range of customer family in years
marital_status    | Married, Single
rented			  | 0 - not rented accommodation, 1 - rented accommodation
family_size		  | No of family members
no_of_children	  | No of children in family
income_bracket    | Label Encoded Income Bracket (Higher income corresponds to higher income)

- customer_transaction_data.csv - Transaction data for all customers for duration of campaigns in the train data

|Variable 			  |Definition 					  
|---------------------|---------------------------|
date		      | Date of Transaction
customer_id	  	  | Unique id for a customer
item_id    		  | Unique id for item
quantity		  | quantity of item bought
selling_price	  | Sales value of the transaction
other_discount	  | Discount from other sources such as manufacturer coupon, loyalty card
coupon_discount   | Discount availed from retailer coupon

item_data.csv - Item information for each item sold by the retailer

|Variable 			  |Definition 					  
|---------------------|---------------------------|
item_id		      | Unique id for item
brand	  	  	  | Unique id for item brand
brand_type    	  | Brand Type(local,Established)
category		  | Item category 

- test.csv - Contains the coupon customer combination for which redemption status is to be predicted

|Variable 			  |Definition 					  
|---------------------|---------------------------|
id		      	  | Unique id for coupon customer impression
campaign_id	  	  | Unique id for discount campaign
coupon_id    	  | Unique id for discount coupon
customer_id		  | Unique id for a customer

# Evaluation Metric
Submissions are evaluated on area under the ROC curve
Note : Here, submission of probabilities of 1's is being used

# Ranking
Public Leaderboard : 290/1021 (0.8652)
Private Leaderboard : 284/1021 (0.8645)