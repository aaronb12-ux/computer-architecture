## Conditional Assignment

Conditional assignment selects the output from among alternatives based on an input called the condition. The below example illustrates a 2:1 multiplexer using conditional assignment.

### HDL Example: 2:1 Multiplexer

The conditional operator `?:` chooses, based on a first expression, between a second and third expression. The first expression is called the **condition**. If the condition is 1, the operator chooses the second expression. If the condition is 0, the operator chooses the third expression.

`?:` is especially useful for describing a multiplexer because, based on the first input, it selects between two others. The following code demonstrates the idiom for a 2:1 multiplexer with 4-bit inputs and outputs using a conditional operator:

```systemverilog
    module mux2(input logic [3:0] d0, d1,
                input logic s,
                output logic [3:0] y);
        assign y = s ? d1 : d0;
    endmodule
```

**Explanation:** If `s` is 1, then `y = d1`. If `s` is 0, then `y = d0`.

`?:` is also a **ternary operator** because it takes 3 inputs.

**General syntax:** `condition ? true_value : false_value`

### Synthesized Circuit:

<img width="477" height="157" alt="Screenshot 2026-05-02 at 4 10 38 PM" src="https://github.com/user-attachments/assets/17f79f60-89db-4736-896a-a58afa9e3d3f" />
