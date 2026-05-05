## Internal Variables

Often it is convenient to break a complex function into intermediate steps. For example, a full adder is a circuit with three inputs and two outputs defined by the following equations:

**S = A ⊕ B ⊕ C<sub>in</sub>**

**C<sub>out</sub> = AB + AC<sub>in</sub> + BC<sub>in</sub>**

If we define intermediate signals, P and G:

**P = A ⊕ B**

**G = AB**

We can rewrite the full adder as follows:

**S = P ⊕ C<sub>in</sub>**

**C<sub>out</sub> = G + PC<sub>in</sub>**

P and G are called **internal variables**, because they are neither inputs nor outputs but are used only internal to the module. They are similar to local variables in programming languages.

---

### HDL Example: Full Adder

In SystemVerilog, internal signals are usually declared as `logic`.

    module fulladder(input logic a, b, cin,
                     output logic s, cout);
        logic p, g;
        
        assign p = a ^ b;
        assign g = a & b;
        
        assign s = p ^ cin;
        assign cout = g | (p & cin);
    endmodule

### Synthesized Circuit:

<img width="355" height="175" alt="Screenshot 2026-05-04 at 5 10 32 PM" src="https://github.com/user-attachments/assets/2f0c9fd9-dd84-4f24-9188-0980a5bfe9b0" />
