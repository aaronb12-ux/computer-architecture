## Adders:

### Half Adder

<img width="538" height="224" alt="Screenshot 2026-04-20 at 8 25 22 PM" src="https://github.com/user-attachments/assets/c5bb1bd0-9bcc-4589-9f6a-0cbb8546610f" />

A half adder adds two 1-bit numbers and produces a sum and carry output.

---

### Full Adder

<img width="604" height="296" alt="Screenshot 2026-04-20 at 8 28 17 PM" src="https://github.com/user-attachments/assets/429f07a7-5dbd-4d26-9ba0-8bc165af12ac" />

A single full adder can only add 2 one-bit numbers together plus a carry in.

---

### Ripple Carry Adder:

If we want to add N-bit numbers together, we can simply hook up N full adders together, feeding the carry out of the prior stage into the carry in of the current stage.

The downside of this method is that the adder produced will be slow as we have to wait for the carry to propagate all the way through to the last stage.

<img width="308" height="170" alt="Screenshot 2026-04-20 at 8 34 10 PM" src="https://github.com/user-attachments/assets/ffa597c2-d308-4264-aa60-f79919e75b35" />

This is slow as it does all add computations in series → NOT parallel.

**How can we do the computations in parallel?** → prefix adder

---

### Prefix Adder:

To reduce the delay on the carry, we calculate the carries in parallel.

- If we don't distribute the terms, we have ripple carry
- If we do distribute the terms, we have a prefix adder

While this does speed things up, it comes at the cost of a lot more hardware.

**Trade-off:**
- **Ripple Carry Adder:** slower, less hardware
- **Prefix Adder:** faster, more hardware

