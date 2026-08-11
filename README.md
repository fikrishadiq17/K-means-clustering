# K-means-clustering
K-means clustering to group customers based on their purchase behavior

Objective:
To group the customers based on their RFM (Recency, Frequency, and Monetary). The result can later be used for targeted marketing.

Data:
The analysis is using the sales data on a year period from 1 July 2025 - 30 June 2026. Consist of 13751 rows of data, each row contains:
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

Tools:
  1. Excel
  2. Python (accessed with Google Colab)
