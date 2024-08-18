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
   - **Answer:** A stored procedure is a set of SQL statements that can be stored and reused. They allow for encapsulation of logic, reduce redundancy, and can improve performance by reducing the need for repeated parsing and compilation.

### 10. **Explain the concept of `ACID` properties in a database.**
   - **Answer:** ACID stands for Atomicity, Consistency, Isolation, and Durability. These properties ensure reliable processing of database transactions:
     - **Atomicity:** Transactions are all-or-nothing.
     - **Consistency:** Transactions bring the database from one valid state to another.
     - **Isolation:** Transactions are executed in isolation.
     - **Durability:** Once a transaction is committed, it remains so, even in the event of a system failure.


