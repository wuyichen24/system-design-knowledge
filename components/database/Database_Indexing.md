# Database Indexing

## Concepts
- A data structure that speeds up data retrieval operations.
- Indexes are typically stored on disk.
- Indexes are associated with a table.

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

## Benefits
- Speed up data retrieval without needing to scan every row in a database table.

## Strategies
- Overviews
   - Finding the right indexes a balancing act between quick query responses and update costs.
