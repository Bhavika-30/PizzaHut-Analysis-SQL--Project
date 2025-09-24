# 🍕 PizzaHut-Analysis-SQL--Project

This project showcases an **end-to-end MySQL analytics workflow** using pizza sales data.  
The goal is to replicate how a data analyst explores transactional data, builds KPIs, and delivers actionable insights for a retail food chain.

---

## 📌 Project Objectives
- Create a relational database with proper **keys, constraints, and datatypes**  
- Perform **Exploratory Data Analysis (EDA)** directly in SQL  
- Calculate key **business metrics** such as revenue, product performance, and ordering patterns  
- Demonstrate **window functions**, aggregation, and advanced SQL techniques for real analytics use cases  

---

## 🔍 Dataset Overview
The dataset simulates **PizzaHut** order transactions and item-level details.  
It contains information on **orders**, **pizzas**, **pizza types**, and **order details**, reflecting real restaurant operations.

### Key Tables
| Table | Description |
|------|-------------|
| **orders** | Each customer order with order date & time |
| **order_details** | Itemized pizzas per order and their quantities |
| **pizzas** | SKU-level pizza records with size & price |
| **pizza_types** | Pizza name and category (e.g., Classic, Supreme, Veggie) |

---

## 🧠 Key Insights
- **Total Orders & Revenue**: Overall sales volume and total revenue across all dates  
- **Highest-Priced Pizza**: Identify premium SKUs to optimize pricing strategy  
- **Most Common Size**: Determine customer preference (Small/Medium/Large/XL)  
- **Top 5 Pizza Types**: Rank pizzas by total quantity sold  
- **Category Contribution**: Revenue share of each pizza category  
- **Hourly Demand Curve**: Order distribution by time of day  
- **Daily Averages**: Average pizzas sold per day  
- **Cumulative Revenue**: Running total of revenue over time  
- **Category-wise Top 3 by Revenue**: Window functions to reveal leaders in each category  

---

## 🛠️ Skills Demonstrated
- **SQL DDL**: Creating databases, tables, primary & foreign keys, constraints  
- **SQL DML**: Joins, Group By, Aggregations, Window Functions, Subqueries  
- **Analytical Thinking**: Translating business questions into SQL metrics  
- **Data Modeling**: Designing normalized tables for scalable analysis  
- **Performance Optimization**: Using indexes & query refactoring for efficiency  

---

## 🧪 Sample Query — Cumulative Revenue Over Time
```sql
WITH daily AS (
  SELECT o.order_date,
         SUM(od.quantity * p.price) AS revenue
  FROM orders o
  JOIN order_details od ON o.order_id = od.order_id
  JOIN pizzas p ON p.pizza_id = od.pizza_id
  GROUP BY o.order_date
)
SELECT order_date,
       SUM(revenue) OVER (ORDER BY order_date
                          ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS cum_revenue
FROM daily
ORDER BY order_date;
```
This query calculates **daily revenue** and the **running total** to track sales growth.

---

## 🚀 Project Highlights
- Clean, **modular SQL scripts** for each analysis question (Q1–Q13)  
- Business-oriented metrics directly usable by operations teams  
- Demonstrates **window functions** (`RANK`, `SUM OVER`) for advanced analytics  
- **Portfolio-ready** for GitHub and LinkedIn to showcase SQL expertise  

---

## 🖥️ Tools & Technologies
- **MySQL / SQL Server / PostgreSQL** (queries are ANSI-SQL compliant with minor syntax tweaks)  
- MySQL Workbench / DBeaver for schema design & query execution  
- VS Code for SQL script management and documentation  

---

## 📬 Let’s Connect
This project is part of my journey into **Data Analytics and Business Intelligence**.  
Feel free to explore the SQL scripts, share feedback, or connect with me on [LinkedIn](https://www.linkedin.com/in/bhavika-garg-470371259/) for collaboration opportunities.

---

### 🏷️ Tags
`#SQL` `#MySQL` `#PizzaHut` `#DataAnalytics` `#RetailAnalysis` `#PortfolioProject` `#WindowFunctions` `#BusinessInsights`
