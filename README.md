## Customer Segmentation with Cluster Analysis

Customer segmentation is a crucial aspect of marketing strategy that involves dividing a customer base into distinct groups with similar characteristics or behaviors. This allows businesses to tailor their marketing efforts, products, and services to better meet the needs of each group. When writing a problem statement for a customer segmentation project, it's essential to focus on the specific goals, challenges, and desired outcomes of the segmentation effort. 
For example, instead of spending money to market a new product to every customer in the company’s database, a company can analyze which customer segment is most likely to buy the product and then market the product only on that particular segment.

### Problem statement:
Here we used a dataset that contains data collected from a marketing campaign of a local shopping mart, where our task is to predict how different customer segments will respond for a particular product or service.

### Attributes:

#### People Columns:

ID: Customer's unique identifier

Year_Birth: Customer's birth year

Education: Customer's education level

Marital_Status: Customer's marital status

Income: Customer's yearly household income

Kidhome: Number of children in customer's household

Teenhome: Number of teenagers in customer's household

Dt_Customer: Date of customer's enrollment with the company

Recency: Number of days since customer's last purchase

Complain: 1 if the customer complained in the last 2 years, 0 otherwise

Products Columns: These columns represent a customer's total spending on a specific product. To check their data type so that I create a new column "Spending" that's their summation.

MntWines: Amount spent on wine in last 2 years

MntFruits: Amount spent on fruits in last 2 years

MntMeatProducts: Amount spent on meat in last 2 years

MntFishProducts: Amount spent on fish in last 2 years

MntSweetProducts: Amount spent on sweets in last 2 years

MntGoldProds: Amount spent on gold in last 2 years

#### Promotion Columns:

NumDealsPurchases: Number of purchases made with a discount

AcceptedCmp1: 1 if customer accepted the offer in the 1st campaign, 0 otherwise

AcceptedCmp2: 1 if customer accepted the offer in the 2nd campaign, 0 otherwise

AcceptedCmp3: 1 if customer accepted the offer in the 3rd campaign, 0 otherwise

AcceptedCmp4: 1 if customer accepted the offer in the 4th campaign, 0 otherwise

AcceptedCmp5: 1 if customer accepted the offer in the 5th campaign, 0 otherwise

Response: 1 if customer accepted the offer in the last campaign, 0 otherwise

#### Place Columns:
NumWebPurchases: Number of purchases made through the company’s website

NumCatalogPurchases: Number of purchases made using a catalogue

NumStorePurchases: Number of purchases made directly in stores

NumWebVisitsMonth: Number of visits to company’s website in the last month

### Objective:
Need to perform clustering to summarize customer segments.

### Data cleaning and pre-processing for Customer Personality Analysis:
Data cleaning and preprocessing are crucial steps in any data analysis or machine learning project. These steps ensure that the data is accurate, consistent, and suitable for analysis. Here’s a comprehensive summary of data cleaning and pre-processing, including definitions, steps, techniques, and best practices.

In the dataset used, there were quite a few missing values and outliers , incorrect data types ,Categorical Inconsistencies, Irrelevant Data, etc.

From the observations in the dataset, we were able to conclude and note that:
There are missing values in “income”
Dt_Customer that indicates the date a customer joined the database is not parsed as DateTime
There are some categorical features in our data frame; as there are some features in dtype: object). So we will need to encode them into numeric forms later.
Feature engineering new columns to increase Interpretability.


### DATA PREPROCESSING:
In this section, we preprocessed the data to perform clustering operations.
The following steps were applied to preprocess the data:
Label encoding the categorical features.
Scaling the features using the standard scaler.
Creating a subset dataframe for dimensionality reduction with PCA.
All the features were scaled and the data was cleaned and preprocessed properly to gain help with better interpretation.To handle outliers we opted for the Interquartile Range (IQR) method. IQR is the range between the first quartile (Q1) and the third quartile (Q3). Outliers are often defined as points that fall below Q1 - 1.5 * IQR or above Q3 + 1.5 * IQR. To reduce complexity of the data , we derived new columns like- “Age”, “Childrens”, “Spendings” by aggregating available features.

### DIMENSIONALITY REDUCTION:
In this problem, there are many factors on the basis of which the final classification will be done. These factors are basically attributes or features. The higher the number of features, the harder it is to work with it. Many of these features are correlated, and hence redundant. This is why we will be performing dimensionality reduction on the selected features before putting them through a classifier.
Dimensionality reduction is the process of reducing the number of random variables under consideration, by obtaining a set of principal variables.

**Principal component analysis (PCA)** is a technique for reducing the dimensionality of such datasets, increasing interpretability but at the same time minimizing information loss.

Steps used:

-Dimensionality reduction with PCA: For this project, I will be reducing the dimensions to 3.

-Plotting the reduced dataframe

