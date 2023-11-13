# Database SQL - Query Optimization

## SELECT
### Select on specific columns rather than select *
- Example
   - Good
     ```sql
     SELECT first_name, last_name, email, phone_number FROM employees;
     ```
   - Bad
     ```sql
     SELECT * FROM employees;
     ```
### Avoid using SELECT DISTINCT
- Reason
   - DISTINCT groups together related rows and then removes duplicate rows.
   - DISTINCT will call GROUP BY, but GROUP BY operation is a costly operation.
