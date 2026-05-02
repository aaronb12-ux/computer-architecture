## Bitwise Operators

Bitwise operators act on single-bit signals or on multi-bit buses. For example, the `inv` module in the example below describes four inverters connected to 4-bit buses.

### HDL Example: Inverters

```systemverilog
module inv(input logic [3:0] a,
           output logic [3:0] y);
    assign y = ~a;
endmodule
```

`a[3:0]` represents a 4-bit bus. The bits, from most significant to least significant, are `a[3]`, `a[2]`, `a[1]` and `a[0]`. This is called **little-endian order**, because the least significant bit has the smallest bit number. We could have used `a[0:3]` in which case the bits, from most significant to least significant, would be `a[0]`, `a[1]`, `a[2]` and `a[3]`. This is called **big-endian order**.

Endianness matters only for operators, such as addition, where the sum of one column carries over into the next.

### inv Synthesized Circuit

<img width="421" height="99" alt="Screenshot 2026-05-02 at 2 24 46 AM" src="https://github.com/user-attachments/assets/b76be34b-2f6f-494c-a83c-86803bb78738" />

The bank of inverters connects to 4-bit input and output buses.

---

### HDL Example: Logic Gates

```systemverilog
module gates(input logic [3:0] a, b, 
             output logic [3:0] y1, y2, y3, y4, y5);
    /* five different two-input logic gates acting on 4-bit buses */
    assign y1 = a & b;   // AND
    assign y2 = a | b;   // OR
    assign y3 = a ^ b;   // XOR
    assign y4 = ~(a & b); // NAND
    assign y5 = ~(a | b); // NOR
endmodule
```

`~`, `^`, and `|` are examples of SystemVerilog operators, whereas `a`, `b` and `y1` are operands. Combining these results in an **expression**. A complete command such as `y4 = a | b;` is called a **statement**.

`assign out = in1 op in2;` is called a **continuous assignment statement**. Continuous assignment statements end with a semicolon. Anytime the inputs on the right side of the `=` in a continuous assignment statement change, the output on the left side is recomputed.

Thus, continuous assignment statements describe combinational logic.


    
