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
   - May slow down write operations (from the property of non-clustered index).

### Composite index
- **Alias**
   - Multi-column index
   - Concatenated index
- **Concept**
   - The index on multiple columns.
   - Beneficial for queries that filter or sort by a specific set of columns.
   - The column order can significantly affect the composite index's usefulness.
   - The composite indexes can become large and use more storage space (Need to find balance between query performance and storage usage).
- **Strategies**
   - The column that narrows down the data most should come first in the index.

### Covering index
- **Concepts**
   - All the indexed columns are used in the select, where, and join clauses of the query.
   - Database can retrieve all the necessary information from the covering index itself without additional lookups in the table.
   - Beneficial for large tables and queries that return a small subset of columns.
   - The covering indexes can become large and use more storage space (Need to find balance between query performance and storage usage).
  
### Unique index
- **Concepts**
   - The unique index ensures values are unique in the indexed column.

### Filter index
- **Alias**
   - Partial index
   - Conditional index
- **Concepts**
   - Only creates index on a subset or specific range of data.
   - Enhances performance and save storage space when dealing with large tables where only a small portion of data is accessed frequently.

### Bitmap index
### Spatial index
### Full-text index
### Hash index

## Strategies
- Overviews
   - Finding the right indexes a balancing act between quick query responses and update costs.
