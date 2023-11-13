# Database SQL - Join

## Overview
```mermaid
graph LR;
  A["Join"] --> B1["Inner Join"];
  A --> B2["Outer Join"];
  A --> B3["Cross Join"];
  A --> B4["Self Join"];
  B2 --> C1["Left Join (Left Outer Join)"];
  B2 --> C2["Right Join (Right Outer Join)"];
  B2 --> C3["Full Join (Full Outer Join)"];
  C1 --> D1["Left Join Excluding Inner Join"];
  C2 --> D2["Right Join Excluding Inner Join"];
  C3 --> D3["Full Join Excluding Inner Join"];
```

![0_rFMChX4SAmQ9RzF9](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/60eb4295-671b-497c-b46f-6826e0bbdf8f)

## Inner Join
- **Venn diagram**

  <img width="167" alt="Screenshot 2023-11-12 at 10 43 14 AM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/db735808-7234-438b-a402-9a2cb5383236">

- **SQL example**
  ```sql
  SELECT * FROM TableA a
  INNER JOIN TableB b
  ON a.key = b.key;
  ```
- **Result example**

  ![inner_join](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/3a90e609-7f63-4b9e-bee0-d9c65a1f1f00)

## Outer Join
### Left Join
- **Venn diagram**

  <img width="161" alt="Screenshot 2023-11-12 at 4 30 24 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/69652a5e-baf3-489a-b2b8-4273e75fb7e3">

- **SQL example**
  ```sql
  SELECT * FROM TableA a
  LEFT JOIN TableB b
  ON a.key = b.key;
  ```
- **Result example**

  ![left_join](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/d2c05ea8-b5f6-4df5-9d92-520479250f42)

- **Notes**
   - All the records from the left table will be included into the result, even if there is no matching on the right table.

### Left Join Excluding Inner Join
- **Venn diagram**

  <img width="164" alt="Screenshot 2023-11-12 at 6 52 51 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/d1554344-3420-454e-bfa2-b09a925f6385">
  
- **SQL example**
  ```sql
  SELECT * FROM TableA a
  LEFT JOIN TableB b
  ON a.key = b.key
  WHERE b.key IS NULL;
  ```
- **Result example**

  ![left_join_excluding](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/10a8a681-7fb8-4e86-a850-171313a5751a)

### Right Join
- **Venn diagram**

  <img width="162" alt="Screenshot 2023-11-12 at 7 07 27 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/37df0edb-1394-463e-8a9d-7c5f7782ceb5">
  
- **SQL example**
  ```sql
  SELECT * FROM TableA a
  RIGHT JOIN TableB b
  ON a.key = b.key;
  ```
- **Result example**

  ![right_join](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/22f48466-6138-4b5d-9820-0ca36c0c781c)

### Right Join Excluding Inner Join
- **Venn diagram**

  <img width="162" alt="Screenshot 2023-11-12 at 7 08 02 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/422debf3-0722-46f6-bc7c-af54b3ee194e">
  
- **SQL example**
  ```sql
  SELECT * FROM TableA a
  RIGHT JOIN TableB b
  ON a.key = b.key
  WHERE a.key IS NULL;
  ```
- **Result example**

  ![right_join_exluding](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/26c57270-b4f6-42d9-b3a8-7df2d1ed6ce3)

### Full Join
- **Venn diagram**

  <img width="162" alt="Screenshot 2023-11-12 at 7 08 34 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/08cae06d-6b85-48cf-8721-6d8fa715ed6b">
  
- **SQL example**
  ```sql
  SELECT * FROM TableA a
  FULL OUTER JOIN TableB b
  ON a.key = b.key;
  ```
- **Result example**

  ![full_join](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/2027992b-f0a1-4d98-b266-a8b48c14ba8f)

### Full Join Excluding Inner Join
- **Venn diagram**
  
  <img width="163" alt="Screenshot 2023-11-12 at 7 09 20 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/a9c6f49b-7d19-4721-9a4e-d6be982f1584">

- **SQL example**
  ```sql
  SELECT * FROM TableA a
  FULL OUTER JOIN TableB b
  ON a.key = b.key
  WHERE a.key IS NULL or b.key IS NULL;
  ```
- **Result example**

  ![full_join_exluding](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/b1b7a82a-636e-4c32-8342-3df55a789b2e)

  
## Cross Join
- **SQL example**
  ```sql
  SELECT * FROM TableA a
  CROSS JOIN TableB b;
  ```
- **Result example**

  ![cross_join](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/b994df3a-2f18-455e-bc90-7de5491a6731)

## Self Join
- **SQL example**
  ```sql
  SELECT * FROM TableA a1
  FULL OUTER JOIN TableA a2
  ON a1.column1 = a2.column2;
  ```
- **Result example**
   - Original table
     | ID | Name | ManagerID |
     |----|----|----|
     | 456 | Robert | |
     | 383 | Cook | 222 |
     | 777 | Daniel | 222 |
     | 123 | Smith | 456 |
     | 222 | William | 456 |
   - Result
     | ID | Name | ManagerID | Manager |
     |----|----|----|----|
     | 456 | Robert | | |
     | 383 | Cook | 222 | William |
     | 777 | Daniel | 222 | William |
     | 123 | Smith | 456 | Robert |
     | 222 | William | 456 | Robert |