![Screenshot 2024-07-26 001249](https://github.com/user-attachments/assets/c688b2b7-1e4f-4d11-a08e-491b1d53ffc3)

                    Fig : Reducing dimensionality


### CLUSTERING:
Now that we have reduced the attributes to three dimensions, we will be performing agglomerative clustering. Agglomerative clustering is a hierarchical clustering method. It involves merging examples until the desired number of clusters is achieved.

Steps involved in the Clustering:

-Elbow Method to determine the number of clusters to be formed

-Clustering via Agglomerative Clustering

-Examining the clusters formed via scatter plot

![Screenshot 2024-07-26 002804](https://github.com/user-attachments/assets/f8eacf86-0a59-4aca-86b4-951b558c4555)

     Fig 1: The above cell indicates that 4 will be an optimal number of clusters for this data. 


![Screenshot 2024-07-26 004550](https://github.com/user-attachments/assets/510c002b-4775-4d11-baa3-20244a5d2a62)
     Fig 2:  fitting the Agglomerative Clustering Model to get the final clusters.


### EVALUATING CLUSTER ANALYSIS MODEL: 
Since this is an unsupervised clustering , we do not have a tagged feature to evaluate or score our model. The purpose of this section is to study the patterns in the clusters formed and determine the nature of the clusters' patterns.For that, we will be having a look at the data in light of clusters via exploratory data analysis and drawing conclusions.
The clusters seem to be evenly distributed and a co-linear relationship exists between Income and Spendings.

![Screenshot 2024-07-26 011147](https://github.com/user-attachments/assets/c0301040-1874-46ff-bdb8-a00d2b59d630)

     Fig 3: Co-linear relationship between Income & Spending variables


![Screenshot 2024-07-26 011737](https://github.com/user-attachments/assets/0585c480-b8d8-45d2-8a31-dd890dd696a5)
     Fig 4: Distribution of cluster 


From the above figures, we can interpret that Income vs spending plot shows the following pattern:

-group 0: average income & low spending

-group 1: high income & high spending 

-group 2: high spending & medium income

-group 3: Medium-low income & low spending

**Correlation Between Features and Clusters:**

We looked at the detailed distribution of clusters as per the various products in the data namely: Wines, Fruits, Meat, Fish, Sweets and Gold

![Screenshot 2024-07-26 022422](https://github.com/user-attachments/assets/0d8a40fa-cd22-48f5-95c7-3b5c2e99c7ec)

    Fig 5: Distribution of customer spendings

From fig 5, it can be clearly seen that cluster 1 is our biggest set of customers closely followed by cluster 2. We can explore what each cluster is spending on for the targeted marketing strategies.

![Screenshot 2024-07-26 024038](https://github.com/user-attachments/assets/a91f3db2-6c37-4413-afeb-6821a1af044a)
    Fig 6: Promotion acceptance distribution

As per fig 6, there has not been a good response to the campaigns so far. Very few participants overall. Moreover, no one part takes in all 5 of them. Perhaps better-targeted and well-planned campaigns are required to boost sales.

![Screenshot 2024-07-26 025208](https://github.com/user-attachments/assets/53533643-ce38-4621-a22d-823fda597bb5)

    Fig 7:  Number of purchases made with a discount

As per fig 7, Unlike campaigns, the deals offered did well. It has the best outcome with cluster 3. However, our star customers cluster 1 are not much into the deals. Nothing seems to attract cluster 2 overwhelmingly

![Screenshot 2024-07-26 030008](https://github.com/user-attachments/assets/154b1e52-0df8-4c18-9cc6-07b42f0ead18) 

    Fig 8:  Distribution of customer income

As per the Fig 8, Cluster 0 is mostly characterized by low income.Cluster 2  is mostly characterized by medium income.Cluster 1 is characterized by high income.Cluster 3 is mostly characterized by medium-low income


![Screenshot 2024-07-26 031328](https://github.com/user-attachments/assets/a570e918-55ee-46d5-ae04-9a7decff2645)
    Fig 9:   Purchases made through the company’s website

As per Fig 9, Clusters 3 and 0 mostly characterized by higher number of visits.Clusters 1 is characterized by lower number of visits and Cluster 2 is characterized as average visits.


![Screenshot 2024-07-26 032123](https://github.com/user-attachments/assets/9d816831-25a6-4420-a295-9a2db2919f6f)

    Fig 10:   Sales conversion on 5th campaign

As per Fig 10, Clusters 0 and 3 didn't accept campaign 5. While 1/3 of Cluster 1 accepted it and most Cluster 2 didn't accept it.

![Screenshot 2024-07-26 032909](https://github.com/user-attachments/assets/8dcc6fa6-5e8c-42db-9f45-6613e72defde)

    Fig 11: Customers with childrens

As per Fig 11, Cluster 0 & 2 mostly has 1 kid.Cluster 1 mostly has 0 kids. Cluster 3 mostly has 1 or 2 kids.

### Conclusion:
Our cluster analysis revealed four distinct customer segments, each with unique characteristics. The segments are differentiated by their spending habits, income levels, and purchasing behavior.

*Segmentation Overview:*

**Frugal Families (Cluster 0):** Low spenders with average income, characterized by fewer store and catalog purchases, frequent visits, and a higher likelihood of having 1 kid. They tend to reject campaign 5.

**High-Rolling Singles (Cluster 1):** High spenders with high income, characterized by lower visit frequencies, a higher acceptance of campaigns 1 and 5, and a majority having no kids.

**Aspirational Families (Cluster 2):** Medium-high spenders with medium-high income, with purchasing behavior similar to Clusters 0 and 1, but with a lower acceptance of campaigns and a majority having 0-1 kids.

**Middle-Income Moderates (Cluster 3):** Medium-low spenders with medium-low income, similar to Cluster 0 in terms of purchasing behavior, but with a slightly higher acceptance of campaigns.

These segments provide valuable insights for targeted marketing strategies, allowing businesses to tailor their campaigns and promotions to specific customer groups.
