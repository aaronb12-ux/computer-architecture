## Given the following information, how many bits will there be in the Primary Page #, Secondary Page #, and Offset bits when partitioning the virtual address?

![Paging Parameters](https://github.com/user-attachments/assets/8dfe6bf2-8e07-47ca-931c-969871bbe37d)

### Step 1: Calculate the Offset Bits

```text
Offset Bits = log2(Page Size)

Offset Bits = log2(2^10) = 10
```

**Offset = 10 bits**

### Step 2: Calculate the Virtual Page Number (VPN) Bits

```text
VPN Bits = Virtual Address Size - Offset Bits

VPN Bits = 32 - 10 = 22
```

**VPN = 22 bits**

### Step 3: Calculate the Secondary Page Number Bits

A second-level page table must fit within one page.

```text
Entries per Page Table = Page Size / Page Table Entry Size

Entries per Page Table = 2^10 / 4 = 2^8

Secondary Page Bits = log2(2^8) = 8
```

**Secondary Page # = 8 bits**

### Step 4: Calculate the Primary Page Number Bits

```text
Primary Page Bits = VPN Bits - Secondary Page Bits

Primary Page Bits = 22 - 8 = 14
```

**Primary Page # = 14 bits**

### Final Answer

| Field | Number of Bits |
|---------|---------------:|
| Primary Page # | **14** |
| Secondary Page # | **8** |
| Offset | **10** |


