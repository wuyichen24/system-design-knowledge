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

### B tree
- **Concepts**
   - A self-balancing tree data structure that maintains sorted data and allows for efficient insertion, deletion, and search operations.
- **Time complexity**
   - *O(logN)*
- **Strucure**
   - Root node has at least two children.
   - All internal nodes have `m/2 ~ m` children.
   - All leaves are at the same level.
   - A non-leaf node with k children contains k−1 keys.

  <img width="448" alt="output253" src="https://github.com/wuyichen24/system-design-knowledge/assets/8989447/0557b681-40e8-4389-bbad-68675884669c">

### B+ tree


## Benefits
- Speed up data retrieval without needing to scan every row in a database table.

## Strategies
- Overviews
   - Finding the right indexes a balancing act between quick query responses and update costs.
