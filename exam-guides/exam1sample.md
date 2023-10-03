# Computer Architecture Exam 1 Sample Questions (CDA4150/5155)

1. **What is the purpose of a computer's memory hierarchy?**
   - To provide memory storage with varying speeds and sizes to optimize both performance and cost. The hierarchy typically ranges from fast, small, and expensive registers to slower, larger, and cheaper main memory and secondary storage.

2. **Define and differentiate between SRAM and DRAM.**
   - **SRAM (Static RAM)**: Uses flip-flops to store data, faster, more expensive, and consumes less power. Often used for cache memory.
   - **DRAM (Dynamic RAM)**: Uses capacitors to store data, slower, less expensive, and requires periodic refreshing. Commonly used for main memory.

3. **Explain the concept of "Locality of Reference."**
   - Refers to the tendency of a processor to access the same set of memory locations repetitively over a short period. It encompasses two main types: temporal (same location accessed multiple times) and spatial (adjacent locations accessed sequentially).

4. **What are the different types of cache misses? Describe each.**
   - **Compulsory Miss**: The first access to a memory block will always result in a miss.
   - **Capacity Miss**: Occurs when the cache cannot contain all the blocks needed during program execution.
   - **Conflict Miss**: Occurs in set-associative and direct-mapped caches when multiple blocks compete for the same set or line.

5. **How does a direct-mapped cache work?**
   - Each memory block is mapped to a specific line in the cache. The mapping is usually done using modulo arithmetic.

6. **Describe the set-associative cache. How does it differ from a direct-mapped cache?**
   - Memory blocks are mapped to a specific set in the cache, and within that set, they can be placed in any line. It offers a balance between the flexibility of fully associative and the simplicity of direct-mapped caching.

7. **What is a fully associative cache?**
   - Any block of main memory can be placed in any line of the cache, offering maximum flexibility in block placement.

8. **Explain the concept of "write policies" in cache memory.**
   - Determines how writes to the cache are propagated to main memory. The two main policies are write-through and write-back.

9. **Differentiate between write-through and write-back policies.**
   - **Write-through**: Data is written to both the cache and main memory simultaneously.
   - **Write-back**: Data is written only to the cache. The write to main memory is deferred until the cache block is replaced.

10. **What is the significance of the "dirty bit" in cache memory?**
   - Indicates whether a cache line has been modified (written to) and not yet updated in main memory. Used in write-back caches to determine if a block needs to be written to main memory when replaced.

11. **Describe the process of "cache initialization."**
   - Involves setting up the cache for use, typically by marking all entries as invalid or clearing them.

12. **Explain the concept of "cache coherence."**
   - Ensures that all processors in a multi-processor system have a consistent view of memory. If one processor updates a location in its cache, other processors' caches are updated or invalidated.

13. **What are the challenges associated with multi-level caches?**
   - Complexity in managing multiple cache levels, ensuring coherence, and deciding which level to fetch data from or write data to.

14. **Describe the working of a two-level cache system.**
   - Consists of L1 (closer to the CPU) and L2 caches. L1 is faster but smaller, while L2 is larger but slower. Data is first searched in L1, and if not found, then in L2.

15. **What is the significance of the LRU (Least Recently Used) policy in cache management?**
   - It's a replacement policy that replaces the least recently accessed block, based on the assumption that if a block hasn't been used recently, it's less likely to be used in the near future.

16. **Explain the concept of "virtual memory."**
   - An abstraction that provides an "idealized abstraction of the storage resources that are actually available on a given machine."

17. **How does paging work in virtual memory?**
   - Memory is divided into fixed-size pages. When a program needs a page that's not in physical memory, it's brought in from secondary storage, leading to a page fault if not found.

18. **Describe the significance of the Translation Lookaside Buffer (TLB).**
   - A cache for page table entries. It speeds up the virtual-to-physical address translation by storing recent translations.

