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

 These are some great best practices for writing efficient and readable SQL code. Here’s a breakdown of each guideline:

1. **Write SQL keywords in capital letters:**  
   Using capital letters for SQL keywords like `SELECT`, `FROM`, `WHERE`, `JOIN`, etc., helps in differentiating them from table names, columns, and other elements. It enhances the readability of the query.

2. **Use table aliases with columns when joining multiple tables:**  
   Table aliases help in making your SQL queries shorter and easier to read, especially when you are dealing with multiple tables. For instance:
   ```sql
   SELECT A.column1, B.column2
   FROM table1 AS A
   JOIN table2 AS B ON A.id = B.id;
   ```

3. **Never use `SELECT *`; always mention the list of columns in the `SELECT` clause:**  
   Using `SELECT *` can lead to unnecessary data retrieval, which can be inefficient. It’s better to specify the columns you need:
   ```sql
   SELECT column1, column2
   FROM table1;
   ```

4. **Add useful comments wherever you write complex logic. Avoid too many comments:**  
   Comments can explain why certain complex logic is used, making the code easier to understand. However, over-commenting can clutter the code. Keep comments concise and to the point.
   ```sql
   -- This join is used to combine data from table1 and table2 based on the id column
   SELECT A.column1, B.column2
   FROM table1 AS A
   JOIN table2 AS B ON A.id = B.id;
   ```

5. **Use `JOIN` instead of subqueries when possible for better performance:**  
   Joins are generally more efficient than subqueries, especially for large datasets, because the database can optimize the join operation better.

6. **Create CTEs (Common Table Expressions) instead of multiple subqueries; it will make your query easy to read:**  
   CTEs can simplify complex queries by breaking them down into more manageable parts:
   ```sql
   WITH CTE AS (
       SELECT column1, column2
       FROM table1
       WHERE condition
   )
   SELECT *
   FROM CTE;
   ```

7. **Join tables using `JOIN` keywords instead of writing join conditions in the `WHERE` clause for better readability:**  
   Using explicit `JOIN` syntax makes the intention of the query clearer and easier to understand:
   ```sql
   SELECT A.column1, B.column2
   FROM table1 AS A
   JOIN table2 AS B ON A.id = B.id;
   ```

8. **Never use `ORDER BY` in subqueries; it will unnecessarily increase runtime:**  
   Ordering in subqueries can lead to inefficient execution plans. Instead, apply `ORDER BY` in the outer query if needed:
   ```sql
   SELECT *
   FROM (
       SELECT column1, column2
       FROM table1
   ) AS subquery
   ORDER BY column1;
   ```

9. **If you know there are no duplicates in two tables, use `UNION ALL` instead of `UNION` for better performance:**  
   `UNION` removes duplicates, which can be costly in terms of performance. If you are sure there are no duplicates, `UNION ALL` is more efficient:
   ```sql
   SELECT column1 FROM table1
   UNION ALL
   SELECT column1 FROM table2;
   ```


### 1. How to Find Duplicates in a Table
To find duplicates in a table, you can group by the columns that should be unique and use the `HAVING` clause to filter groups with a count greater than 1.

```sql
SELECT column1, column2, COUNT(*)
FROM your_table
GROUP BY column1, column2
HAVING COUNT(*) > 1;
```

### 2. How to Delete Duplicates from a Table
To delete duplicates, you can use a `CTE` with `ROW_NUMBER()` to identify duplicates and then delete those rows.

```sql
WITH CTE AS (
    SELECT *, ROW_NUMBER() OVER(PARTITION BY column1, column2 ORDER BY (SELECT 1)) AS rn
    FROM your_table
)
DELETE FROM your_table
WHERE id IN (SELECT id FROM CTE WHERE rn > 1);
```

### 3. Difference Between `UNION` and `UNION ALL`
- **`UNION`**: Combines the results of two queries and removes duplicate records. It performs an additional step to check for duplicates, which may affect performance.
- **`UNION ALL`**: Combines the results of two queries without removing duplicates. It's faster because it doesn't check for duplicates.

### 4. Difference Between `RANK`, `ROW_NUMBER`, and `DENSE_RANK`
- **`ROW_NUMBER()`**: Assigns a unique sequential integer to rows within a partition of a result set, starting at 1.
- **`RANK()`**: Similar to `ROW_NUMBER()` but gives the same rank to rows with identical values, leaving gaps in the sequence.
- **`DENSE_RANK()`**: Similar to `RANK()`, but without gaps in the ranking sequence. Rows with identical values receive the same rank.

