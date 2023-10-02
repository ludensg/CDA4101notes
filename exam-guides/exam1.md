# Computer Architecture Exam 1 Study Guide (CDA4150/5155)

	*Infromation for this guide was sourced primarily from provided lecture slides, as well as from Hennessy and Patterson's Computer Architecture: A Quantitative Approach (6th Edition).*

# Table of Contents for Exam 1 Study Guide

- [Computer Architecture Exam 1 Study Guide (CDA4150/5155)](#computer-architecture-exam-1-study-guide-cda41505155)
- [Table of Contents for Exam 1 Study Guide](#table-of-contents-for-exam-1-study-guide)
  - [1. Memory-performance gaps](#1-memory-performance-gaps)
    - [Definition and Significance](#definition-and-significance)
    - [Causes and Implications](#causes-and-implications)
    - [Solutions and Strategies](#solutions-and-strategies)
  - [2. DRAM \& SRAM](#2-dram--sram)
    - [2.a. Trade-Offs \& Concepts](#2a-trade-offs--concepts)
  - [3. Memory Hierarchy](#3-memory-hierarchy)
  - [4. Cache](#4-cache)
    - [4.a. Why do we need a cache?](#4a-why-do-we-need-a-cache)
    - [4.b. What is cache?](#4b-what-is-cache)
    - [4.c. Structure](#4c-structure)
    - [4.d. How does it work?](#4d-how-does-it-work)
    - [4.e. Operations and definitions](#4e-operations-and-definitions)
    - [4.f. Comparisons of direct and associative cache](#4f-comparisons-of-direct-and-associative-cache)
    - [4.g. Write hit and miss replacement policies](#4g-write-hit-and-miss-replacement-policies)
    - [4.h. Performance with examples](#4h-performance-with-examples)
    - [4.i. Types of misses](#4i-types-of-misses)
    - [4.j. Multilevel caches (with examples)](#4j-multilevel-caches-with-examples)
    - [4.k. Optimization (prioritizing read miss vs. hit miss)](#4k-optimization-prioritizing-read-miss-vs-hit-miss)
  - [5. Locality](#5-locality)
  - [6. Hits and Misses](#6-hits-and-misses)
  - [7. Address \& Cache](#7-address--cache)
  - [8. Block size \& cache](#8-block-size--cache)
  - [9. Cache optimizations](#9-cache-optimizations)
  - [10. Software: matrix multiply with register use/reuse](#10-software-matrix-multiply-with-register-usereuse)
  - [11. Cache reuse, for matrix multiplication](#11-cache-reuse-for-matrix-multiplication)




## 1. Memory-performance gaps

The memory-performance gap, often referred to as the "memory wall", describes the growing disparity between the speed of CPU operations and the latency of memory access. As CPUs have continued to advance at a rapid pace, memory speeds have not kept up, leading to this widening gap. This section delves into the causes, implications, and potential solutions to this challenge.

![Diagram illustrating the memory-performance gap](imagesx1/memwall.png)


### Definition and Significance

- **Memory-Performance Gap**: The difference in growth rates between CPU processing speeds and memory access times. While CPU speeds have been doubling approximately every 18 months (following Moore's Law), memory latency has seen only modest improvements.
  
- **Significance**: As CPUs become faster, they often have to wait for data to be fetched from memory. This waiting period, or "stall", can significantly hamper the overall system performance, even if the CPU itself is highly efficient.

### Causes and Implications
- **Causes**:
  - **Technological Limitations**: Physical constraints in DRAM technology that limit the rate of improvements.
  - **Economic Factors**: The high cost of developing faster memory technologies can deter rapid advancements.
  - **Power Consumption**: Faster memory often requires more power, leading to thermal challenges.

- **Implications**:
  - **Stalled CPU Cycles**: The CPU spends a significant amount of time waiting for data from memory, leading to underutilization of its capabilities.
  - **Energy Inefficiency**: Waiting for memory consumes power without doing useful work, leading to wasted energy.
  - **System Bottlenecks**: The overall system performance can be bottlenecked by memory latency, regardless of how fast the CPU is.

### Solutions and Strategies

- **Caching**: Using small amounts of faster memory (cache) to store frequently accessed data, reducing the need to fetch data from main memory.
  
- **Prefetching**: Predictively loading data into cache before it's needed by the CPU.
  
- **Memory-Level Parallelism**: Accessing memory in parallel to hide latency. This refers to the ability of a processor to issue multiple memory operations (like loads and stores) to different memory locations in parallel. Instead of waiting for one memory operation to complete before starting the next, MLP allows for several memory operations to be in progress at the same time, thereby hiding or reducing the perceived memory latency.
  
- **Improved DRAM Technologies**: Developing new memory technologies that can offer faster access times, such as DDR4, DDR5, and beyond.
  
- **Near Data Processing**: Moving computation closer to where data is stored, such as processing-in-memory (PIM) techniques.

By understanding and addressing the memory-performance gap, architects and developers can design systems that make the most of both CPU and memory capabilities, leading to more efficient and performant computing systems.


## 2. DRAM & SRAM
- Definitions and differences
- Applications and use-cases

### 2.a. Trade-Offs & Concepts
- Speed vs. power consumption
- Cost vs. capacity
- Volatility and non-volatility

## 3. Memory Hierarchy
- Definition and importance
- Levels of memory hierarchy
- Access time and cost at each level

## 4. Cache
- Definition and purpose
- Structure and components

### 4.a. Why do we need a cache?
- Speeding up memory access
- Reducing memory-performance gap
- Improving CPU efficiency

### 4.b. What is cache?
- Temporary storage between main memory and CPU
- Types: L1, L2, L3

### 4.c. Structure
- Cache lines/blocks
- Tags, index, and offset

### 4.d. How does it work?
- Cache lookup process
- Cache hit vs. cache miss

### 4.e. Operations and definitions
- Read and write operations
- Direct-mapped, fully associative, and n-way set associative cache

### 4.f. Comparisons of direct and associative cache
- Advantages and disadvantages
- Up to 4-way associative cache

### 4.g. Write hit and miss replacement policies
- Write-through vs. write-back
- LRU, FIFO, random replacement

### 4.h. Performance with examples
- Cache hit ratio
- Average memory access time

### 4.i. Types of misses
- Compulsory, capacity, and conflict misses

### 4.j. Multilevel caches (with examples)
- L1, L2, L3 caches
- Interactions and coherence

### 4.k. Optimization (prioritizing read miss vs. hit miss)
- Techniques and strategies
- Impact on performance

## 5. Locality
- Temporal and spatial locality
- Importance in cache design

## 6. Hits and Misses
- Definitions and differences
- Impact on performance

## 7. Address & Cache
- Address translation
- Tag, index, and offset

## 8. Block size & cache
- Definition and significance
- Impact on cache performance

## 9. Cache optimizations
- Prefetching
  - Advantages: Reduces cache miss rate
  - Disadvantages: Can lead to unnecessary data fetch
- Cache bypassing
  - Advantages: Avoids polluting cache with non-reusable data
  - Disadvantages: Can miss potential cache hits
- Victim cache
  - Advantages: Stores blocks evicted from primary cache
  - Disadvantages: Additional hardware complexity

## 10. Software: matrix multiply with register use/reuse
- Definition and significance
- Analysis of register use and reuse

## 11. Cache reuse, for matrix multiplication
- Different matrix multiplication orders: kij, jik, etc.
- Impact on cache performance and reuse
