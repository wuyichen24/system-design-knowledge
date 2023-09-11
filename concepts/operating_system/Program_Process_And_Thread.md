# Program, Process and Thread

## Program
- **Concepts**
   - An executable file containing a set of instructions and passively stored on disk.

## Process
- **Concepts**
   - A program is in execution.
   - When a program is loaded into the memory and becomes active, the program becomes one or multiple processes.
- **Characteristics**
   - Processes are usually independent.
   - Each process has its own memory space.
   - A process is a heavyweight operation. It takes more time to create and terminate.
   - Context switching is more expensive between processes.
- **Inter-process communication**

## Thread
- **Concepts**
   - The smallest unit of execution within a process.
- **Key points**
   - **Shared memory**
      - Threads that belong to the same process share the same memory.
   - **Mutexes**
      - Mutexes are synchronization primitives that allow threads to lock and unlock access to shared resources.
      - Only one thread can hold a mutex at a time, ensuring exclusive access to the protected resource.
   - **Semaphores**
      - Semaphores are synchronization objects that allow a specified number of threads to access a resource simultaneously.
      - They are often used to control access to a limited pool of resources.
   - **Condition variables**
      - Condition variables are used to signal and coordinate threads when specific conditions are met or changed.
   - **Signal**
      - Threads can signal or notify each other when certain events occur, allowing them to respond to changes in the program's state or conditions.
   - **Message queues/Channels**
      - Threads can use message queues or channels to send messages or data to each other within the same process.
- **Inter-thread communication**
