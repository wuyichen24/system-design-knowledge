# Database SQL - Query Optimization

## SELECT
### Select on specific columns rather than select *
- **Example**
   - Bad
     ```sql
     SELECT * FROM employees;
     ```
   - Good
     ```sql
     SELECT first_name, last_name, email, phone_number FROM employees;
     ```
   
### Avoid using SELECT DISTINCT by adding more columns in SELECT
- **Reason**
   - DISTINCT groups together related rows and then removes duplicate rows.
   - DISTINCT will call GROUP BY, but GROUP BY operation is a costly operation.
- **Example**
   - Bad
     ```sql
     SELECT DISTINCT first_name FROM employees;
     ```
   - Good
     ```sql
     SELECT first_name, last_name FROM employees;
     ```

## JOIN
### Use inner join rather than joining by where clause
- **Reason**
   - Joining by where clause creates the CROSS join/ CARTESIAN product for merging tables.
   - CARTESIAN product of two tables takes a lot of time.
- **Example**
   - Bad
     ```sql
     SELECT * from product p, order o where p.id = o.product_id;
     ```
   - Good
     ```sql
     SELECT * from product p
     INNER JOIN order o
     ON p.id = o.product_id;
     ```

## LIMIT
### Use LIMIT if possible
- **Reason**
   - LIMIT controls the number of rows to be displayed from the result set.
   - The result set needs to display only those rows that are required.
 
## IN, EXISTS
### Use EXISTS rather than IN for large dataset
- **Reason**
   - IN operator is more costly than EXISTS in terms of scans especially when the result of the subquery is a large dataset.
- **Example**
   - Bad
     ```sql
     SELECT * FROM order
     WHERE product_id IN (SELECT id FROM product);
     ```
   - Good
     ```sql
     SELECT * FROM order
     WHERE product_id EXISTS (SELECT id FROM product);
     ```

## References
- [A Detailed Guide on SQL Query Optimization](https://www.analyticsvidhya.com/blog/2021/10/a-detailed-guide-on-sql-query-optimization/)
