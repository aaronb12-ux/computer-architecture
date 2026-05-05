## Sequential Logic

HDL synthesizers recognize certain idioms and turn them into specific sequential circuits. Other coding styles may simulate correctly but synthesize into circuits with blatant or subtle errors.

This section presents the proper idioms to describe registers and latches.

### Registers:

The vast majority of modern commercial systems are built with registers using positive edge-triggered D flip-flops.

In SystemVerilog, `always` statements keep their old value until an event in the sensitivity list takes place that explicitly causes them to change. Hence, such code, with appropriate sensitivity lists, can be used to describe sequential circuits with memory.

The flip-flop includes only `clk` in the sensitivity list. It remembers its old value of `q` until the next rising edge of the `clk`, even if `d` changes in the interim.

In contrast, SystemVerilog continuous assignment statements (`assign`) are reevaluated anytime any of the inputs on the right hand side changes.

---

### HDL Example: Register


    module flop(input logic clk,
                input logic [3:0] d,
                output logic [3:0] q);
        always_ff @(posedge clk)
            q <= d;
    endmodule

In general, a SystemVerilog `always` statement is written in the form:

    always @(sensitivity list)
        statement;

The `statement` is executed only when the event specified in the `sensitivity list` occurs. In this example, the statement is `q <= d` (q gets d).

Hence, the flip-flop copies `d` to `q` on the positive edge of the clock and otherwise remembers the old state of `q`. Sensitivity lists are also referred to as stimulus lists.

`<=` is called a **nonblocking assignment**. It can be thought of as a regular `=` sign for now. Note that `<=` is used instead of `assign` inside an `always` statement.

As will be seen soon, `always` statements can be used to imply flip-flops, latches, or combinational logic, depending on the sensitivity list and statement. Because of this flexibility, it is easy to produce wrong hardware.

SystemVerilog introduces `always_ff`, `always_latch`, and `always_comb` to reduce the risk of common errors. `always_ff` behaves like `always` but is used exclusively to imply flip-flops and allows tools to produce a warning if anything else is implied.

### Synthesized Circuit:

<img width="523" height="108" alt="Screenshot 2026-05-05 at 4 43 30 PM" src="https://github.com/user-attachments/assets/e3d6eec2-be0a-444f-a42e-34fb64b413d7" />


