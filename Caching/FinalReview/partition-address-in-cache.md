## Cache Address Breakdown Problem

**Given the following cache parameters, how many bits will there be in the Tag, Set, and Offset fields for each cache?**

<img width="588" height="131" alt="Screenshot 2026-05-22 at 8 44 32 PM" src="https://github.com/user-attachments/assets/3de1f9ef-b3d2-4911-9b1a-2ba2e8d95283" />

---

## Formulas:

### Offset:
**Offset = log₂(Block_Size)**

### Tag:
**Tag = Address_Size − Set_Bits − Offset_Bits**

### Set:
- **Direct Mapped:** log₂(Cache_Blocks) where Cache_Blocks = Cache_Size / Block_Size
- **N-Way Associative:** log₂(Cache_Blocks / N)
- **Fully Associative:** 0

---

## Solutions:

### Cache A (16-way set associative):

**Offset = log₂(2³) = 3 bits**

**Set = log₂((2²⁰ / 2³) / 16)**
- Cache_Blocks = 2²⁰ / 2³ = 2¹⁷
- Number of Sets = 2¹⁷ / 16 = 2¹⁷ / 2⁴ = 2¹³
- **Set = 13 bits**

**Tag = 50 − 13 − 3 = 34 bits**

---

### Cache B (Fully associative):

**Offset = log₂(2⁴) = 4 bits**

**Set = 0** (fully associative has no set bits)

**Tag = 60 − 0 − 4 = 56 bits**

---

### Cache C (Direct mapped):

**Offset = log₂(2⁸) = 8 bits**

**Set = log₂(Cache_Blocks)**
- Cache_Blocks = Cache_Size / Block_Size = 2³⁰ / 2⁸ = 2²²
- **Set = log₂(2²²) = 22 bits**

**Tag = 80 − 22 − 8 = 50 bits**

---

## Summary Table:

| Cache | Type | Address Size | Cache Size | Block Size | Offset | Set | Tag |
|-------|------|--------------|------------|------------|--------|-----|-----|
| A | 16-way | 50 bits | 2²⁰ bytes | 2³ = 8 bytes | 3 | 13 | 34 |
| B | Fully Assoc. | 60 bits | 2⁴ bytes | 2⁴ = 16 bytes | 4 | 0 | 56 |
| C | Direct Mapped | 80 bits | 2³⁰ bytes | 2⁸ = 256 bytes | 8 | 22 | 50 |
