# Consistent Hashing

## Concepts
- A special hashing technique that when a hash table is resized, only k/n keys need to be remapped on average.
   - k is the total number of keys.
   - n is the total number of servers.
   
## Algorithm
- **Basic**
   - Create a new ring based on the range of hashing [0, h]
      - The starting point is 0 (12 o'clock's direction).
      - The ending point is h (right next to the starting point).
   - Evenly place the servers to the ring.
     
     ![ch2](https://user-images.githubusercontent.com/8989447/117731167-ea655c00-b1aa-11eb-9d61-f101e951ab7b.png)

## Operations
### Map a key to a server
- **Process**
   - Get the hash value of the key: hash(key).
   - hash(key) will be represented a position on the ring.
   - The key will assigned to the next server that appears on the circle in clockwise order from the position. 
   - If the assigned server is failed:
      - The key will be be reassigned to the next server in clockwise order.

     ![ch3](https://user-images.githubusercontent.com/8989447/117731784-f1409e80-b1ab-11eb-8d64-ecd141276d57.png)  
     ![ch4](https://user-images.githubusercontent.com/8989447/117732075-70ce6d80-b1ac-11eb-9349-f148aed9872b.png)

### Add a new server to the ring
- **Example**
   - Add server D (see diagram).
- **Process**
   - The keys which hash(key) is in the range of `[B,D]` will be moved from C to D.

     ![ch5](https://user-images.githubusercontent.com/8989447/117736418-c3ac2300-b1b4-11eb-914d-fc7c3b5ddbc6.png)

### Remove a server from the ring
- **Example**
   - Remove server A (see diagram).
- **Process**   
   - All keys that were originally resided to A will move into B.

     ![ch6](https://user-images.githubusercontent.com/8989447/117738189-ac6f3480-b1b8-11eb-95e0-71cd251a31c9.png)

## Virtual nodes
### Issues for the basic approach
- It is impossible to keep the same size of partitions on the ring for all servers when a server is add or removed.

  ![ring drawio](https://user-images.githubusercontent.com/8989447/156979379-26b333d3-1d73-4528-a8b3-49ce4374e2ff.png)

- The keys cannot be distributed evenly on the ring.

  ![ring drawio (1)](https://user-images.githubusercontent.com/8989447/156979756-5a15c1f0-ee60-4bfb-9852-824154ce2959.png)

### Concepts of virtual nodes
- Use multiple virtual nodes to represent a server on the ring (Each server is responsible for multiple partitions).
- Example
   - The virtual nodes V<sub>A1</sub>, V<sub>A2</sub> and V<sub>A3</sub> represent the server A.
   - The virtual nodes V<sub>C1</sub>, V<sub>C2</sub> and V<sub>C3</sub> represent the server C.
  
  ![ring drawio (2)](https://user-images.githubusercontent.com/8989447/156980505-0b2dd681-d91e-43ab-b01c-d227f13a71be.png)

## Benefits
- Minimize reorganization/rebalance when servers are added or removed.
