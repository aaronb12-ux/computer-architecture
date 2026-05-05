## Resettable Registers

When simulation begins or power is first applied to a circuit, the output of a flop or register is unknown. This is indicated with `x` in SystemVerilog. Generally, it is good practice to use resettable registers so that on powerup you can put your system in a known state. The reset may be either asynchronous or synchronous. Recall that asynchronous reset occurs immediately, whereas synchronous reset clears the output only on the next rising edge of the clock. The example below demonstrates the idioms for flip-flops with asynchronous and synchronous resets.

---

### HDL Example: Asynchronous Reset

    module flopr(input logic clk,
                 input logic reset,
                 input logic [3:0] d,
                 output logic [3:0] q);
        // asynchronous reset
        always_ff @(posedge clk, posedge reset)
            if (reset) q <= 4'b0;
            else       q <= d;
    endmodule

---

### HDL Example: Synchronous Reset

    module flopr(input logic clk,
                 input logic reset,
                 input logic [3:0] d,
                 output logic [3:0] q);
        // synchronous reset
        always_ff @(posedge clk)
            if (reset) q <= 4'b0;
            else       q <= d;
    endmodule

---

### Key Differences:

Multiple signals in an `always` statement's sensitivity list are separated with a comma or the word `or`.

Notice that `posedge reset` is in the sensitivity list on the asynchronously resettable flop, but not on the synchronously resettable flop. Thus, the asynchronously resettable flop immediately responds to a rising edge on `reset`, but the synchronously resettable flop responds to reset only on the rising edge of the clock.

### Synthesized Circuits:

**(a) Asynchronous reset**

**(b) Synchronous reset**

<img width="561" height="334" alt="Screenshot 2026-05-05 at 4 53 44 PM" src="https://github.com/user-attachments/assets/b4ccd6bc-8b5f-4d74-9bb2-af9cefd2c54e" />


