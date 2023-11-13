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
