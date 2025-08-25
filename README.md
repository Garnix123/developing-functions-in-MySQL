# 🛠 SQL Functions & Stored Procedures – Lucky Shrub Database

## 🚀 Project Overview
This project demonstrates how to create and use **SQL user-defined functions** and **stored procedures** within a retail dataset (Lucky Shrub).  
The goal was to automate common operations such as retrieving order costs and applying discounts based on order quantity.

By practicing this, I learned how SQL functions help encapsulate logic and how stored procedures improve efficiency and reusability in real-world business contexts.

---

## 📊 Dataset
The database `Lucky_Schrub` contains an `Orders` table with the following fields:  
- **OrderID** – unique identifier of each order  
- **ClientID** – customer reference  
- **ProductID** – product reference  
- **Quantity** – items ordered  
- **Cost** – total cost of the order  
- **Date** – when the order was placed  

Example snippet of the data:  

| OrderID | ClientID | ProductID | Quantity | Cost  | Date       |
|---------|----------|-----------|----------|-------|------------|
| 5       | Cl3      | P3        | 10       | 450   | 2020-09-08 |
| 7       | Cl1      | P4        | 22       | 1200  | 2020-09-10 |
| 14      | Cl3      | P3        | 20       | 800   | 2022-09-03 |

## 📝 Tasks, Solutions & Outputs

### 🔹 Task 1: Create a Function `FindCost`

**Problem:** Retrieve the cost of an order given its `OrderID`.  

**SQL Code:**  
```sql
CREATE FUNCTION FindCost(order_id INT) 
RETURNS DECIMAL (5,2) DETERMINISTIC 
RETURN (SELECT Cost FROM Orders WHERE OrderID = order_id);

-- Example call:
SELECT FindCost(5);

OUTPUT = 450

