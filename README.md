# SQL---Interview-Question
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


### 1. **What is a correlated subquery, and how does it differ from a regular subquery?**
   - **Correlated Subquery:** A correlated subquery is a subquery that references columns from the outer query. It is executed repeatedly, once for each row in the outer query.
     - **Example:**
       ```sql
       SELECT e1.EmployeeID, e1.Salary
       FROM Employees e1
       WHERE e1.Salary > (SELECT AVG(e2.Salary) FROM Employees e2 WHERE e2.DepartmentID = e1.DepartmentID);
       ```
       In this example, the subquery is correlated with the outer query because it references `e1.DepartmentID`.
   - **Regular Subquery:** A regular subquery, or non-correlated subquery, is independent of the outer query. It is executed once and the result is passed to the outer query.
     - **Example:**
       ```sql
       SELECT EmployeeID, Salary
       FROM Employees
       WHERE Salary > (SELECT AVG(Salary) FROM Employees);
       ```
       Here, the subquery calculates the average salary of all employees and compares each employee’s salary to this value.

### 2. **Explain how to use the `LEAD()` and `LAG()` functions in SQL. Provide an example.**
   - **`LEAD()` Function:** Retrieves the value from the next row in the result set, based on the specified ordering.
   - **`LAG()` Function:** Retrieves the value from the previous row in the result set, based on the specified ordering.
     - **Example:**
       ```sql
       SELECT 
           EmployeeID, 
           Salary, 
           LEAD(Salary, 1) OVER (ORDER BY Salary) AS NextSalary,
           LAG(Salary, 1) OVER (ORDER BY Salary) AS PreviousSalary
       FROM Employees;
       ```
       In this example, `LEAD(Salary, 1)` gets the next employee's salary, and `LAG(Salary, 1)` gets the previous employee's salary.

### 3. **How would you calculate a moving average for sales data over a 7-day period?**
   - **Moving Average Calculation:**
     - **Example:**
       ```sql
       SELECT 
           SaleDate, 
           SalesAmount, 
           AVG(SalesAmount) OVER (ORDER BY SaleDate ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS MovingAverage
       FROM Sales;
       ```
       This query calculates the 7-day moving average by averaging the sales amount from the current row and the previous 6 rows.

### 4. **What is the difference between `ROW_NUMBER()` and `RANK()` in SQL?**
   - **`ROW_NUMBER()`:** Assigns a unique sequential number to rows, starting at 1 for the first row.
   - **`RANK()`:** Assigns a rank to each row within a partition of the result set. If two rows have the same rank, the next rank(s) are skipped.
     - **Example:**
       ```sql
       SELECT 
           EmployeeID, 
           Salary, 
           ROW_NUMBER() OVER (ORDER BY Salary DESC) AS RowNum,
           RANK() OVER (ORDER BY Salary DESC) AS Rank
       FROM Employees;
       ```
       If two employees have the same salary, `ROW_NUMBER()` will still assign unique numbers, but `RANK()` will assign the same rank to both.

### 5. **How can you use CTEs to manage hierarchical data, such as an employee organizational chart?**
   - **Using CTEs for Hierarchical Data:**
     - **Example:**
       ```sql
       WITH EmployeeCTE AS (
           SELECT EmployeeID, Name, ManagerID, 1 AS Level
           FROM Employees
           WHERE ManagerID IS NULL  -- Start with top-level managers
           UNION ALL
           SELECT e.EmployeeID, e.Name, e.ManagerID, c.Level + 1
           FROM Employees e
           INNER JOIN EmployeeCTE c ON e.ManagerID = c.EmployeeID
       )
       SELECT * FROM EmployeeCTE ORDER BY Level;
       ```
       This CTE recursively builds the organizational chart, starting from top-level managers and progressing down the hierarchy.

### 6. **Describe how to calculate a rolling sum over a partitioned dataset.**
   - **Rolling Sum Calculation:**
     - **Example:**
       ```sql
       SELECT 
           DepartmentID, 
           EmployeeID, 
           Salary, 
           SUM(Salary) OVER (PARTITION BY DepartmentID ORDER BY EmployeeID ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS RollingSum
       FROM Employees;
       ```
       This query calculates the rolling sum of salaries within each department over the current row and the previous two rows.

### 7. **What is the purpose of `NTILE()` in SQL, and how would you use it?**
   - **Purpose of `NTILE()`:** The `NTILE()` function distributes rows into a specified number of approximately equal buckets or groups.
     - **Example:**
       ```sql
       SELECT 
           EmployeeID, 
           Salary, 
           NTILE(4) OVER (ORDER BY Salary DESC) AS SalaryQuartile
       FROM Employees;
       ```
       This divides employees into four groups based on their salaries, creating salary quartiles.

