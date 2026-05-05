## Conditional Assignment

Conditional assignment selects the output from among alternatives based on an input called the condition. The below example illustrates a 2:1 multiplexer using conditional assignment.

### HDL Example: 2:1 Multiplexer

The conditional operator `?:` chooses, based on a first expression, between a second and third expression. The first expression is called the **condition**. If the condition is 1, the operator chooses the second expression. If the condition is 0, the operator chooses the third expression.

`?:` is especially useful for describing a multiplexer because, based on the first input, it selects between two others. The following code demonstrates the idiom for a 2:1 multiplexer with 4-bit inputs and outputs using a conditional operator:

    module mux2(input logic [3:0] d0, d1,
                input logic s,
                output logic [3:0] y);
        assign y = s ? d1 : d0;
    endmodule

**Explanation:** If `s` is 1, then `y = d1`. If `s` is 0, then `y = d0`.

`?:` is also a **ternary operator** because it takes 3 inputs.

**General syntax:** `condition ? true_value : false_value`

### Synthesized Circuit:

<img width="477" height="157" alt="Screenshot 2026-05-02 at 4 10 38 PM" src="https://github.com/user-attachments/assets/17f79f60-89db-4736-896a-a58afa9e3d3f" />

---

### HDL Example: 4:1 Multiplexer

A 4:1 multiplexer can select one of four inputs using nested conditional operators:

    module mux4(input logic [3:0] d0, d1, d2, d3, 
                input logic [1:0] s,
                output logic [3:0] y);
        assign y = s[1] ? (s[0] ? d3 : d2)
                        : (s[0] ? d1 : d0);
    endmodule

**Explanation:** If `s[1]` is 1, then the multiplexer chooses the first expression, `(s[0] ? d3 : d2)`. This expression in turn chooses either `d3` or `d2` based on `s[0]` (y = d3 if s[0] is 1 and d2 if s[0] is 0). If `s[1]` is 0, then the multiplexer similarly chooses the second expression, which gives either `d1` or `d0` based on `s[0]`.

**Truth table:**
- `s = 00`: `y = d0`
- `s = 01`: `y = d1`
- `s = 10`: `y = d2`
- `s = 11`: `y = d3`

### Synthesized Circuit:

<img width="353" height="419" alt="Screenshot 2026-05-04 at 5 04 57 PM" src="https://github.com/user-attachments/assets/22d25127-039b-44d4-a665-abe07c0a3367" />
