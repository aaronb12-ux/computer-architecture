# Finite State Machines

Finite State Machines (FSMs) consist of a **state register** and two blocks of combinational logic:

- One to compute the **next state**
- One to compute the **output** based on the current state and input

HDL descriptions of state machines are correspondingly divided into three parts:
- State register
- Next state logic
- Output logic

---

# HDL Example: Divide-By-3 Finite State Machine

```systemverilog
module divideby3FSM(
    input  logic clk,
    input  logic reset,
    input  logic y
);

  typedef enum logic [1:0] {
    S0, S1, S2
  } statetype;
  // statetype is a 2-bit value with three states: S0, S1, S2

  statetype state, nextstate;

  // -------------------------
  // State register
  // -------------------------
  always_ff @(posedge clk or posedge reset) begin
    if (reset)
      state <= S0;
    else
      state <= nextstate;
  end

  // -------------------------
  // Next state logic
  // -------------------------
  always_comb begin
    case (state)
      S0: nextstate = S1;
      S1: nextstate = S2;
      S2: nextstate = S0;
      default: nextstate = S0;
    endcase
  end

  // -------------------------
  // Output logic
  // -------------------------
  assign y = (state == S0); // y is 1 when state == S0

endmodule
```

# Synthesized Circuit

<img width="419" height="376" alt="Screenshot 2026-05-09 at 4 26 31 PM" src="https://github.com/user-attachments/assets/538e72be-2bd7-4ee1-bfcb-7dbcd98248fd" />



