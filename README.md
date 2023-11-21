# RFV-Analysic

The idea in this project is to analyze the RFV (Recency, Frequency, Value) of customers using sales of an e-commerce and the K-Means clustering algorithm. 

The data used here can be found at Kaggle, here: https://www.kaggle.com/datasets/gabrielramos87/an-online-shop-business

After a brief exploratory data analysis, I use K-Means to cluster customers so I can get a better understanding of how the RFV divides them.

My approach is as follows:
1. Run the algorithm with 1 up to 5 clusters on the standardized data
2. Use the elbow method to try to identity the optimal number of clusters. It seemed to me that 2, 3 or 4 could be good candidates
3. Rerun the algorithm with 2, 3 and 4 clusters and analyze the centroid of each cluster in each algorithm

From that, and using some business arguments, I decided that the algorithm with 3 clusters was the best one. It separated the data in a useful way for the business. 

Below I show the centroids of each cluster in the 3-cluster algorithm and discuss some insights from them.

| Cluster | Customers | Recency | Frequency | Value | Label |
| ------- |  -------  | ------- | -------   |  ---- | ----- |
|    1    |    17     |  23.06  | 2111.41   | $715,010 | Premium customers
|    2    | 1274      | 244.36  | 46.34     | $3,795 | Possible churn
|    3    | 3427      | 41.20   | 126.30    | $13,415 | Core customers

The table above show average values for all customers in each cluster. The recency columns represents the average number of days since the last purchase of customers. The frequency column represents the average number of purchases customers made in the period considered (from Dec 2018 to Dec 2019). And the value represents the average amount of money spent customers in the period. I also added a label column which I believe represent a general idea of the customers in each cluster.

**Cluster 1**:

In the first cluster, we have is the same as the last one in the 2 clusters case. These are recurrent customers (low recency and very high frequency), but they also spend a lot of money on the store. They represent ~20% of the total sales, so we want to keep them engaged in the store. Since there are so few of them, it is easy to personalize the marketing approach to each one of them.

**Cluster 2**:

Second cluster shows customers with high recency, low frequency and low value. These are customers who have not bought anything in a long time and they are not frequent buyers. They will likely churn eventually. And, when they do buy, they do not spend much. They represent ~7% in total sales. Business do not want to lose them, but I wouldn't say they are a priority (unless we do not need to do anything to keep other customers engaged).

**Cluster 3**:

Last cluster shows customers that buy frequently (low recency and moderate frequency) and spend a moderate amount of money. This group represents ~73%.These customers are the ones we want to keep engaged in the store, since they represent the majority of the sales. We could monitor the activity of these customers in the platform to see if they mantain the same pattern displayed here or if they need to be re-engaged in some way.
