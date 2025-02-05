# Ecommerce_Data_Analysis_using_MySQL
## 📊 Ecommerce Data Analysis using MySQL

### 📌 Overview

#### This repository contains an E-commerce Data Analysis project using MySQL. It provides structured queries to analyze key business metrics such as sales trends, top customers, revenue analysis, and product performance.

### 🚀 Features

#### 📈 Sales Performance Analysis: Identify total sales, revenue trends, and best-selling products.

#### 🏆 Top Customers: Determine the top-spending customers each year.

#### 📊 Order Trends: Analyze peak purchase times and seasonal trends.

#### 📦 Inventory Insights: Track stock availability and demand patterns.

#### 🔍 Customer Behavior: Understand order frequency, retention rates, and churn analysis.

### ⚙️ Installation & Setup

#### 1. Clone the Repository

git clone https://github.com/harshit0330/Ecommerce_Data_Analysis_using_MySQL.git
cd Ecommerce_Data_Analysis_using_MySQL

#### 2. Import the Database

#### I. Open MySQL Workbench or phpMyAdmin.

#### II. Import the ecommerce.sql file from the repository.

#### III. Use the following command in MySQL:

#### SOURCE path/to/ecommerce.sql;

### 📌 SQL Queries Used

1️⃣ Total Sales and Revenue

SELECT YEAR(order_date) AS year, SUM(order_value) AS total_revenue
FROM orders
GROUP BY YEAR(order_date)
ORDER BY year DESC;

2️⃣ Top 3 Customers by Year

WITH RankedCustomers AS (
    SELECT customer_id, YEAR(order_date) AS order_year, SUM(order_value) AS total_spent,
           RANK() OVER (PARTITION BY YEAR(order_date) ORDER BY SUM(order_value) DESC) AS rank
    FROM orders
    GROUP BY customer_id, YEAR(order_date)
)
SELECT customer_id, order_year, total_spent FROM RankedCustomers WHERE rank <= 3;

3️⃣ Best-Selling Products

SELECT product_id, COUNT(*) AS total_sold
FROM order_details
GROUP BY product_id
ORDER BY total_sold DESC
LIMIT 10;

### 📊 Visualizations

📌 Matplotlib & Seaborn are used for data visualization.

Charts included: Histograms, Bar Charts, and Sales Trends.

🤝 Contributing

Fork the repository.

Create a new branch: git checkout -b feature-branch

Commit your changes: git commit -m "Added new analysis query"

Push the changes: git push origin feature-branch

Submit a Pull Request.


### 📞 Contact

🔹 Author: Harshit0330🔹 GitHub: @harshit0330🔹 Email: harshitjain3927@gmail.com

💡 Let's explore insights from E-commerce data together! 🚀

