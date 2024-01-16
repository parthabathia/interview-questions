### SQL and NoSQL Queries:

Certainly! Here are 10 SQL queries along with explanations, followed by 10 NoSQL queries and explanations:

### SQL Queries:

1. **Query: Retrieve all columns from the "employees" table for employees with a salary greater than $50,000.**

   ```sql
   SELECT * FROM employees WHERE salary > 50000;
   ```

   **Explanation:** This SQL query uses the `SELECT` statement to retrieve all columns from the "employees" table where the salary is greater than $50,000.

2. **Query: Calculate the average salary of employees in the "departments" table.**

   ```sql
   SELECT AVG(salary) FROM employees;
   ```

   **Explanation:** The `SELECT AVG()` statement is used to calculate the average salary from the "employees" table.

3. **Query: Update the job title of an employee with the ID 101 to "Senior Developer".**

   ```sql
   UPDATE employees SET job_title = 'Senior Developer' WHERE employee_id = 101;
   ```

   **Explanation:** The `UPDATE` statement modifies the job title for the employee with ID 101 to "Senior Developer" in the "employees" table.

4. **Query: Delete all records from the "customers" table where the account balance is zero.**

   ```sql
   DELETE FROM customers WHERE account_balance = 0;
   ```

   **Explanation:** The `DELETE` statement removes all records from the "customers" table where the account balance is zero.

5. **Query: Retrieve the total number of employees in each department from the "employees" table.**

   ```sql
   SELECT department_id, COUNT(*) FROM employees GROUP BY department_id;
   ```

   **Explanation:** This query uses the `SELECT COUNT(*)` statement along with `GROUP BY` to count the number of employees in each department.

6. **Query: Find the highest salary in the "employees" table.**

   ```sql
   SELECT MAX(salary) FROM employees;
   ```

   **Explanation:** The `SELECT MAX()` statement retrieves the highest salary from the "employees" table.

7. **Query: Display the unique job titles in the "employees" table.**

   ```sql
   SELECT DISTINCT job_title FROM employees;
   ```

   **Explanation:** The `SELECT DISTINCT` statement returns unique job titles from the "employees" table.

8. **Query: Join the "orders" and "customers" tables to retrieve order details along with customer information.**

   ```sql
   SELECT * FROM orders JOIN customers ON orders.customer_id = customers.customer_id;
   ```

   **Explanation:** This query uses the `JOIN` statement to combine data from the "orders" and "customers" tables based on the customer ID.

9. **Query: Calculate the total revenue generated from all orders in the "order_details" table.**

   ```sql
   SELECT SUM(quantity * unit_price) AS total_revenue FROM order_details;
   ```

   **Explanation:** The `SELECT SUM()` statement calculates the total revenue by multiplying the quantity and unit price for each order in the "order_details" table.

10. **Query: Retrieve the top 5 highest-paid employees from the "employees" table.**

    ```sql
    SELECT * FROM employees ORDER BY salary DESC LIMIT 5;
    ```

    **Explanation:** This query uses `ORDER BY` to sort employees by salary in descending order and `LIMIT` to retrieve only the top 5.

### NoSQL Queries (MongoDB):

1. **Query: Retrieve all documents from the "employees" collection where the salary is greater than $50,000.**

   ```javascript
   db.employees.find({ salary: { $gt: 50000 } });
   ```

   **Explanation:** This MongoDB query uses the `find` method to retrieve documents from the "employees" collection where the salary is greater than $50,000.

2. **Query: Calculate the average salary of employees in the "employees" collection.**

   ```javascript
   db.employees.aggregate([{ $group: { _id: null, avgSalary: { $avg: "$salary" } } }]);
   ```

   **Explanation:** The `aggregate` method with `$group` and `$avg` is used to calculate the average salary in the "employees" collection.

3. **Query: Update the job title of an employee with the ID 101 to "Senior Developer".**

   ```javascript
   db.employees.update({ employee_id: 101 }, { $set: { job_title: "Senior Developer" } });
   ```

   **Explanation:** The `update` method with `$set` modifies the job title for the employee with ID 101 in the "employees" collection.

4. **Query: Delete all documents from the "customers" collection where the account balance is zero.**

   ```javascript
   db.customers.remove({ account_balance: 0 });
   ```

   **Explanation:** The `remove` method deletes all documents from the "customers" collection where the account balance is zero.

5. **Query: Retrieve the total number of employees in each department from the "employees" collection.**

   ```javascript
   db.employees.aggregate([{ $group: { _id: "$department_id", count: { $sum: 1 } } }]);
   ```

   **Explanation:** This MongoDB query uses the `aggregate` method with `$group` and `$sum` to count the number of employees in each department.

6. **Query: Find the highest salary in the "employees" collection.**

   ```javascript
   db.employees.find().sort({ salary: -1 }).limit(1);
   ```

   **Explanation:** This query uses `find`, `sort`, and `limit` to retrieve the document with the highest salary from the "employees" collection.

7. **Query: Display unique job titles in the "employees" collection.**

   ```javascript
   db.employees.distinct("job_title");
   ```

   **Explanation:** The `distinct` method returns unique job titles from the "employees" collection.

8. **Query: Perform an aggregation to join the "orders" and "customers" collections and retrieve order details along with customer information.**

   ```javascript
   db.orders.aggregate([
     {
       $lookup: {
         from: "customers",
         localField: "customer_id",
         foreignField: "customer_id",
         as: "order_with_customer"
       }
     }
   ]);
   ```

   **Explanation:** The `$lookup` stage is used to perform a left outer join between the "orders" and "customers" collections.

9. **Query: Calculate the total revenue generated from all orders in the "order_details" collection.**

   ```javascript
   db.order_details.aggregate([{ $group: { _id: null, totalRevenue: { $sum: { $multiply: ["$quantity", "$unit_price"] } } } }]);
   ```

   **Explanation:** The `aggregate` method with `$group` and `$sum` is used to calculate the total revenue in the "order_details" collection.

10. **Query: Retrieve the top 5 highest-paid employees from the "employees" collection.**

    ```javascript
    db.employees.find().sort({ salary: -1 }).limit(5);
    ```

    **Explanation:** This MongoDB query uses `find`, `sort`, and `

limit` to retrieve the top 5 highest-paid employees from the "employees" collection.

These queries cover a range of operations in both SQL and NoSQL databases, showcasing common operations such as filtering, aggregation, updates, and joins. The MongoDB queries provided are specific to the MongoDB syntax and operations.