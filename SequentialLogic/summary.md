## Summary

This section described the analysis and design of sequential logic. In contrast to combinational logic, whose outputs depend only on the current inputs, sequential logic outputs depend on both current and prior inputs.

Sequential circuits can be difficult to analyze and are easy to design incorrectly, so we limit ourselves to a small set of carefully designed building blocks. The most important element for our purposes is the flip-flop, which receives a clock and an input D and produces an output Q. The flip-flop copies D to Q on the rising edge of the clock and otherwise remembers the old state of Q. A group of flip-flops sharing a common clock is called a register. Flip-flops may also receive reset or enable control signals.

Synchronous sequential circuits consist of blocks of combinational logic separated by clocked registers. The state of the circuit is stored in the registers and updated only on clock edges.

Finite state machines are a powerful technique for designing sequential circuits.

**Steps:**
1. Identify the inputs and outputs of the machine and sketch a state transition diagram, indicating the states and transitions between them
2. Select an encoding for the states and rewrite the diagram as a state transition table and output table, including the next state and output given the current state and input
3. From these tables, design the combinational logic to compute the next state and output, and sketch the circuit

Synchronous sequential circuits have a timing specification including the clock-to-Q propagation and contamination delays, t<sub>pcq</sub> and t<sub>ccq</sub>, and the setup and hold times t<sub>setup</sub> and t<sub>hold</sub>. For correct operation, their inputs must be stable during an aperture time that starts a setup time before the rising clock edge and ends a hold time after the rising edge of the clock.

The minimum cycle time T<sub>c</sub> of the system is equal to the propagation delay t<sub>pd</sub> through the combinational logic plus t<sub>pcq</sub> + t<sub>setup</sub> of the register. For correct operation, the contamination delay through the register and combinational logic must be greater than t<sub>hold</sub>. Despite the common misconception to the contrary, hold time does not affect the cycle time.

Overall system performance is measured in latency and throughput. The latency is the time required for a token to pass from start to end. The throughput is the number of tokens that the system can process per unit time. Parallelism improves system throughput.
