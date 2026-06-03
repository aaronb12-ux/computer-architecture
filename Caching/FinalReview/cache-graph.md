## Consider this graph from the book which shows block size vs. miss rate for caches of different sizes.

![Block Size vs Miss Rate Graph](https://github.com/user-attachments/assets/f273f88e-a43e-4707-ab18-a8caf9c017ac)

### 1. Explain why as the block size increases the miss rate initially decreases and then increases for the 4K cache.

Initially, increasing the block size reduces more **compulsory misses** than the number of **conflict misses** it introduces, causing the miss rate to decrease.

However, as the block size continues to increase, fewer blocks can fit in the cache. This leads to more conflict and capacity misses, eventually outweighing the reduction in compulsory misses and causing the miss rate to increase.

### 2. Explain why the effect of changing the block size is less pronounced as the cache becomes larger.

Larger caches can hold more data, so they are less sensitive to changes in block size. Because they can already store a larger portion of the working set, changing the block size has a smaller impact on the overall miss rate.

### 3. Given that the 256K cache has the lowest miss rate of all caches shown, will it always perform better than the 4K cache?

No. The graph only shows **miss rate**, not **average memory access time (AMAT)**.

While the 256K cache has a lower miss rate, larger caches typically have a higher **cache access time (CAT)**. Depending on the workload and memory access patterns, the increased access time may offset the benefit of the lower miss rate, meaning the 256K cache will not always outperform the 4K cache.
