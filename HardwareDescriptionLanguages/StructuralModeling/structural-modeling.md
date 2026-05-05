## Structural Modeling

This section examines structural modeling, describing a module in terms of how it is composed of simpler modules.

### HDL Example: Structural Model of 4:1 Multiplexer

    module mux4(input logic [3:0] d0, d1, d2, d3,
                input logic [1:0] s,
                output logic [3:0] y);
        logic [3:0] low, high;
        
        mux2 lowmux(d0, d1, s[0], low);
        mux2 highmux(d2, d3, s[0], high);
        mux2 finalmux(low, high, s[1], y);
    endmodule

The three `mux2` instances are called `lowmux`, `highmux`, and `finalmux`. Note that the `mux2` module is defined elsewhere in the code.

**Explanation:**

The example shows how to assemble a 4:1 mux from three 2:1 muxes. Each copy of the 2:1 mux is called an **instance**. Multiple instances of the same module are distinguished by distinct names. In this case: `lowmux`, `highmux`, and `finalmux`. This is an example of **regularity**, in which the 2:1 mux is reused many times.

**How it works:**
- `lowmux` selects between `d0` and `d1` based on `s[0]`
- `highmux` selects between `d2` and `d3` based on `s[0]`
- `finalmux` selects between the outputs of `lowmux` and `highmux` based on `s[1]`

### Synthesized Circuit:

<img width="392" height="240" alt="Screenshot 2026-05-04 at 5 26 26 PM" src="https://github.com/user-attachments/assets/eb64f6d6-5a17-43e8-aec1-97ed8cf3ef70" />
