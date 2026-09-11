# K-means-clustering
K-means clustering to group customers based on their purchase behavior

### Objective
To group the customers based on their RFM (Recency, Frequency, and Monetary). The result can later be used for targeted marketing.

### Data
The analysis is using the sales data from a small retail shop on a year period from 1 July 2025 - 30 June 2026. Consist of 13751 rows of data, each row contains:
  <details>
<summary>Show columns</summary>

| Column | Description |
|---|---|
| `order_no` | Unique order number generated automatically |
| `order_date` | Date of the transaction |
| `order_time` | Time of the transaction |
| `order_source` | Source of order: Mobile app, online website, or Point of Sales (cashier) |
| `sales_name` | Cashier's name |
| `customer_id` | Unique customer's identifier |
| `customer_type` | type of customers |
| `customer_name` | Customer's name |
| `customer_phone` | Customer's phone number |
| `total_qty` | Total quantity in a single transaction |
| `currency` | Type of currency used in the transaction |
| `subtotal` | Amount of purchase before discounts |
| `discount_name` | Type of discount if applicable |
| `discount_code` | Discount's code |
| `discount` | Discounted amount |
| `redeemed` | Amount of promotion vouchers redeemed |
| `total_amount` | Purchase amount after discounts |
| `product_cost` | Base cost of product |
| `gross_profit` | Sale profit |
| `payment_mode` | Payment method: Shopee, Cash, QRIS, Debit, Bank Transfer, COD |
| `payment_amount` | Amount paid in a transaction |
| `payment_date` | Date of payment |

</details>
Note: Due to confidentiality, the sales data will not be included

### Tools
  1. Excel
  2. Language: Python
  3. Libraries: Pandas, Matplotlib, Seaborn, Numpy, Scikit-learn

### Methodology
  1.	Data gathering
  2.	Data cleaning
  
  Rows containing missing data is deleted. In this case, any purchases made by non shop members is deleted since no customer name will be recorded. 

  3.	RFM Feature engineering
  
  Utilizing the pivot table, the data is turned to show the RFM features:

  Recency: substract the latest purchase date of a customer from the set current date
  
  Frequency: count the number of purchases made by each customer
  
  Monetary: calculate the total amount of purchase from each customer

  4.	Data transform
  
  It is common for data to be skewed in their distribution due to outliers. But in this case, removing outliers might be not an option because it indicates customers with very high purchase amount and frequency. Keeping them as they are is also not possible because K-means clustering is highly sensitive to extreme values.
  
  Log transforming is one of the common method to address skewed distribution. This makes the extreme data have lesser influence to the clustering process then before.

  5.	Feature scaling
  
  Since K-means clustering calculates the distance between data points, different scales between the RFM features will makes the result disproportional. Scaling levels the weight between features so each will have roughly the same influence.

  6.	Engage K-means Clustering

### Analysis

1. Choosing the number of clusters

       According to the Elbow method and Silhouette score graph, the best number of clusters are either 3 or 4 under these considerations:
          •	The inertia graph suggest that using more then 4 clusters reduce insignificant number of inertia.
          •	The Silhouette score graph imply that more then 5 clusters greatly reduce the score.
          •	Although using only 2 clusters produces a high Silhouette score, it also generate a great inertia.

2. Comparing after-clustering result

  Using 3 clusters results in these output:
  
        •	Customers are divided into 3 clusters: 
          a.	Cluster 0 for recently purchasing, high frequency and spending customers.
          b.	Cluster 1 for recently purchasing, low frequency, low spending customers. 
          c.	Cluster 2 for inactive, low frequency, and low spending customers.

  Meanwhile, using 4 clusters result in:
  
        •	Customers are grouped into 4 clusters:
          a.	Cluster 0: recently buying, low frequency, low spending.
          b.	Cluster 1: recently buying, low frequency, high spending.
          c.	Cluster 2: haven’t buying for a while, low frequency, low-medium spending
          d.	Cluster 3: low-medium recency, medium frequency, low-medium spending

  Using 4 clusters provide a more detailed, smaller clusters than 3 clusters. 

    According to the 3 clusters pairplot, some customers from cluster 2 spend as much as cluster 0, just not as recent
    Using 4 clusters divide some of them into a new group
    Because the result will be used as the base for targeted promotion campaign, those old high spenders are still appealing to target
    Considering the data came from a small retail shop with limited marketing budget, high campaign efficiency is a priority

  For those reasons, 4 clusters are the most ideal number for grouping the customers based on their behaviour
