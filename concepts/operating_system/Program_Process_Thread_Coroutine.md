# Program, Process, Thread and Coroutine

- [**Program**](#program)
- [**Process**](#process)
- [**Thread**](#thread)
- [**Coroutine**](#coroutine)
- [**Comparison**](#comparison)
   - [Process vs. Thread](#process-vs-thread)
   - [Coroutine vs. Thread](#coroutine-vs-thread)

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
   - Concepts
      - The mechanisms and techniques that separate processes use to exchange data, share information, or coordinate their activities.
   - Methods
      - *Pipes*
         - Pipes provide a unidirectional communication channel between two related processes, typically a parent and child process.
      - *Shared memory*
         - Processes can map a shared region of memory into their address spaces.
      - *Message queues*
         - Message queues enable processes to send messages to each other.
      - *Sockets*
         - Sockets are a network-based IPC mechanism that enables communication between processes running on different machines or locally.
      - *Signals*
         - Processes can send signals to other processes to notify them of events or trigger specific actions.
      - *File locking*
         - Processes can use file locking mechanisms to coordinate access to shared files, ensuring that only one process at a time can modify a particular file.
        
## Thread
- **Concepts**
   - The smallest unit of execution within a process.
- **Characteristics**
   - Treads are not independent.
   - Threads that belong to the same process share the same memory.
- **Inter-thread communication**
   - Concepts
      - The mechanisms and techniques that threads within the same process use to exchange data, synchronize their actions, and coordinate their execution.
   - Methods
      - *Shared memory*
         - Threads that belong to the same process share the same memory.
      - *Mutexes*
         - Mutexes are synchronization primitives that allow threads to lock and unlock access to shared resources.
         - Only one thread can hold a mutex at a time, ensuring exclusive access to the protected resource.
      - *Semaphores*
         - Semaphores are synchronization objects that allow a specified number of threads to access a resource simultaneously.
         - They are often used to control access to a limited pool of resources.
      - *Condition variables*
         - Condition variables are used to signal and coordinate threads when specific conditions are met or changed.
      - *Signal*
         - Threads can signal or notify each other when certain events occur, allowing them to respond to changes in the program's state or conditions.
      - *Message queues/Channels*
         - Threads can use message queues or channels to send messages or data to each other within the same process.

## Coroutine
- **Concepts**
   - A concurrent computational entity that is used for cooperative multitasking and asynchronous programming.
- **Characteristics**
   - *Cooperative multitasking*
      - Coroutines are cooperatively scheduled. A coroutine voluntarily yields control to other coroutines.
   - *Can be paused and resumed*
      - Allow execution to be suspended and resumed.
   - *Single thread*
      - Multiple coroutines can exist within the same thread and share the same execution context.
   - *Asynchronous operations*
      - Coroutines are often used to perform asynchronous operations.
   - *Release resources and clean up when finish*
      - When a coroutine is canceled or completes, it can automatically clean up resources and perform necessary cleanup actions.
- **Terms**
   - *Subroutine*
      - Subroutines are special cases of coroutines.
      - An instance of a subroutine only returns once, and does not hold state between invocations.
      - By contrast, a coroutine instance holds state, and varies between invocations
   - *Generators*
     
## Comparison
### Process vs. Thread
| | Processes | Threads |
|---|---|---|
| Independency | Independent | Not independent |
| Memory | Not shared | Shared | 
| Weight | Heavyweight | Lightweight |
| Context switching | More expensive | Less expensive |

### Coroutine vs. Thread
| | Coroutine | Thread |
|---|---|---|
| Multitasking | Cooperative multitasking:<li>Application handles task scheduling (context switch). | Preemptively multitasking: <li>Operating system handles task scheduling (context switch) |
| Parallelism | Do not provide:<li>Coroutines do not execute multiple tasks simultaneously. | Provide (but may not be true parallelism). |
| Need synchronization primitives (mutexes, semaphores, etc.) | No need:<li>Switching between coroutines need not involve any system calls or any blocking calls | Need |
