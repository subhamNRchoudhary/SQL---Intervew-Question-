# SQL---Interview-Question-
All the questions related to SQL




### 1. **What is the difference between `INNER JOIN` and `OUTER JOIN`?**
   - **Answer:** `INNER JOIN` returns only the matching rows from both tables, while `OUTER JOIN` returns all rows from one table and the matching rows from the other. If there's no match, NULL values are returned for the non-matching side.

### 2. **What is a `PRIMARY KEY` and a `FOREIGN KEY`?**
   - **Answer:** A `PRIMARY KEY` uniquely identifies each record in a table, ensuring no duplicate values. A `FOREIGN KEY` is a field in one table that links to the `PRIMARY KEY` in another table, establishing a relationship between the two tables.

### 3. **How would you optimize a slow-running query?**
   - **Answer:** Strategies include:
     - Analyzing the query execution plan.
     - Adding appropriate indexes.
     - Reducing the number of joins.
     - Optimizing subqueries and using `JOIN` instead of `IN` when possible.
     - Limiting the number of rows returned using `LIMIT` or `TOP`.
     - Avoiding SELECT * by specifying the needed columns.

### 4. **Explain the difference between `WHERE` and `HAVING` clauses.**
   - **Answer:** `WHERE` is used to filter rows before any groupings are made, whereas `HAVING` filters rows after the grouping has occurred.

### 5. **What is the difference between `UNION` and `UNION ALL`?**
   - **Answer:** `UNION` combines the results of two queries and removes duplicates, while `UNION ALL` combines the results and includes duplicates.

### 6. **What is a `CROSS JOIN`?**
   - **Answer:** A `CROSS JOIN` returns the Cartesian product of the two tables involved, meaning it returns all possible combinations of rows from both tables.

### 7. **What is normalization? Explain the different normal forms.**
   - **Answer:** Normalization is the process of organizing data to reduce redundancy. The different normal forms include:
     - **1NF (First Normal Form):** Ensures each column contains atomic (indivisible) values, and each record is unique.
     - **2NF (Second Normal Form):** Meets all 1NF requirements and removes subsets of data that apply to multiple rows of a table, and places them in separate tables.
     - **3NF (Third Normal Form):** Meets all 2NF requirements and removes columns that are not dependent on the primary key.
     - **BCNF (Boyce-Codd Normal Form):** A stronger version of 3NF, where every determinant must be a candidate key.

### 8. **What are `Indexes`? How do they work?**
   - **Answer:** Indexes are database objects that improve the speed of data retrieval operations on a table at the cost of additional space and slower write operations. They work by creating a data structure (like a B-tree) that allows for fast lookups, similar to an index in a book.

### 9. **What is a `Stored Procedure`?**
   - **Answer:** A stored procedure is a set of SQL statements that can be stored and reused. They allow for the encapsulation of logic, reduce redundancy, and can improve performance by reducing the need for repeated parsing and compilation.

### 10. **Explain the concept of `ACID` properties in a database.**
   - **Answer:** ACID stands for Atomicity, Consistency, Isolation, and Durability. These properties ensure reliable processing of database transactions:
     - **Atomicity:** Transactions are all-or-nothing.
     - **Consistency:** Transactions bring the database from one valid state to another.
     - **Isolation:** Transactions are executed in isolation.
     - **Durability:** Once a transaction is committed, it remains so, even in the event of a system failure.




To make your work easier when dealing with large datasets in SQL, especially when performing complex operations like indexing, ranking, and analytical calculations, it's essential to understand and effectively utilize various SQL techniques. Here's a guide on how to approach these tasks, along with additional questions for practice.

### 1. **Indexing**
   - **Tip:** Create indexes on columns that are frequently used in `JOIN` conditions, `WHERE` clauses, and as part of the `ORDER BY` clause. This speeds up data retrieval by reducing the number of rows scanned.
   - **Key Points:**
     - Use **Clustered Indexes** for columns that are frequently queried in ranges.
     - Use **Non-Clustered Indexes** for specific lookups.
     - Avoid over-indexing, as it can slow down `INSERT`/`UPDATE` operations.

