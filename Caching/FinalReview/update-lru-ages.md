## Assume you have a cache with two sets and 3 ways per set, with an LRU replacement policy. Select a way if the event would cause that way's age to update.

![LRU Cache Table](https://github.com/user-attachments/assets/f2a831e4-fae2-4c9f-9ffb-79fced759410)

### Hit in Set 0, Way 1
- **Set 0:** All ways in Set 0 update their age information.
- **Set 1:** No ways in Set 1 update.

### Miss where the item maps to Set 0
- **Set 0:** All ways in Set 0 update their age information.
- **Set 1:** No ways in Set 1 update.

### Hit in Set 1, Way 2
- **Set 0:** No ways in Set 0 update.
- **Set 1:** All ways in Set 1 update their age information.

### Miss where the item maps to Set 1
- **Set 0:** No ways in Set 0 update.
- **Set 1:** All ways in Set 1 update their age information.

> **Note:** LRU state is maintained independently for each set. Therefore, only the accessed set updates on a hit or miss.
        

