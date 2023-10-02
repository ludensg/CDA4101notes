# Computer Architecture Study Guide (CDA4150/5155)

## 1. Memory-performance gaps
- Definition and significance
- Causes and implications
- Solutions and strategies

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
