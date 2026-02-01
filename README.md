# Concurrency Problem Solutions

**Operating Systems Course Project – Group 6**

## Project Overview

This project is a **concurrency and synchronization simulator** developed as part of the Operating Systems course.  
It demonstrates how operating systems manage **multiple concurrent threads**, **shared resources**, and **synchronization** using classic concurrency problems.

The system demonstrates approaches that avoid common deadlocks (resource ordering, monitors) for classic synchronization problems and visually demonstrates **thread states and resource usage** through console output.

---

## Objectives

The main objectives of this project are to:

- Understand and apply **concurrency concepts**
- Implement **classic synchronization problems**
- Use proper **synchronization primitives**
- Prevent **race conditions and deadlocks**
- Compare **performance of different synchronization approaches**
- Gain practical experience with **multithreaded programming**

---

## Key Concepts Covered

- Concurrency and Parallelism
- Critical Sections
- Race Conditions
- Deadlocks and Deadlock Prevention
- Mutex Locks
- Semaphores
- Condition Variables
- Monitors
- Performance Measurement

---

## Problems Implemented

### 1️. Producer–Consumer Problem

- Synchronization between producer and consumer threads
- Shared bounded buffer
- Prevents buffer overflow and underflow
- Uses **mutex locks** and **condition variables**

Implementation details (actual):

- Uses a `Buffer` with capacity 5.
- Spawns 2 producer threads and 3 consumer threads by default.
- Synchronization implemented with `ReentrantLock` and `Condition` objects.

### 2️. Dining Philosophers Problem

- Philosophers competing for shared forks
- Demonstrates deadlock scenarios and deadlock-free solutions
- Uses **semaphores** and resource ordering

Implementation details (actual):

- Implements 5 philosophers by default.
- Uses a `Semaphore` per fork and enforces a resource ordering (pick lower-index fork first) to avoid deadlock.

### 3️. Readers–Writers Problem

- Manages concurrent access to shared data
- Multiple readers or one writer at a time
- Demonstrates fairness and priority control
- Uses **read-write locks / semaphores**

Implementation details (actual):

- Monitor-based solution using `synchronized`, `wait()` and `notifyAll()`.
- Starts 3 readers and 2 writers by default; readers may run concurrently while writers have exclusive access.

---

## System Architecture

```
os-concurrency-solutions/
├── pom.xml
├── README.md
├── LICENSE
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/
│   │           └── concurrency/
│   │               ├── Main.java
│   │               ├── ProducerConsumer.java
│   │               ├── DiningPhilosophers.java
│   │               ├── ReadersWriters.java
│   │               └── PerformanceMetrics.java
│   └── test/
│       └── java/
│           └── com/
│               └── concurrency/
│                   ├── ProducerConsumerTest.java
│                   ├── DiningPhilosophersTest.java
│                   ├── ReadersWritersTest.java
│                   └── ToDevs.java

```

---

## Technologies Used

- **Language:** Java
- **Concurrency Tools:**
  - `Thread`
  - `Runnable`
  - `synchronized`
  - `Thread`
  - `Runnable`
  - `synchronized` (monitor with `wait`/`notifyAll`)
  - `Semaphore` (for Dining Philosophers)
  - `ReentrantLock` and `Condition` (for Producer–Consumer)
  - `AtomicLong` (for performance metrics)
  - `ThreadLocalRandom`
- **Platform:** Console-based

---

## Program Flow

```
1. Run Producer–Consumer Simulation
2. Run Dining Philosophers Simulation
3. Run Readers–Writers Simulation
4. Exit
```

Notes:

- The interactive `Main` menu runs each chosen simulation for a default of 5 seconds (configurable in `Main.java`).
- Producer–Consumer uses a buffer capacity of 5, with 2 producers and 3 consumers started by default.

---

## Visualization & Output

Console-based logs show:

- Thread actions
- Resource usage
- Waiting and signaling
- Execution states

Example (Producer–Consumer output format):

```
Producer-1 produced: 42 | Buffer size: 3
Consumer-2 consumed: 17 | Buffer size: 2
```

---

## Performance Measurement

- Execution time
- Waiting time
- Throughput

Measured using:

```java
System.nanoTime()
```

Implementation detail: metrics are aggregated with `AtomicLong` counters in `PerformanceMetrics.java` and printed per-simulation.

---

## Team Roles & Contributions

| Developer                     | Responsibility            |
| ----------------------------- | ------------------------- |
| Akelisiyine Desmond Nsoh Brew | Producer–Consumer         |
| Austin Bediako Tsibuah        | Dining Philosophers       |
| Ebenezer Fuachie              | Readers–Writers           |
| Jessy Kankam Yeboah           | Integration & Performance |

---

## Testing Strategy

- Independent module testing
- Multiple-thread simulations
- Edge case validation
- Log-based verification

Testing details:

- Unit tests are included under `src/test/java/com/concurrency/` (JUnit) and are run with Maven Surefire; reports are available under `target/surefire-reports/` when tests are executed.

---

## Documentation

- Well-commented source code
- This README
- 10-page technical report

---

## Conclusion

This project demonstrates practical understanding of **Operating Systems concurrency concepts** through clean, deadlock-free implementations and structured performance evaluation.
