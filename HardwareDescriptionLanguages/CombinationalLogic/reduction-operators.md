## Reduction Operators

Reduction operators imply a multiple-input gate acting on a single bus. The example below describes an eight-input AND gate with inputs `a[7]`, `a[6]`, ..., `a[0]`. Analogous reduction operators exist for OR, XOR, NAND, NOR and XNOR gates. Recall that a multiple-input XOR performs parity, returning TRUE if an odd number of inputs are TRUE.

### HDL Example: 8-input AND Gate

```systemverilog
module and8(input logic [7:0] a, 
            output logic y);
    assign y = &a;
    // &a is much easier to write than
    // assign y = a[7] & a[6] & a[5] & a[4] & a[3] & a[2] & a[1] & a[0];
endmodule
```

**Note:** `&a` is much easier to write than explicitly ANDing all 8 bits together.

### Synthesized Circuit:

<img width="497" height="256" alt="Screenshot 2026-05-02 at 4 04 35 PM" src="https://github.com/user-attachments/assets/5ce4804b-3c67-4841-b28d-f0b9b9a4effe" />

---

### Common Reduction Operators:

| Operator | Description | Example |
|----------|-------------|---------|
| `&a` | AND reduction | Returns 1 if all bits are 1 |
| `\|a` | OR reduction | Returns 1 if any bit is 1 |
| `^a` | XOR reduction | Returns 1 if odd number of 1's (parity) |
| `~&a` | NAND reduction | Returns 0 if all bits are 1 |
| `~\|a` | NOR reduction | Returns 0 if any bit is 1 |
| `~^a` or `^~a` | XNOR reduction | Returns 1 if even number of 1's |