### 8. **Explain how to perform date manipulation to find the number of weekdays between two dates.**
   - **Date Manipulation for Weekdays:**
     - **Example:**
       ```sql
       SELECT 
           StartDate, 
           EndDate,
           (DATEDIFF(DAY, StartDate, EndDate) + 1) 
           - (DATEDIFF(WEEK, StartDate, EndDate) * 2)
           - (CASE WHEN DATENAME(WEEKDAY, StartDate) = 'Sunday' THEN 1 ELSE 0 END)
           - (CASE WHEN DATENAME(WEEKDAY, EndDate) = 'Saturday' THEN 1 ELSE 0 END) 
           AS WeekdaysCount
       FROM DateTable;
       ```
       This query calculates the number of weekdays between two dates, adjusting for weekends.

### 9. **How do you handle NULL values in SQL during aggregation?**
   - **Handling NULL Values:**
     - **Example:**
       ```sql
       SELECT 
           DepartmentID, 
           SUM(ISNULL(Salary, 0)) AS TotalSalary
       FROM Employees
       GROUP BY DepartmentID;
       ```
       Use `ISNULL()` or `COALESCE()` to replace `NULL` values with a default value before performing aggregations.

### 10. **Describe a scenario where using a window function would be more beneficial than a subquery.**
   - **Scenario for Window Function:**
     - **Example:** Calculating cumulative sales within each region.
       ```sql
       SELECT 
           Region, 
           SaleDate, 
           SalesAmount, 
           SUM(SalesAmount) OVER (PARTITION BY Region ORDER BY SaleDate) AS CumulativeSales
       FROM Sales;
       ```
       Here, a window function is more efficient than a subquery because it avoids repeated execution of the subquery and provides cumulative results directly, making the query more readable and performant.


 *Write a query to extract employee name in the sales department:*
    SQL
    SELECT employee_name
    FROM employees
    WHERE department = 'Sales';
    

 *Explain indexing in SQL:*
    - *Indexing* improves the speed of data retrieval operations on a database table at the cost of additional storage and slower writes.

 *Explain what a pivot table does:*
    - A pivot table is a data summarization tool that aggregates data and enables quick data analysis, typically used for sorting, counting, and averaging data.

 *Explain the INDEX and MATCH function in Excel:*
    - *INDEX:* Returns a value from a specified position in a range.
    - *MATCH:* Returns the relative position of an item in a range that matches a specified value.
    - *Formula Example:*
      Excel
      =INDEX(A1:A10, MATCH(B1, B1:B10, 0))
      

### SQL and Excel Functions

 *Explain DELETE, DROP, and TRUNCATE functions:*
    - *DELETE:* Removes rows from a table based on a condition.
    - *DROP:* Removes a table or database completely.
    - *TRUNCATE:* Removes all rows from a table without logging individual row 

    Here's an explanation of different types of SQL commands and queries:

### SQL Command Types

1. **DML (Data Manipulation Language)**:
   - **Purpose**: Used to manage and manipulate data within tables.
   - **Commands**: 
     - `SELECT` - Retrieve data from a database.
     - `INSERT` - Add new rows to a table.
     - `UPDATE` - Modify existing data in a table.
     - `DELETE` - Remove rows from a table.

2. **DDL (Data Definition Language)**:
   - **Purpose**: Used to define and manage the structure of database objects.
   - **Commands**:
     - `CREATE` - Create new tables, views, indexes, etc.
     - `ALTER` - Modify existing database objects.
     - `DROP` - Delete database objects.
     - `TRUNCATE` - Remove all rows from a table (but keeps the table structure).

3. **DCL (Data Control Language)**:
   - **Purpose**: Used to control access to data in the database.
   - **Commands**:
     - `GRANT` - Provide specific privileges to users.
     - `REVOKE` - Remove specific privileges from users.

4. **TCL (Transaction Control Language)**:
   - **Purpose**: Used to manage transactions in a database.
   - **Commands**:
     - `COMMIT` - Save all changes made in the current transaction.
     - `ROLLBACK` - Undo changes made in the current transaction.
     - `SAVEPOINT` - Set a point in the transaction to which you can later roll back.

### SQL Queries

1. **Find the Second Highest Salary**:

   To find the second highest salary, you can use a subquery with `LIMIT` or `ROW_NUMBER()` depending on the SQL dialect.

   **Using a Subquery**:
   ```SQL
   SELECT MAX(salary) AS second_highest_salary
   FROM employees
   WHERE salary < (SELECT MAX(salary) FROM employees);
   ```

   **Using `ROW_NUMBER()` (if supported)**:
   ```SQL
   WITH RankedSalaries AS (
       SELECT salary, ROW_NUMBER() OVER (ORDER BY salary DESC) AS rank
       FROM employees
   )
   SELECT salary AS second_highest_salary
   FROM RankedSalaries
   WHERE rank = 2;
   ```

2. **Write a Query to Extract Employee Names in the Sales Department**:

   Assuming you have an `employees` table and a `department` column:

   ```SQL
   SELECT employee_name
   FROM employees
   WHERE department = 'Sales';
   ```

   If the `department` information is in a separate table, you might need to join the tables. For example:

   ```SQL
   SELECT e.employee_name
   FROM employees e
   JOIN departments d ON e.department_id = d.department_id
   WHERE d.department_name = 'Sales';
   ```

 



