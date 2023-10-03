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