19. **What are the different types of page table entries?**
   - Typically include the physical page number, valid bit, dirty bit, access permissions, and other control bits.

20. **Explain the concept of "page replacement algorithms."**
   - Determine which page to evict when a new page needs to be loaded into memory. Common algorithms include FIFO, LRU, and Optimal.

21. **Differentiate between FIFO, LRU, and Optimal page replacement algorithms.**
   - **FIFO**: Replaces the oldest page in memory.
   - **LRU**: Replaces the least recently used page.
   - **Optimal**: Replaces the page that won't be used for the longest time in the future (mostly theoretical).

22. **What is the significance of the "valid bit" and "reference bit" in page table entries?**
   - **Valid bit**: Indicates if the page is in physical memory.
   - **Reference bit**: Indicates if the page has been accessed recently.

23. **Describe the working of a demand-paged virtual memory system.**
   - Pages are only brought into physical memory when they are needed (on-demand), leading to efficient use of memory.

24. **What are the challenges associated with demand paging?**
   - Can lead to high page fault rates if not managed properly, resulting in performance degradation.

25. **Explain the concept of "page faults" and how they are handled.**
   - Occurs when a program accesses a page that's not in physical memory. The OS interrupts, saves the state of the process, loads the required page into memory, and then resumes the process.


26. **Explain three Cache Optimization methods, and explain advantages and disadvantages**


## Cache Optimization Methods

### 1. **Larger Cache Size**

#### Advantages:
- **Higher Hit Rate:** A larger cache can store more data, which increases the likelihood of a cache hit.
- **Reduced Main Memory Access:** With more data stored in the cache, there's a reduced need to access slower main memory, leading to faster overall performance.

#### Disadvantages:
- **Increased Cost:** Larger caches require more silicon area, which increases manufacturing costs.
- **Higher Power Consumption:** Larger caches consume more power, leading to increased energy costs and potential thermal issues.
- **Increased Access Time:** As cache size grows, the time to search and access the cache might increase, which could offset some of the performance benefits.

### 2. **Higher Associativity (N-way Set Associative Cache)**

#### Advantages:
- **Reduced Conflict Misses:** Higher associativity reduces the chances of multiple memory blocks competing for the same cache line.
- **Improved Flexibility:** Provides a balance between the rigidness of direct-mapped caches and the flexibility of fully associative caches.

#### Disadvantages:
- **Complexity:** Increased associativity requires more complex hardware to determine which set an item should be placed in and which block within the set should be replaced.
- **Increased Access Time:** Higher associativity can lead to longer cache access times due to the need to search multiple blocks within a set.
- **Higher Power Consumption:** Searching multiple blocks can consume more power.

### 3. **Prefetching**

#### Advantages:
- **Reduced Cache Misses:** By predicting and loading data into the cache before it's needed, prefetching can reduce the number of cache misses.
- **Improved Utilization:** Prefetching can make better use of available bandwidth by fetching data during idle times.

#### Disadvantages:
- **Wasted Bandwidth:** Incorrect prefetch predictions can lead to unnecessary data being loaded into the cache, wasting memory bandwidth.
- **Cache Pollution:** Prefetching data that isn't used can displace useful data from the cache, leading to increased cache misses.
- **Complexity:** Implementing effective prefetching algorithms requires sophisticated hardware and/or software mechanisms.


# Further Review

## Cache Architecture and Performance

### Architecture of Cache

Cache memory is a high-speed volatile computer memory that provides high-speed data access to the processor and stores frequently used computer programs, applications, and data. The architecture of cache memory involves several components:

- **Cache Lines:** The smallest unit of cache storage. Each line contains a block of data copied from main memory and some control bits.
- **Tags:** Used to determine if a particular block of main memory is in the cache.
- **Valid Bit:** Indicates whether the associated line in the cache contains valid data.
- **Dirty Bit:** Used in write-back caches to indicate that the line has been modified and needs to be written back to main memory.
- **Set:** A group of one or more cache lines. In set-associative caches, a block can be placed in any line within a specific set.
- **Replacement Policy:** Determines which line to replace when bringing in new data. Common policies include LRU (Least Recently Used), FIFO (First-In-First-Out), and Random.