### 2. **Joins**
   - **Tip:** Optimize joins by ensuring that the columns used in joins are indexed. Avoid joining too many tables in a single query unless necessary.
   - **Key Points:**
     - Use `INNER JOIN` when you need only matching records.
     - Use `LEFT JOIN` or `RIGHT JOIN` when you need all records from one table, regardless of a match.
     - Consider `CROSS JOIN` for Cartesian products and use it wisely.

### 3. **Ranking and Partition**
   - **Tip:** Use `RANK()`, `DENSE_RANK()`, and `ROW_NUMBER()` functions for ranking data within partitions.
   - **Key Points:**
     - Partition data using `PARTITION BY` to group data into subsets.
     - Use ranking functions to assign ranks within each partition.

### 4. **Rolling Sum and Moving Average**
   - **Tip:** Utilize `WINDOW FUNCTIONS` like `SUM()` and `AVG()` over a specific range of rows to calculate rolling sums and moving averages.
   - **Key Points:**
     - Use `OVER(PARTITION BY... ORDER BY...)` to define the window.
     - Define the frame using `ROWS BETWEEN...`.

### 5. **Descriptive Statistics**
   - **Tip:** Use built-in SQL functions like `AVG()`, `COUNT()`, `SUM()`, `MIN()`, `MAX()` to calculate descriptive statistics.
   - **Key Points:**
     - Group data appropriately using `GROUP BY` to calculate statistics for different categories.
     - For more complex statistics, consider using subqueries or CTEs.

### 6. **CTE (Common Table Expression)**
   - **Tip:** Use CTEs to simplify complex queries by breaking them down into more manageable parts.
   - **Key Points:**
     - Use `WITH` to define a CTE at the beginning of your query.
     - CTEs can be recursive, making them powerful for hierarchical data.

### 7. **DateTime Manipulation**
   - **Tip:** Use SQL functions like `DATEADD()`, `DATEDIFF()`, and `DATEPART()` to manipulate and analyze date and time data.
   - **Key Points:**
     - Convert and format dates as needed using `CONVERT()` and `FORMAT()`.
     - Calculate intervals between dates with `DATEDIFF()`.

### 8. **Grouping and Sorting**
   - **Tip:** Use `GROUP BY` for aggregation and `ORDER BY` for sorting results.
   - **Key Points:**
     - Use `HAVING` to filter groups after aggregation.
     - Ensure indexes are used on columns that appear in `ORDER BY` clauses for faster sorting.

### 9. **Correlation**
   - **Tip:** To find correlations, use statistical functions like `COVAR_SAMP()` or `COVAR_POP()` to calculate covariance and then use the results to compute correlation.
   - **Key Points:**
     - Combine correlation calculations with data grouping and partitioning for better insights.
     - Use window functions to analyze correlations over time periods.

### 10. **Rounding**
   - **Tip:** Use `ROUND()`, `FLOOR()`, `CEILING()` for rounding numeric data as needed.
   - **Key Points:**
     - Specify the precision level when using `ROUND()`.
     - Use `TRUNCATE()` for truncating without rounding.

### 11. **Aggregation Functions**
   - **Tip:** Utilize SQL’s aggregation functions to summarize data.
   - **Key Points:**
     - `SUM()`, `AVG()`, `COUNT()`, `MIN()`, `MAX()` are commonly used.
     - Combine with `GROUP BY` to aggregate data across categories.

### 12. **Sub-Queries**
   - **Tip:** Use subqueries to break down complex queries or when you need to perform operations in multiple steps.
   - **Key Points:**
     - Correlated subqueries can be used for row-by-row operations.
     - Non-correlated subqueries are useful for filtering and aggregation.

### 13. **Other Analytical Functions**
   - **Tip:** Explore other SQL analytical functions like `LEAD()`, `LAG()`, `NTILE()` for advanced analysis.
   - **Key Points:**
     - `LEAD()` and `LAG()` can be used to compare values from different rows.
     - Use `NTILE()` to divide rows into buckets.






