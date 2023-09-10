# Database Indexing

- [**Concepts**](#concepts)
- [**Benefits**](#benefits)
- [**Data structure**](#data-structure)
   - [B-tree](#b-tree)
   - [B+ tree](#b-tree-1)
   - [Comparison between B-tree and B+ tree](#comparison-between-b-tree-and-b-tree)
- [**Main categories**](#main-categories)
   - [Clustered index](#clustered-index)
   - [Non-clustered index](#non-clustered-index)
   - [Comparison between clustered index and non-clustered index](#comparison-between-clustered-index-and-non-clustered-index)
- [**Types**](#types)
   - [Primary index](#primary-index)
   - [Secondary index](#secondary-index)
   - [Composite index](#composite-index)
   - [Covering index](#covering-index)
   - [Unique index](#unique-index)
   - [Filter index](#filter-index)
   - [Bitmap index](#bitmap-index)
   - [Spatial index](#spatial-index)
   - [Full-text index](#full-text-index)
   - [Hash index](#hash-index)
- [**Use case**](#use-cases)
   - [Search](#search)
   - [SQL optimization](#sql-optimization)

## Concepts
- A data structure that speeds up data retrieval operations.
- Indexes are typically stored on disk.
- Indexes are associated with a table.

## Benefits
- Speed up data retrieval without needing to scan every row in a database table.

## Data structure
- B-tree
- B+ tree (Typical)
- Bitmap
- Hash map

### B-tree
- **Concepts**
   - A self-balancing tree data structure that maintains sorted data and allows for efficient insertion, deletion, and search operations.
- **Time complexity**
   - *O(logN)*
- **Strucure**
   - Root node has at least two children.
   - All internal nodes have `m/2 ~ m` children.
   - All leaves are at the same level.
   - A non-leaf node with `k` children contains `k−1` keys.

  ![80327ae8-389b-4fa7-81ad-47d7db9afad5_1350x428](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/013263dc-d108-4dd5-a6ab-19b340da6c38)

### B+ tree
- **Concepts**
   - A variant of B-tree, the main difference is data is stored in leaf nodes.
   - Storing data for efficient retrieval in a block-oriented storage context.
   - B+ trees have very high fanout (Reduces the number of I/O operations required to find an element in the tree).
- **Strucure**
   - Internal nodes don't store data, they only contains keys and pointers to other nodes.
   - Leaf nodes stores data (or pointers to data) and the pointers to next leaf node.
   - All leaf nodes are linked together in a linked list.
   - Every key appears twice, once in the internal nodes and once in the leaf nodes.

  ![cde45cda-7d59-4e99-88e8-a3e06dc3ceb0_1532x508](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/a69f3c2e-aa3b-452e-8ab4-1d7f131fb2d6)
 
### Comparison between B-tree and B+ tree
| | B-tree | B+ tree |
|---|---|---|
| Structure | Both leaf and internal nodes store keys and data. | Only leaf nodes store data. |
| Data accessibility | Data can be accessed directly from both leaf and internal nodes. | Data can only be accessed by traversing to leaf nodes. |
| Efficiency | Slightly less efficient for range queries | More efficient for range queries. |
| Insertion and deletion | Slightly more complex | Slightly more efficient |
| Space utilization | Might be less efficient. | More space efficient. |
| Use cases | Useful for database systems where data retrieval is usually targeted (e.g., specific key). | More commonly used in database and file systems where range queries are more common. |

## Main categories
### Clustered index
- **Concepts**
   - Determines the physical order of rows.
   - One table can have only one clustered index.
   - Adding or altering the clustered index can be time-consuming.
   - Only need 1 disk read (index and data are one and the same).
   - The clustered index could be based on any column or set of columns, not necessarily the primary key.
- **Strategy of selection**
   - Choose a unique, sequential key (That is the reason why the primary key is selected as the clustered index by default).
- **Exceptions**
   - In PostgreSQL, data is stored in the order it was inserted, not based on the clustered index or any other index (You have to run `CLUSTER` command).   
     
### Non-clustered index
- **Concepts**
   - Determines the logical order of rows.
   - One table can have multiple clustered indexes.
   - Maintains a list of key-value pairs:
      - Key: Values in the column.
      - Value: A pointer indicating the location of the row.
   - Only need 2 disk reads (access the index and access the data).

### Comparison between clustered index and non-clustered index
| | Custered index | Non-clustered index |
|---|---|---|
| Order of row | Physical order | Logical order |
| Number limitation | Allow only one | Allow multiple |
| Number of disk read | 1 | 2 |
| Pros | | <li>You can create multiple non-clustered indexes based on different types of queries.<li>Speed up read operations. |
| Cons | <li>You can only create one clustered index. | <li>Slow down write operations (each index must be updated whenever data is modified in the table).  |

## Types
### Primary index
- **Concepts**
   - The clustered index on the primary-key column.

### Secondary index
- **Concepts**
   - The non-clustered index on a non-primary-key column.
- **Cons**
   - May slow down write operations (from the property of non-clustered index).

### Composite index
- **Alias**
   - Multi-column index
   - Concatenated index
- **Concept**
   - The index on multiple columns.
   - The column order can significantly affect the composite index's usefulness.
- **Cons**
   - The composite indexes can become large and use more storage space (Need to find balance between query performance and storage usage).
- **Strategies**
   - The column that narrows down the data most should come first in the index.
- **Use cases**
   - Queries that filter or sort by a specific set of columns.

### Covering index
- **Concepts**
   - All the indexed columns are used in the select, where, and join clauses of the query.
   - Database can retrieve all the necessary information from the covering index itself without additional lookups in the table.
- **Cons**
   - The covering indexes can become large and use more storage space (Need to find balance between query performance and storage usage).
- **Use cases**
   - Large tables and queries that return a small subset of columns.
  
### Unique index
- **Concepts**
   - The unique index ensures values are unique in the indexed column.

### Filter index
- **Alias**
   - Partial index
   - Conditional index
- **Concepts**
   - Only creates index on a subset or specific range of data.
- **Use cases**
   - Dealing with large tables where only a small portion of data is accessed frequently.

### Bitmap index
- **Concept**
   - Each unique value of the column gets its own bitmap, where the number of bits corresponds to the number of rows.
- **Pros**
   - More efficient storage useage.
   - Handle complex queries involving multiple predicates efficiently using bitwise operations (`AND`, `OR`, `NOT`).
- **Cons**
   - May slow down write operations.
- **Use cases**
   - Dealing with columns that have a limited number of distinct values (like status, yes/no).

### Spatial index
- **Concepts**
   - Used for indexing multi-dimensional objects (geographical coordinates, polygons).
- **Pros**
   - Speed up spatial queries, like nearest neighbor searches or range searches.
- **Data structure**
   - R-trees (most common)
   - Quad-trees

### Full-text index
- **Concepts**
   - Handle searches in a text column (large volumes of text).
   - Full-text indexes work by breaking the text into or tokens, and then building an index over these tokens.
- **Pros**
   - Speed up complex search queries that involve multiple words, phrases, or different forms of a word.
- **Cons**
   - May slow down write operations.
   - May use more storage.
- **Data structure**
   - Inverted index
      - Inverts a page-centric schema (page->words) into a keyword-centric schema (word->pages).
  
### Hash index
- **Concepts**
   - Uses a hash function to map keys to specific locations in an index.
- **Cons**
   - Not well-suited for range-based queries.
- **Use cases**
   - Well-suited for equality comparisons, such as "=", where the search key is exactly equal to the indexed key.

## Use cases
### Search
- **Point search**
   - Searches on a specific attribute or key.
- **Range search**
   - Search on a range of values.
- **Prefix search**
   - Search on prefix.
- **Geo-location search**
   - Geohashes are a form of spatial index that divides the Earth into a grid.
   - Each cell in the grid is assigned a unique hash, and points within the same cell share the same hash prefix.
- **Text search**
   - Searches within a large string of text.

### SQL optimization
- **JOIN**
   - If there's an index on the columns being joined, the database can quickly identify matching records without scanning every row in both tables.
- **ORDER BY**
   - If there's an index on the columns being ordered by, the index will store the rows in that specific order, reducing the need for the database to sort the data whenever the query is run.
- **GROUP BY**
   - If we frequently group results by a certain column, the database can utilize an index on that column to group the rows more quickly.

## Best practices
- **Have a clear understanding of the application's requirements**
   - Analysis of the application’s workload.
   - Identify the most common queries and understand how frequently they are used.
   - Determine the application's read-to-write ratio:
      - Read-heavy: Can use more indexes.
      - Write-heavy: Use less indexes.
- **Choose the right columns**
   - Create indexes on the columns are frequently used in WHERE clauses, ORDER BY clauses, JOIN conditions, or used for sorting and grouping data.
   - The column that narrows down the data most should be indexed first.
- **Use different types of indexes properly**
   - Composite index: Use when multiple columns are involved in WHERE clause.
   - Covering index: Use when querying a large table but only need to return a small subset of columns.
   - Unique index: Use on the columns need to have unique values.
   - Filter index: Use when querying a large table but only need to get a small portion of data.
   - Bitmap index: Use on the columns that have a limited number of distinct values.
   - Full-text index: Use when querying a text column frequently.
- **Balance the trade-off**
   - The trade-off between query efficiency (read) and data modification (write).
   - The trade-off between query efficiency (read) and storage usage.
- **Regularly monitor and optimize indexes**
   - Use database built-in tools.
   - Check the slow query log.
- **Drop unused indexes**
