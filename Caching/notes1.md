## Memory Technologies

When building a CPU there are many different technologies that we can use to store information.

Each of these technologies has different tradeoffs in terms of cost, speed, energy usage, and data density.

Ideally we would like memory that is large, fast, and cheap, but no single technology fits that bill.

We keep the values that we utilize regularly close to the CPU, inside of the fast memory.

**From most expensive, fastest, least energy efficient, least dense to cheapest, slowest, most energy efficient, and most dense:**
1. Registers
2. SRAM
3. DRAM
4. SSD
5. HDD

---

## What is a Cache?

A cache is a smaller, faster memory component inserted between main memory and the CPU that stores values recently accessed in memory.

To the CPU, the cache is invisible.

Requests to memory are intercepted by the cache and if the cache has the desired value, it is given to the CPU without accessing main memory.

If the value is missing, the cache retrieves the value from memory, stores it inside itself, and then gives the value to the CPU.

### The Idea of Caching Can Be Extended Beyond the Cache Itself:

- Main memory serves as a cache for the hard drive
- Registers serve as a cache for the cache

### Caching is Also Used in the Internet:

Servers will cache web pages that are accessed and serve up the cached pages instead of having to go to the primary server every time. This saves time and reduces network traffic.

---

## Why Caching Works

Caching works because programs exhibit **spatial and temporal locality**.

### Spatial Locality:
- Values next to each other are often accessed together
- Due to arrays and functions
  - Functions because local variables and arguments are near each other

### Temporal Locality:
- A value recently accessed is likely to be accessed again
- Due to functions:
  - You keep accessing the local variables and arguments of a function over and over again inside a function

**Note:** If memory accesses were random, caching would have no effect.

---

## Some Terminology

Given that a cache is smaller than the whole it stores, the cache will not always contain the value we are looking for.

**Hit:** happens when we look inside the cache and find the thing we are looking for

**Miss:** when we look inside the cache and do not find the thing we are looking for

---

## Cache Performance

**Hit Rate = number of hits / number of cache accesses**

**Miss Rate = number of misses / number of cache accesses**

**Hit Rate + Miss Rate = 1**

**Cache Access Time:** time it takes to find something in the cache or find it isn't there

**Memory Access Time:** the amount of time it takes to retrieve a value from memory

**Average Memory Access Time = Cache Access Time + (Memory Access Time × Miss Rate)**

We always have to look in the cache, which is why we have to pay the Cache Access Time, but only have to access memory when we miss.

---

### Memory Hierarchy Visualization:

The memory hierarchy creates a pyramid:
- **Top (fastest, smallest, most expensive):** Registers
- **Bottom (slowest, largest, cheapest):** Hard Disk Drives

---

## Multilevel Caching

We can have caches for our caches to help improve our performance.

**Variables:**
- CA1 = time to access cache 1
- MR1 = miss rate for cache 1
- CA2 = time to access cache 2
- MR2 = miss rate for cache 2
- MA = access time for memory

**Average Memory Access Time = CA1 + MR1 × (CA2 + MR2 × MA)**

---

## Mapping Strategy 1: Direct-Mapped Cache

Imagine that we have a cache that can fit 4 data elements but memory is 16 bytes big. Where would we look to find each element in the cache?

We could map those elements as: **cache entry = address % Cache Size**

<img width="458" height="119" alt="Screenshot 2026-05-12 at 4 53 10 PM" src="https://github.com/user-attachments/assets/a3835ab2-0220-42be-b248-dc48ec7860c4" />

**Tag bits** tell us "where did this thing come from"

If the address of the data we are trying to read does not match the tag of the value in that entry/set, then we know that's not the value we are looking for.

---

**Example #1:** See 53 min of 5/06 Lecture for detailed walkthrough

paused 1hr
