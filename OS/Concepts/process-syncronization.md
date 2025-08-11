# Process Syncronization

Process Synchronization is a mechanism in operating systems that ensures multiple processes (or threads) that share resources do not interfere with each other and produce consistent, correct results.

## Why is Process Syncronization needed ?

When multiple processes run concurrently and share resources, problems can occur — especially in a critical section.

### Critical Section

- A part of a program where the process accesses shared resources (data, files, etc.).
- If two processes execute their critical sections at the same time, race conditions can happen.

## Example Problem: Race Condition

Imagine two threads updating the same bank account balance:

Initial Balance = ₹1000
Thread 1: Deposit ₹500
Thread 2: Withdraw ₹200

If they run without synchronization:

```
Thread 1 reads balance: 1000
Thread 2 reads balance: 1000
Thread 1 adds 500 → 1500
Thread 2 subtracts 200 → 800

```

> Final balance = ₹800 ❌ (wrong, should be ₹1300).

## Goal of Syncronization

Any synchronization mechanism must satisfy the 3 requirements of a critical section solution:

- **Mutual Exclusion** - Only one process at a time can be in the critical section.
- **Progress** - If no process is in the critical section, one waiting process must enter without unnecessary delay.
- **Bounded Waiting** - A process should not wait forever to enter the critical section.

> #### Analogy
> Think of process synchronization like a public restroom with one key:
> - Only one person (process) can use it at a time (mutual exclusion).
> - If it’s empty, the next person in line gets the key (progress).
> - No one should be stuck outside forever if others keep coming in (bounded waiting).

## Methods of Syncronization

### Software-Based
- Peterson’s Algorithm
- Dekker’s Algorithm
- Bakery Algorithm

### Hardware-Based
- Test-and-Set instruction
- Compare-and-Swap instruction

### OS/Programming Constructs
- Semaphores (counting & binary)
- Mutex Locks
- Monitors
- Condition Variables

<!-- Peterson's Algorithm -->
<!-- Semaphores -->
<!-- Muutex Locks -->