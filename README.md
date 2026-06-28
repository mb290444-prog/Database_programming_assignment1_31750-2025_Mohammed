# Database Programming Assignment 1:

## 1. Business Problem
​"The objective is to manage customer orders efficiently by organizing data into relational tables and utilizing SQL techniques like Common Table Expressions (CTEs) and Window Functions to generate meaningful insights and reports from order details."

## 2. Database Schema & ER Diagram
+----------------+          +-----------------+          +----------------+
|    Customers   |          |      Orders     |          |    Products    |
+----------------+          +-----------------+          +----------------+
| PK CustomerID  |----------| FK CustomerID   |          | PK ProductID   |
|    Name        |          | FK ProductID    |----------|    Name        |
+----------------+          |    Quantity     |          +----------------+
                            +-----------------+

#The database is designed to handle retail operations through three core tables:
​*Customers Table: Stores essential customer information (e.g., CustomerID, CustomerName).
​*Products Table:  Maintains a catalog of items (e.g., ProductID, ProductName).
​*Orders Table:    Acts as the central transaction table, linking customers and products via foreign keys (OrderID, CustomerID, ProductID, Quantity).
​This relational structure ensures data integrity and supports complex queries like joins and aggregations."
## 3. CTE Implementations
1.Simple CTE:
"A simple CTE used to isolate the OrderID and Quantity columns from the Orders table for cleaner data retrieval"
<img width="371" height="198" alt="1_Simple_CTE" src="https://github.com/user-attachments/assets/eabc867a-4cb0-4458-8af7-1cb72f354e27" />

2.Multiple CTEs:
"This query uses two CTEs simultaneously (Customer_CTE and Product_CTE) to join data from three different tables, demonstrating efficient multi_table querying"
<img width="332" height="365" alt="2_Multiple_CTEs" src="https://github.com/user-attachments/assets/6d22699f-353b-47f6-b80c-9fdfc0e2cc0f" />

3.Recursive CTE:
"A recursive CTE that generates a sequential list of numbers from 1to5, illustrating the power of self_referencing queries in SQL"
<img width="413" height="245" alt="3_Recursive_CTE" src="https://github.com/user-attachments/assets/8d547218-643e-4598-a24f-b9c579f5b938" />

4.CTE with Aggregation:
"This implementation uses a CTE combined with SUM() function to calculate the total quantity of items per customer, simplifying complex aggregation tasks"
<img width="416" height="157" alt="4_CTE_Aggregation" src="https://github.com/user-attachments/assets/a242d493-48d9-4adb-a40c-794ec28b44a9" />

5.CTE combined with JOIN: 
"A CTE utilized to prepare order details, which is then joined with the Customers table to map each order to the respective customer name"
<img width="443" height="223" alt="5_CTE_JOIN" src="https://github.com/user-attachments/assets/98c75425-e33c-4748-a46d-c7f79413d2f8" />

## 4. Window Function Implementations
​Description:
This query utilizes the SUM() OVER() Window Function to calculate a running total of the quantity ordered, partitioned by each customer and ordered by their order date. This provides a cumulative view of customer purchasing activity.

SELECT OrderID, CustomerID, Quantity, 
SUM(Quantity) OVER (PARTITION BY CustomerID ORDER BY OrderDate) as RUNNING_TOTAL
FROM Orders;

<img width="622" height="209" alt="Windoe_func_Result" src="https://github.com/user-attachments/assets/753a3774-0f7d-421a-a163-5b7155714a68" />

#Ranking Funiction:
Description: This query uses RANK() to assign a rank to orders based on their quantity, allowing us to identify high-value orders easily.
<img width="571" height="167" alt="Ranking_Funiction_Result" src="https://github.com/user-attachments/assets/400014a0-177c-43f5-98a5-c6fd220da81d" />

#Aggregate Window Funiction:
Description: This query utilizes SUM() OVER() to calculate a running total of the quantity ordered, partitioned by customer.
 <img width="616" height="178" alt="Aggregate_Function_Result" src="https://github.com/user-attachments/assets/96953838-8205-4b67-a490-9913eb0b9fd2" />


#Navigation Function:
Description: This query uses LAG() to look at the previous order's quantity, which helps in analyzing trends or changes between consecutive orders.
<img width="686" height="177" alt="Navigation_Funiction_Result" src="https://github.com/user-attachments/assets/1ef85908-acef-4e93-a709-8d88662d3169" />

#Distribution Function
​Description: This query uses the NTILE(2) function to divide the orders into two equal groups (or "buckets") based on their quantity. This is highly effective for categorizing data into performance levels (e.g., high-quantity vs. low-quantity orders).
<img width="472" height="178" alt="Distribution_Function_Result" src="https://github.com/user-attachments/assets/670db70a-4118-4b3a-a1ff-fa4c5867fddd" />


## 5. Analysis and Findings
​#Based on the implementation of CTEs and Window Functions, the following findings were observed:
​*Efficiency: CTEs significantly improved the readability and maintainability of complex queries compared to nested subqueries.
​*Data Insights: Window functions allowed for sophisticated row-level calculations, providing deeper insights into order patterns and customer behavior.
​*Scalability: The modular design approach makes the queries easier to debug and scale for larger datasets."

​#Descriptive Analysis:
Based on the implemented queries, we successfully retrieved total sales per customer and observed the progression of orders over time. The analysis shows the quantity distribution across different customer tiers, clearly illustrating "what happened" in our transaction history.

## Academic Integrity Statement
I, [Mohammed], hereby declare that this assignment is my own original work. 
I have acknowledged all sources and materials used in the preparation of this report 
in accordance with the university's academic integrity policy.

## References
* SQL Window Functions Documentation (e.g., PostgreSQL or Oracle Docs).
* Common Table Expressions (CTE) Overview - SQL Performance Explained.
* Course Lecture Notes and Provided Materials.


