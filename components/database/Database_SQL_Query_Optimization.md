# Database SQL - Query Optimization

- [**SELECT**](#select)
   - [Select on specific columns rather than select *](#select-on-specific-columns-rather-than-select-)
   - [Avoid using unnecessary DISTINCT condition](#avoid-using-unnecessary-distinct-condition)
- [**JOIN**](#join)
   - [Use inner join rather than joining by where clause](#use-inner-join-rather-than-joining-by-where-clause)
   - [Use inner join insteal of subquery](#use-inner-join-insteal-of-subquery)
- [**LIMIT**](#limit)
   - [Use LIMIT if possible](#use-limit-if-possible)
- [**IN, EXISTS**](#in-exists)
   - [Use EXISTS rather than IN](#use-exists-rather-than-in)
- [**GROUP BY**](#group-by)
   - [Use WHERE rather then HAVING](#use-where-rather-then-having)
- [**UNION**](#union)
   - [Use UNION ALL rather than UNION](#use-union-all-rather-than-union)

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
   
### Avoid using unnecessary DISTINCT condition
- **Reason**
   - DISTINCT groups together related rows and then removes duplicate rows.
   - DISTINCT will call GROUP BY, but GROUP BY operation is a costly operation.
- **Example**
   - Bad
     ```sql
     SELECT DISTINCT first_name FROM employees;
     ```
   - Good (add more columns to SELECT)
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

### Use inner join insteal of subquery
- **Reason**
   - Subqueries execute all the queries and load all the data to perform the processing.
   - JOINs allow RDBMS to construct an execution plan that is better for your query and can forecast what data should be loaded.
- **Example**
   - Bad
     ```sql
     SELECT * FROM products p
     WHERE p.product_id =
     (SELECT s.product_id FROM sales s
     WHERE s.customer_id = 2468 AND s.quantity_sold = 12);
     ```
   - Good
     ```sql
     SELECT * FROM products p
     INNER JOIN sales s
     ON p.product_id = s.product_id
     WHERE s.customer_id = 2468 AND s.quantity_sold = 12;
     ```

## LIMIT
### Use LIMIT if possible
- **Reason**
   - LIMIT controls the number of rows to be displayed from the result set.
   - The result set needs to display only those rows that are required.
 
## IN, EXISTS
### Use EXISTS rather than IN
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

## GROUP BY
### Use WHERE rather then HAVING
- **Reason**
   - Using WHERE before GROUP BY could narrow down the rows need to be grouped.
- **Example**
   - Bad
     ```sql
     SELECT customer_id,count(customer_id)
     FROM sales
     GROUP BY customer_id
     HAVING customer_id != '16' AND customer_id != '2';
     ```
   - Good
     ```sql
     SELECT customer_id,count(customer_id)
     FROM sales
     WHERE customer_id != '16'
     AND customer_id !='2'
     GROUP BY customer_id;
     ```

## UNION
### Use UNION ALL rather than UNION
- Reason
   - UNION removes duplicate records when merging the data.
   - UNION ALL displays the data with duplicates.
- Example
   - Bad
     ```sql
     SELECT customer_id
     FROM sales
     UNION
     SELECT customer_id
     FROM customers;
     ```
   - Good
     ```sql
     SELECT customer_id
     FROM sales
     UNION ALL
     SELECT customer_id
     FROM customers;
     ```
    
## References
- [A Detailed Guide on SQL Query Optimization](https://www.analyticsvidhya.com/blog/2021/10/a-detailed-guide-on-sql-query-optimization/)
