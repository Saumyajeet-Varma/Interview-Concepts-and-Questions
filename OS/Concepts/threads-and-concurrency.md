# Thread

A thread is the smallest unit of execution within a process.

- It shares memory space of the parent process (code, data, files).
- It has its own:
    - Program Counter (PC)
    - Registers
    - Stack (for function calls and local variables)

> This makes threads faster to create and switch than processes because they don’t need separate memory allocation.

## Process vs Thread

- A process is like an entire program running (with its own memory, files, etc.).
- A thread is a lightweight worker inside that process that runs part of the program’s instructions.

| **Aspect**    | **Process**                              | **Thread**                                                  |
| ------------- | ---------------------------------------- | ----------------------------------------------------------- |
| Memory Space  | Has its own memory space.                | Shares memory space with other threads in the same process. |
| Overhead      | High (needs separate memory allocation). | Low (reuses process memory).                                |
| Communication | Needs Inter-Process Communication (IPC). | Communicates directly via shared variables.                 |
| Creation Time | Slower.                                  | Faster.                                                     |
| Example       | Chrome running as a process.             | Each Chrome tab as a separate thread in the same process.   |

> A process is like a restaurant kitchen (its own space, equipment, resources). <br> Threads are like chefs in the same kitchen — they can work on different tasks but share the same ingredients and tools.

## Types of Threads

- **User-Level Threads (ULT)** – Managed by a user-space library (fast, but if one thread blocks, the whole process blocks).
- **Kernel-Level Threads (KLT)** – Managed directly by the OS kernel (slower to create, but more control).
- **Hybrid Threads** – Mix of both (used in modern OSes).

# Concurrency

Concurrency means doing multiple things in overlapping time periods — not necessarily at the exact same moment, but making progress on more than one task at once.

> In operating systems, concurrency is about managing multiple tasks (processes or threads) so that they appear to run simultaneously, even if the CPU is actually switching between them quickly.

## Key Idea

- **Parallelism**: Actually running multiple tasks at the same time (needs multiple CPUs/cores).
- **Concurrency**: Handling multiple tasks at once by interleaving execution (can happen even on a single CPU via context switching).

| Feature            | **Concurrency**                                                        | **Parallelism**                                                            |
| ------------------ | ---------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Meaning**        | Multiple tasks *in progress* at the same time (overlapping execution). | Multiple tasks *executing* at the same time.                               |
| **Hardware Needs** | Can work on a **single CPU** via time-slicing (context switching).     | Requires **multiple CPUs/cores**.                                          |
| **Goal**           | Better **task management** and responsiveness.                         | Faster **task completion** through actual simultaneous execution.          |
| **Example**        | Switching between boiling water and toasting bread (one cook).         | Two cooks — one boils water while the other toasts bread at the same time. |
| **Execution**      | Tasks *appear* to run at once, but may be interleaved.                 | Tasks truly run at the exact same moment.                                  |

### Visual Representation

```
Concurrency (1 CPU core, time-sliced):
A  A  B  A  B  B  A  B
Task A and Task B share CPU time in turns.

Parallelism (2 CPU cores):
Core 1: A  A  A  A  A
Core 2: B  B  B  B  B
Tasks A and B run simultaneously.

```

> - Parallelism is a subset of concurrency.
> - You can have concurrency without parallelism (single-core CPU multitasking).
> - You can have parallelism with concurrency (multi-core CPU running multiple threads that also multitask).

