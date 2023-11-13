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
```

![0_rFMChX4SAmQ9RzF9](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/60eb4295-671b-497c-b46f-6826e0bbdf8f)

## Inner Join
- Venn diagram

  <img width="167" alt="Screenshot 2023-11-12 at 10 43 14 AM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/db735808-7234-438b-a402-9a2cb5383236">

- SQL example
  ```sql
  SELECT * FROM TableA a
  INNER JOIN TableB b
  ON a.key = b.key
  ```
- Result example

  ![inner_join](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/3a90e609-7f63-4b9e-bee0-d9c65a1f1f00)

## Outer Join
### Left Join
- Venn diagram

  <img width="161" alt="Screenshot 2023-11-12 at 4 30 24 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/69652a5e-baf3-489a-b2b8-4273e75fb7e3">

- SQL example
  ```sql
  SELECT * FROM TableA a
  LEFT JOIN TableB b
  ON a.key = b.key
  ```
- Result example

  ![left_join](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/d2c05ea8-b5f6-4df5-9d92-520479250f42)
