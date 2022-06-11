# Customer_Segmentation_Kmeans
Customer Segementation using KMeans
**Description and Motivation**
Welcome to my retail customer segmentation project! We are going to analyze the data of a retail company, and try to understand the behavior of their customers. Hopefully, we’ll find a lot of insights to help the company on how to plan their next campaigns, who would be the target of a new product, what are the most valuable customers, etc.
It contains information of 2240 customers, with 29 attributes each. These attributes are: 
**People**
- ID: Customer's unique identifier
- Year_Birth: Customer's birth year
- Education: Customer's education level
- Marital_Status: Customer's marital status
- Income: Customer's yearly household income
- Kidhome: Number of children in customer's household
- Teenhome: Number of teenagers in customer's household
- Dt_Customer: Date of customer's enrollment with the company
- Recency: Number of days since customer's last purchase
- Complain: 1 if the customer complained in the last 2 years, 0 otherwise

**Products**

- MntWines: Amount spent on wine in last 2 years
- MntFruits: Amount spent on fruits in last 2 years
- MntMeatProducts: Amount spent on meat in last 2 years
- MntFishProducts: Amount spent on fish in last 2 years
- MntSweetProducts: Amount spent on sweets in last 2 years
- MntGoldProds: Amount spent on gold in last 2 years

**Promotion**

- NumDealsPurchases: Number of purchases made with a discount
- AcceptedCmp1: 1 if customer accepted the offer in the 1st campaign, 0 otherwise
- AcceptedCmp2: 1 if customer accepted the offer in the 2nd campaign, 0 otherwise
- AcceptedCmp3: 1 if customer accepted the offer in the 3rd campaign, 0 otherwise
- AcceptedCmp4: 1 if customer accepted the offer in the 4th campaign, 0 otherwise
- AcceptedCmp5: 1 if customer accepted the offer in the 5th campaign, 0 otherwise
- Response: 1 if customer accepted the offer in the last campaign, 0 otherwise

**Place**

- NumWebPurchases: Number of purchases made through the company’s website
- NumCatalogPurchases: Number of purchases made using a catalogue
- NumStorePurchases: Number of purchases made directly in stores
- NumWebVisitsMonth: Number of visits to company’s website in the last month

**Data Preprocessing**

**Removing Null**
1)We had 24 null values in the “income” feature, it is replaced with median as this feature has outlier
2) "Z_CostContact" and "Z_Revenue" have same value in all the rows that's why 
they are not going to contribute anything in the model building. So we can drop them.
3)columns are renamed

**Feature Engineering**
Creating new features
1)Percentage of purchases made with discount.
2)Percentage of value spent on essential items (fruits + meat + fish + sweet)
3)total_spent = mnt_wines + mnt_fruits+ mnt_meat+ mnt_fish + mtn_sweet + mnt_gold
4)num_purchases= num_web_purchases+ num_catalog_purchases + num_store_purchases + num_web_visits_month 
5) num_children =  kid_home  + teen_home
6) days_since_enrollment  
7) age 

**Removing outliers**
1)We have removed some customers that have extreme values, and are not in pace with the others from Income and age
2)he new dataset have 2236 rows. Only 4 customers were removed in this process.

**Regrouping Categorical Values**
Here is our problem: The feature containing the relationship status and the education, have a lot of categories and some of them are very similar to each other. It makes sense to regroup them, to make the analysis easier:

In the relationship feature, we are going to have 2 groups: people who have a partner, and peoples who don’t.
In the education feature, we are going to have 3 groups: Undergraduate, Graduated, and Postgraduate.

**Exploratory Data Analysis**
We had closer look at our features, their distributions, and how they relate to each other between Categorical Features,Continuous Features,Relation between variables

**Applying K means ML model**
1)Scaling the data
2)have done PCA (components =4)
3)Optimal K determination by Elbow Method (K=3)& silhouette score (K=3)
4)Applied K mean unsupervised ML model

**Insights**
1)People from cluster 2 buy items at full price, and spend a lot of money. Therefore, they are our most valuable customers. The company should make an extra effort to keep them happy.***

2)People in cluster 3 buy a lot of non-essential items, and are very sensitive to discounts.

3)On the other hand, people in cluster 1 don’t respond very well to discounts. Therefore, it might be a good idea to concentrate efforts to send special offers to the people in cluster 3 (and don’t send so much to cluster 2).
