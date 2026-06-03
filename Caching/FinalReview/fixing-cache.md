## Select the cache parameters you would adjust, and how you would adjust them to resolve the following problems. You may modify more than one parameter in each row.

![Cache Parameters Table](https://github.com/user-attachments/assets/9377fb1d-7c2b-4a28-9765-ff27e0dd86ee)

| Problem | Cache Parameter Adjustment |
|----------|----------------------------|
| Too many compulsory misses | Increase **block size** (larger blocks exploit spatial locality) |
| Too many conflict misses | Increase **associativity** (reduces placement conflicts) |
| Too many capacity misses | Increase **cache size** (more data can be stored) |
| CAT (Cache Access Time) is too high | Decrease **cache size**, decrease **block size**, and/or decrease **associativity** (simplifies cache access and reduces access time) |

**Summary**
- Compulsory misses → increase block size
- Conflict misses → increase associativity
- Capacity misses → increase cache size
- High CAT → decrease cache size, block size, and/or associativity
