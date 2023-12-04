# Task Queue

## Motivation

## Solution
### Concepts

![task_queue drawio](https://github.com/wuyichen24/system-design-knowledge/assets/8989447/fc576274-6ab8-4e2d-8dee-9c8cd7b2bef7)

- Clients add tasks into the task queue and create a new task status record.
- Task queue holds tasks as a buffer.
- Worker pulls a task from the task queue and update the corresponding task status record.
- Once worker is done (either success or fail), update the corresponding taks status record.

### Implementation
- Choose message queue
- Push vs. pull
    - Worker pulling tasks from the task queue.


## Pros & Cons
### Pros
### Cons

## Consideration

## When To Use

## Projects
- Celery: Distributed task queue for handling asynchronous tasks and scheduling.
- Taskmaster: Lightweight simple distributed queue for handling large volumes of one-off tasks.
- Huey: Redis-based task queue that aims to provide a simple, yet flexible framework for executing tasks.
- Kuyruk: Simple and easy to use task queue system built on top of RabbitMQ.
- Dramatiq: A fast and reliable alternative to Celery. It supports RabbitMQ and Redis as message brokers.
- tasq: A brokerless task queue for simple use cases.

## References
- Web Article: [Task Queues | https://www.fullstackpython.com/task-queues.html](https://www.fullstackpython.com/task-queues.html)
