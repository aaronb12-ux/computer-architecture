# Modules

A **module** is a block of hardware with inputs and outputs. Examples include:
- AND gates  
- Multiplexers  
- Priority circuits  

There are two main styles for describing module functionality:

- **Behavioral**: describes *what* the module does  
- **Structural**: describes *how* the module is built from smaller components (hierarchical design)  

---

## Example: Combinational Logic (DL Example 4.1)

### SystemVerilog

```systemverilog
module sillyfunction(input logic a, b, c, output logic y);

  assign y = ~a & ~b & ~c |
             a  & ~b & ~c |
             a  & ~b &  c;

endmodule
```

---

## Explanation

- A SystemVerilog module begins with:
  - The `module` keyword  
  - A name  
  - A list of inputs and outputs  

- The `assign` statement describes **combinational logic**

### Operators
- `~` → NOT  
- `&` → AND  
- `|` → OR  

---

## Signals

- `logic` signals represent **Boolean values**:
  - `0` (false)  
  - `1` (true)  

---

## Modularity

Modules are a key example of **modularity** in hardware design:

- They have a **well-defined interface** (inputs and outputs)  
- They perform a **specific function**  
- Their internal implementation is **hidden**  

As long as a module behaves correctly, other components can use it without needing to know how it is implemented.
