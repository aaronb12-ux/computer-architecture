## Average Memory Access Time (2-Level Cache)

The formula for a 2-level cache is:

```text
AMAT = CAT1 + MR1 × (CAT2 + MR2 × MAT)
```

### Final Expression (expanded form):

```text
AMAT = CAT1 + (MR1 × CAT2) + (MR1 × MR2 × MAT)
```

### Where:
- **CAT1** = Cache access time of L1 cache  
- **MR1** = Miss rate of L1 cache  
- **CAT2** = Cache access time of L2 cache  
- **MR2** = Miss rate of L2 cache  
- **MAT** = Main memory access time  

### Key idea:
- You always pay **L1 access time first**
- If L1 misses → you pay L2 cost
- If L2 also misses → you pay main memory cost
