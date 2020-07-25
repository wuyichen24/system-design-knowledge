# Transaction

## Guarantees
### ACID
- **Atomicity**: Each transaction is treated as a single unit, which either succeeds completely, or fails completely.
- **Consistency**: Each transaction can only bring the database from one valid state to another and always obey database invariants (rules).
- **Isolation**: Concurrently executing transactions shouldn’t interfere with each other.
- **Durability**: Once a transaction has committed successfully, any data it has written will not be forgotten, even if there is a hardware fault or the database crashes.

### BASE (Eventual Consistency)
- **Basically Available**: Basic reading and writing operations are available as much as possible (using all nodes of a database cluster), but without any kind of consistency guarantees (the write may not persist after conflicts are reconciled, the read may not get the latest write).
- **Soft state**: Without consistency guarantees, after some amount of time, we only have some probability of knowing the state, since it may not yet have converged.
- **Eventually consistent**: If the system is functioning and we wait long enough after any given set of inputs, we will eventually be able to know what the state of the database is, and so any further reads will be consistent with our expect.

## Race Conditions
- **Dirty read**: A transaction reads the data that has not yet been committed by another transaction.
- **Dirty write**: A transaction overwrites the data that has not yet been committed by another transaction.
- **Read skew (Non-repeatable read)**: When a transaction reads the same record twice but gets different result each time.
- **Lost update**: When two transactions do read-modify-write on the same record concurrently, one of the modifications can be lost (overwritten by another).
- **Write skew**: Two transactions read the same set of objects, and then update a different subset of those objects concurrently. But the updates violate the rules defined by the application.
- **Phantom**: A write in one transaction changes the result of a search query in another transaction.
