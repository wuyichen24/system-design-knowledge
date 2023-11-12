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
  ```
  SELECT * FROM TableA a
  INNER JOIN TableB b
  ON a.key = b.key
  ```
- Result example

  ![inner_join](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/bc3b8bf5-5b3c-4a70-8ce4-76f5f2a15e85)

## Outer Join
