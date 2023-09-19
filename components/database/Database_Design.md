# Database Design

- [**Schema Design**](#schema-design)
   - [Steps](#steps)
      - [Step 1: Find and organize the information](#step-1-find-and-organize-the-information)
      - [Step 2: Divide the information into tables](#step-2-divide-the-information-into-tables)
      - [Step 3: Turn information items into columns](#step-3-turn-information-items-into-columns)
      - [Step 4: Specify primary keys](#step-4-specify-primary-keys)
      - [Step 5: Set up the table relationships](#step-5-set-up-the-table-relationships)
      - [Step 6: Add indexes to some columns](#step-6-add-indexes-to-some-columns)
   - [Best practices](#best-practices)

## Schema Design
### Steps
#### Step 1: Find and organize the information
- **Concepts**
   - Gather all of the types of information you might want to record in the database, such as product name and order number.
 
#### Step 2: Divide the information into tables
- **Concepts**
   - Divide your information items into major entities or subjects, such as Products or Orders. Each subject then becomes a table.

#### Step 3: Turn information items into columns 
- **Concepts**
   - Decide what information you want to store in each table. Each item becomes a field, and is displayed as a column in the table. 

#### Step 4: Specify primary keys   
- **Concepts**
   - Choose each table’s primary key. The primary key is a column that is used to uniquely identify each row.

#### Step 5: Set up the table relationships 
- **Concepts**
   - Look at each table and decide how the data in one table is related to the data in other tables. Add fields to tables or create new tables to clarify the relationships, as necessary.
- **Types of relationship**
   - *One-to-one* (1:1)
      - Each record (or row) in one table is related to exactly one record in another table, and vice versa.
   - *One-to-many* (1:N)
      - Each record in one table can be related to multiple records in another table, but each record in the second table is related to only one record in the first table.
   - *Many-to-many* (N:M)
      - Each record in one table can be related to multiple records in another table, and vice versa.
      - Create a junction table (also known as a bridge or linking table) to handle many-to-many relationship. The junction table will have 2 primary keys from 2 tables respectively.

        <img width="395" alt="Screenshot 2023-09-18 at 11 46 19 PM" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/a1e90152-54b4-487f-b03d-d852546d7087">

#### Step 6: Add indexes to some columns
- **Concepts**
   - Look at each table and decide which column need to be indexed based on the common queries will be run from the applications.
- **Which column needs to be indexed**
   - See [Database Indexing - Best practices](Database_Indexing.md#best-practices)

### Normalization
#### First Normal Form (1NF)
- **Concept**
   - Each column must have only one value, it cannot hold multiple values.
- **Example**
   - Violation (The `Department` column)
     | EmployeeID | EmployeeName | Department |
     |----|----|----|
     | 001 | John | **Sales,Finance** |
     | 002 | Mary | **Sales,Finance,HR** |

#### Second Normal Form (2NF)
- **Concept**
   - Satisfies 1NF.
   - Each non-key column (a column that is not part of the primary key) should be functionally dependent on the entire primary key.
- **Example**
   - Violation (ProductName depends on the ProductID only, not the entire composite key)
     | OrderID (PK) | ProductID (PK) | ProductName |
     |----|----|----|
     | 001 | 003 | **Fork** |
     | 001 | 005 | **Bowl** |

#### Third Normal Form (3NF)
- **Concept**
   - Satisfies 2NF.
   - Non-key columns should not depend on other non-key columns.
- **Example**
   - Violation (ManageName depends on EmployeeName)
     | EmployeeID | EmployeeName | ManagerName |
     |----|----|----|
     | 001 | John | Alex |
     | 002 | Mary | Mike |

#### Boyce-Codd Normal Form (BCNF)
#### Fourth Normal Form (4NF)
#### Fifth Normal Form (5NF) 
### Denormalization (Materialized View)
- **Concept**
   - Introduces redundancy into a relational database schema to improve query performance or simplify data retrieval.
   - Creates a redundant table to pre-join data from multiple tables.
 
     ![materialized-view-pattern-diagram](https://user-images.githubusercontent.com/8989447/154134405-95c792a7-ce84-4b8b-94a9-6dbdf145fb44.png)
     
- **Pros**
   - *Improves read performance*
   - *Simplifies queries*
   - *Reduces complexity*
- **Cons**
   - *Increases redundancy*
   - *Increases storage usage*
   - *Degrades write performance*
   - *Increases maintenance complexity*

### Best practices
