# Multiple Registers

A single `always`/process statement can be used to describe multiple pieces of hardware. For example, a synchronizer made of two back-to-back flip-flops is shown below. On the rising edge of `clk`, `d` is copied to `n1`, and at the same time `n1` is copied to `q`.

## Synchronizer Circuit

![Synchronizer Circuit](https://github.com/user-attachments/assets/1e7f814a-b7e0-46bf-b740-4f3359b28734)

## HDL Example: Synchronizer

```verilog
module sync (
    input  logic clk,
    input  logic d,
    output logic q
);

    logic n1;

    always_ff @(posedge clk) begin
        n1 <= d;   // nonblocking
        q  <= n1;  // nonblocking
    end

endmodule
```

Notice that the begin/end construct is necessary because multiple statements appear in the always statement.
This is analogous to () in C or Java. The begin/end was not needed in the 
flopr example because if/else counts as a single statement.


## Synthesized Circuit

<img width="500" height="187" alt="Screenshot 2026-05-07 at 12 34 05 PM" src="https://github.com/user-attachments/assets/cd5da489-13c3-462a-bd74-e519782d685d" />
