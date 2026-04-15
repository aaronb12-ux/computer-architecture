## Timing

As we saw before, the output of a gate doesn't change instantly when we change an input, so how long must we wait before we know our output is good?

### Propagation Delay:

The maximum amount of time it takes after an input changes before the output becomes stable.

**AKA:** worst case, longest, critical path through a circuit

### Contamination Delay:

Minimum amount of time after an input changes before any output changes.

**AKA:** shortest path through a circuit

### To find the propagation delay through a circuit:

1. Write the propagation delay of each gate above it
2. Take the maximum delay coming into a gate and add the gate's propagation delay to get the output delay
3. Inputs to the circuit have 0 delay

### To find contamination delay:

1. Write the contamination delay of each gate above it
2. Take the minimum delay coming into the gate and add the contamination delay to get the output delay
3. Inputs to circuit have 0 delay

---

### Example:

**For propagation delay:** take the maximum of the delays at each gate and continuously add it.

<img width="636" height="268" alt="Screenshot 2026-04-11 at 5 06 05 PM" src="https://github.com/user-attachments/assets/0e6df06f-0c35-4ccc-85d6-0ae00ad3ccbe" />

This propagation delay of 27 ns means that once you change the inputs, as long as you wait at least 27 ns, the output will be good.

**For contamination delay:** take the minimum of the delays at each gate and continuously add it.

We care about contamination delay more when we are working with sequential circuits. This is because our flip-flops tend to have a property called 'hold time'. After the rising clock edge changes, there is a certain time the input must remain stable. If the input changes too quickly, the flip-flop will capture the wrong value.

<img width="658" height="278" alt="Screenshot 2026-04-11 at 5 11 39 PM" src="https://github.com/user-attachments/assets/ce26d50c-0b0d-41f9-82a4-802f200be4c9" />

After we change the inputs, once we wait 10 ns we might observe the output to start to change.

---

### Key Points:

**Propagation Delay (t<sub>pd</sub>):**
- Maximum time for output to become stable after input change
- Determines maximum clock frequency in sequential circuits
- Found by summing delays along the longest (critical) path

**Contamination Delay (t<sub>cd</sub>):**
- Minimum time before any output change after input change
- Important for meeting hold time requirements in sequential circuits
- Found by summing delays along the shortest path

---

### Timing Diagrams:

A timing diagram shows the **output of a circuit over time**.

- It shows how signals change over time, including real physical delays.
- Unlike a truth table, it captures both the **value** and the **timing** of signals.

Examples of XOR B both **with and without delay** are below:

- **Without delay:** the output changes immediately when the inputs change.
- **With delay:** the output changes after a delay (e.g., 1 ns), so it is shifted to the right.

This delay corresponds to:
- The **contamination delay** → earliest time the output can start changing
- The **propagation delay** → latest time the output is guaranteed to be stable

<img width="549" height="170" alt="Screenshot 2026-04-14 at 5 43 33 PM" src="https://github.com/user-attachments/assets/36655bc5-8757-4156-a0af-9509c5cacddb" />





