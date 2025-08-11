# Deadlocks

A deadlock in operating systems is a situation where two or more processes are stuck waiting for each other’s resources, and none of them can proceed.

## Real-life Analogy

Two people meet in a narrow hallway:
- Person A says, “I’ll move if you move first.”
- Person B says, “I’ll move if you move first.”
- Both wait forever → Deadlock.

## Example in Operation System

Imagine two processes:

Process 1:
- Holds Resource A
- Wants Resource B

Process 2:
- Holds Resource B
- Wants Resource A

> Since neither will release their resource until they get the other, both are stuck.

## Deadlock Conditions

Deadlock can occur if all four of these conditions hold at the same time (Coffman’s conditions):

- **Mutual Exclusion** – At least one resource is held in a non-shareable mode.
- **Hold and Wait** – A process holding at least one resource is waiting for additional resources.
- **No Preemption** – Resources cannot be forcibly taken; they must be released voluntarily.
- **Circular Wait** – A closed chain of processes exists where each holds a resource the next one needs.

## Deadlock Handling Methods

### Deadlock Prevention

- Break at least one of the four Coffman conditions.
- Example: Force processes to request all resources at once (break Hold and Wait).

### Deadlock Avoidance

- Use Banker’s Algorithm to ensure the system always stays in a “safe state”.

### Deadlock Detection and Recovery

- Let deadlock happen, then detect it and take action (kill a process, release resources).

### Ignore the Problem

- Some OSs (like many desktop systems) just ignore deadlocks if they’re rare.

<!-- Banker's Algo concept -->
<!-- RAG - Resource Allocation Graph -->