### 5. Find Records in a Table That Are Not Present in Another Table
You can use the `LEFT JOIN` with a `NULL` check or a `NOT EXISTS` subquery.

Using `LEFT JOIN`:
```sql
SELECT a.*
FROM table1 a
LEFT JOIN table2 b ON a.column = b.column
WHERE b.column IS NULL;
```

Using `NOT EXISTS`:
```sql
SELECT *
FROM table1 a
WHERE NOT EXISTS (SELECT 1 FROM table2 b WHERE a.column = b.column);
```

### 6. Find Second Highest Salary Employees in Each Department
You can use `DENSE_RANK()` or `ROW_NUMBER()` within a `CTE` to find the second highest salary.

```sql
WITH CTE AS (
    SELECT *, DENSE_RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rk
    FROM employees
)
SELECT *
FROM CTE
WHERE rk = 2;
```

### 7. Find Employees with Salary More Than Their Manager's Salary
Assume `employees` table has columns `employee_id`, `manager_id`, and `salary`.

```sql
SELECT e1.*
FROM employees e1
JOIN employees e2 ON e1.manager_id = e2.employee_id
WHERE e1.salary > e2.salary;
```

### 8. Difference Between `INNER JOIN` and `LEFT JOIN`
- **`INNER JOIN`**: Returns only the rows that have matching values in both tables.
- **`LEFT JOIN`**: Returns all rows from the left table and matched rows from the right table. If there's no match, `NULL` is returned for columns from the right table.

### 9. Update a Table and Swap Gender Values
Assume the `gender` column contains values 'M' for Male and 'F' for Female.

```sql
UPDATE employees
SET gender = CASE 
    WHEN gender = 'M' THEN 'F'
    WHEN gender = 'F' THEN 'M'
    ELSE gender
END;
```
![image](https://github.com/user-attachments/assets/ae48edfe-3cfc-4ae1-b162-f3685bb70909)
![image](https://github.com/user-attachments/assets/f9e83f61-dcd6-4633-92d0-24a1103cefd1)

*SQL | WHERE Clause*

   WHERE keyword is used for fetching filtered data in a result set. It is used to fetch data according to particular criteria. WHERE keyword can also be used to filter data by matching patterns.

![image](https://github.com/user-attachments/assets/6604efc6-e8a0-4b1b-9f5b-a4cfadcd0a5f)

      CREATE TABLE Emp1(
          EmpID INT PRIMARY KEY,
          Name VARCHAR(50),
          Country VARCHAR(50),
          Age int(2),
        mob int(10)
      );
      -- Insert some sample data into the Customers table
      INSERT INTO Emp1 (EmpID, Name,Country, Age, mob)
      VALUES (1, 'Shubham',  'India','23','738479734'),
             (2, 'Aman ',  'Australia','21','436789555'),
             (3, 'Naveen', 'Sri lanka','24','34873847'),
             (4, 'Aditya',  'Austria','21','328440934'),
             (5, 'Nishant', 'Spain','22','73248679');
         
   
       Select * from Emp1;
   ![image](https://github.com/user-attachments/assets/d063914e-d152-44a5-b3d6-34138658a064)

       select* from Emp1 
       where Age = 21;

   ![image](https://github.com/user-attachments/assets/35eeb2ba-2891-4638-a102-fb4db161546d)
    

![image](https://github.com/user-attachments/assets/6b18439a-59bf-4809-ae2f-003da65fbdff)

      SELECT * FROM Emp1 WHERE Age=24;    
    
      select EmpID,Name,Country
      from Emp1 where Age > 21;
      
![image](https://github.com/user-attachments/assets/9af6ac79-cc08-4213-badc-bf2b6d4e137f)


       SELECT * FROM Emp1 WHERE Age BETWEEN 22 AND 24;

   ![image](https://github.com/user-attachments/assets/f5371055-35cf-4824-8776-73926b485777)


       SELECT * FROM Emp1 WHERE Name LIKE 'S%'; 

   ![image](https://github.com/user-attachments/assets/6d867205-0b2f-484c-99de-32254264f27d)

    

    SELECT * FROM Emp1 WHERE Name LIKE '%M%';

   ![image](https://github.com/user-attachments/assets/bf1f9674-0b48-4bbb-b7af-71cb07ae77cb)
    

*SQL | WITH Clause*

 The SQL WITH clause allows you to give a sub-query block a name (a process also called sub-query refactoring), which can be referenced in several places within the main SQL query. 

 
