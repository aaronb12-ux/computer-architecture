# Enabled Registers

Enabled registers respond to the clock only when the enable signal is asserted. The example below shows an asynchronously resettable enabled register that retains its previous value if both `reset` and `en` are FALSE.

---

## Verilog Implementation

```verilog
module flopenr (
    input  logic       clk,
    input  logic       reset,
    input  logic       en,
    input  logic [3:0] d,
    output logic [3:0] q
);

    // Asynchronous reset
    always_ff @(posedge clk, posedge reset)
        if (reset)
            q <= 4'b0;
        else if (en)
            q <= d;

endmodule
```

## Synthesized Circuit

  <img width="397" height="138" alt="Screenshot 2026-05-07 at 12 24 23 PM" src="https://github.com/user-attachments/assets/765e3e23-843b-4d18-a63f-8613c2d947f6" />
