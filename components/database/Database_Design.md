# Database Design

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
   - *One-to-one*
   - *One-to-many*
   - *Many-to-many*

#### Step 6: Add indexes to some columns
- **Concepts**
   - Look at each table and decide which column need to be indexed based on the common queries will be run from the applications.
- **Which column needs to be indexed**
   - See [Database Indexing - Best practices](Database_Indexing.md#best-practices)

### Best practices
