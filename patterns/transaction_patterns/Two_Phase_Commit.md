# Two-Phase Commit (2PC)

- [**Motivation**](#motivation)
- [**Solution**](#solution)
   - [Concepts](#concepts)
   - [Implementation](#implementation)
- [**Pros & Cons**](#pros--cons)
   - [Pros](#pros)
   - [Cons](#cons)
- [**Consideration**](#consideration)
- [**When To Use**](#when-to-use)
- [**References**](#references)

## Motivation

## Solution
### Concepts
The coordinator uses 2 phases to coordinates participants on whether to commit or abort (roll back) a distributed transaction: 
- **Commit-Request/Voting Phase**
   - The coordinator sends a request-to-prepare message to all participants.
   - Each participant prepare the transaction and send back the aggreement message (success) or the abort message (fail) to the the coordinator.
- **Commit/Completion Phase**
   - **Success**: If the coordinator received an agreement message from all participants:
      - The coordinator sends a commit message to all the participants.
      - Each participant commits the transcation and releases all the locks.
      - Each participant sends an acknowledgement to the coordinator.
   - **Failure**: If any participant sent a abort message to the coordinator:
      - The coordinator sends a rollback message to all the participants.
      - Each participant undos the transaction and release all the locks.
      - Each participant sends an acknowledgement to the coordinator.

### Implementation

## Pros & Cons
### Pros
### Cons

## Consideration
| Topic | Consideration | Possible Solution Options |
|----|-----|-----|

## When To Use

## References
