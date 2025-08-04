# 🍕 Pizza Sales SQL Analysis

This project showcases an end-to-end SQL analysis of a pizza sales dataset using MySQL. It involves writing efficient queries to derive business insights such as total revenue, best-selling pizzas, contribution by category, and more.

---

## 📊 Project Objectives

- Analyze and understand pizza sales data
- Calculate key business metrics using SQL
- Apply advanced SQL concepts like window functions, subqueries, and joins
- Visualize performance by category, date, and product

---

## 🧩 Dataset Overview

The dataset includes the following CSV files:

| File Name         | Description                                     |
|------------------|-------------------------------------------------|
| `orders.csv`      | Contains order timestamps and order IDs        |
| `order_details.csv` | Contains pizza orders with quantity info     |
| `pizzas.csv`      | Links each pizza ID to its price and type      |
| `pizza_types.csv` | Describes pizza names, categories, and sizes   |

---
## 🛠️ SQL Concepts Used

- `JOIN` (INNER JOIN)
- `GROUP BY`, `ORDER BY`
- Aggregate functions: `SUM()`, `COUNT()`, `ROUND()`
- `RANK()` and `PARTITION BY` for window functions
- `SUBQUERIES` and `CTEs`
- Data cleaning and type consistency


📈 What You’ll Learn
Real-world SQL use for data analysis

Business intelligence reporting

Creating SQL dashboards (if extended)

Structuring queries for large datasets

🙋‍♂️ Author
Satender Kumar
[Your LinkedIn or Portfolio URL here](https://www.linkedin.com/in/satender-kumar-340038264/)

🌟 Contributions
Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

📄 License
This project is open source and available under the MIT License.
---

## 🧠 Example Query

```sql
SELECT 
    pt.category, 
    pt.name, 
    SUM(od.quantity * p.price) AS revenue,
    RANK() OVER (PARTITION BY pt.category ORDER BY SUM(od.quantity * p.price) DESC) AS rank_within_category
FROM 
    pizza_types pt
JOIN

    pizzas p ON pt.pizza_type_id = p.pizza_type_id
JOIN 
    orders_details od ON od.pizza_id = p.pizza_id

GROUP BY 
    pt.category, pt.name;


