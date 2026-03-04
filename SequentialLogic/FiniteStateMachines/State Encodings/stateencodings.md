# State Encoding in FSMs

A natural question is how to determine the encoding that produces the circuit with the **fewest logic gates** or the **shortest propagation delay**.

---

## Binary Encoding

In **binary encoding**, each state is represented as a binary number. Because $k$ binary digits can represent $2^k$ values, a system with $K$ states only needs $\lceil \log_2 K \rceil$ bits of state.

| States (K) | Bits Required |
|:----------:|:-------------:|
| 2 | 1 |
| 4 | 2 |
| 8 | 3 |

This minimizes the number of flip-flops needed to store state.

---

## One-Hot Encoding

In **one-hot encoding**, a separate bit of state is used for each state. It is called *one-hot* because only **one bit is "hot" (TRUE) at any time**.

For example, a one-hot encoded FSM with 3 states would have the following encodings:

| State | Encoding |
|-------|:--------:|
| S0 | `001` |
| S1 | `010` |
| S2 | `100` |

Because each bit of state is stored in its own flip-flop, one-hot encoding **requires more flip-flops** than binary encoding. However, the simpler state decoding can result in fewer logic gates and shorter propagation delay in the combinational logic.

---

## Comparison

| | Binary Encoding | One-Hot Encoding |
|---|:---:|:---:|
| Flip-flops required | $\lceil \log_2 K \rceil$ | $K$ |
| Combinational logic complexity | Higher | Lower |
| Best for | Many states | Fast/simple transitions |
