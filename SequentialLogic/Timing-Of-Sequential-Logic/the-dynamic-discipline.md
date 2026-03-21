## The Dynamic Discipline

Recall that a synchronous sequential circuit, such as a flip-flop or FSM, also has a timing specification as illustrated in the image.

When the clock rises, the output (or outputs) may start to change after the clock-to-Q contamination delay, t<sub>ccq</sub>, and must definitely settle to the final value within the clock-to-Q propagation delay, t<sub>pcq</sub>. These represent the fastest and slowest delays through the circuit, respectively.

For the circuit to sample its input correctly, the input (or inputs) must have stabilized at least some setup time t<sub>setup</sub> before the rising edge of the clock and must remain stable for at least some hold time t<sub>hold</sub> after the rising edge of the clock.

The sum of the setup and hold time is called the **aperture time** of the circuit, because it is the total time for which the input must remain stable.

<img width="478" height="382" alt="Screenshot 2026-03-21 at 1 13 39 AM" src="https://github.com/user-attachments/assets/716104ee-c826-4f8a-8541-354300db328a" />

The input must stabilize at least some setup time before the rising edge of the clock, t<sub>setup</sub>, for the circuit to sample it correctly. After the clock rises, the input must remain stable for at least some hold time, t<sub>hold</sub>. After the clock rises there is a contamination delay, t<sub>ccq</sub>, after which the outputs may start to change. By the end of the propagation delay, t<sub>pcq</sub>, the outputs have settled. 

The dynamic discipline states that the inputs of a synchronous sequential circuit must be stable during the setup and hold aperture time around the clock edge.

By imposing this requirement, we guarantee that the flip-flops sample signals while they are not changing.