### Multilevel Cache Performance (CPI)

Modern processors often use a multilevel cache design, with two or more levels of caches. The performance of these caches can be measured using the CPI (Cycles Per Instruction):

- **L1 Cache:** The first level of cache, closest to the CPU core. It's the smallest and fastest cache.
- **L2 Cache:** Larger than L1 and slower, but still faster than main memory. It acts as a backup for L1 cache.
- **L3 Cache:** Even larger and slower than L2, often shared among multiple cores.

The overall CPI can be affected by the hit rates and access times of these caches. A miss in the L1 cache that hits in the L2 cache is faster than a miss that goes all the way to main memory.

### Write Miss vs. Read Miss Prioritization

When a cache miss occurs, the system must decide how to handle it. The prioritization between write misses and read misses can impact system performance:

- **Write Miss:** Occurs when the system tries to write data to a cache line that isn't present in the cache.
  - **Handling:** Depending on the write policy, the system might write the data to main memory directly (write-through) or allocate a new line in the cache for the data (write-allocate).
- **Read Miss:** Occurs when the system tries to read data that isn't present in the cache.
  - **Handling:** The system fetches the data from main memory or a lower-level cache and brings it into the cache.

**Prioritization:**

- **Prioritizing Write Misses:** Can reduce the risk of data inconsistency and ensure that data in main memory is up-to-date. However, it might introduce delays for read operations.
- **Prioritizing Read Misses:** Can improve the perceived speed of the system, especially for read-heavy workloads. However, it might delay the propagation of written data to main memory.

The optimal prioritization often depends on the specific workload and system architecture. Some systems might prioritize read misses to ensure fast data access, while others might prioritize write misses to ensure data consistency and coherency.


## Cache Optimization Techniques

### 1. Small and Simple Caches

Small and simple caches prioritize speed by reducing the complexity and size of the cache, making them especially suitable for Level-1 (L1) caches.

#### Advantages:
- **Fast Access Times:** Due to their simplicity and reduced size, these caches can be accessed more quickly.
- **Lower Latency:** Simplified design means fewer cycles are needed to retrieve data.
- **Power Efficiency:** Smaller caches consume less power.

#### Disadvantages:
- **Limited Storage:** Their small size means they can't store as much data, leading to potentially higher miss rates.
- **Frequent Evictions:** Due to limited storage, data might be evicted more often, leading to more cache misses.

### 2. Way Predicting Caches

Way predicting caches predict which "way" of a set-associative cache will be accessed, allowing the cache to only read the predicted way, thereby saving power and potentially improving access time.

#### Advantages:
- **Reduced Power Consumption:** Only a subset of the cache is accessed, saving power.
- **Faster Access:** By predicting the correct way, the cache can reduce the time taken to access data.

#### Disadvantages:
- **Prediction Overhead:** The mechanism to predict the way adds complexity.
- **Prediction Errors:** Incorrect predictions can lead to performance penalties.

### 3. Pipelined and Banked Caches

Pipelining allows cache accesses to be broken down into stages, much like CPU pipelining. Banked caches divide the cache into multiple banks that can be accessed independently.

#### Advantages:
- **Increased Throughput:** Multiple cache accesses can be in different stages of completion simultaneously.
- **Parallel Access:** In banked caches, different banks can be accessed in parallel, improving cache bandwidth.
- **Reduced Contention:** By allowing simultaneous accesses to different banks, banked caches reduce contention.

#### Disadvantages:
- **Complexity:** Both pipelining and banking add complexity to cache design.
- **Potential for Pipeline Stalls:** Just like with CPU pipelining, certain conditions can cause pipeline stalls, reducing the efficiency of pipelined caches.



