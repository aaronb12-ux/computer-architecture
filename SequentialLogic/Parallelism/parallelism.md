## Parallelism

The speed of a system is characterized by the latency and throughput of information moving through it.

We define a **token** to be a group of inputs that are processed to produce a group of outputs. The term conjures up the notion of placing subway tokens on a circuit diagram and moving them around to visualize data moving through the circuit. The **latency** of a system is the time required for one token to pass through the system from start to end. The **throughput** is the number of tokens that can be produced per unit time.

Throughput can be improved by processing several tokens at the same time. This is called **parallelism**, and it comes in two forms: spatial and temporal.

### Spatial Parallelism:
Multiple copies of the hardware are provided so that multiple tasks can be done at the same time.

### Temporal Parallelism:
A task is broken into stages, like an assembly line. Multiple tasks can be spread across the stages. Temporal parallelism is commonly called **pipelining**. Spatial parallelism is sometimes just called parallelism.

Consider a task with latency L. In a system with no parallelism, the throughput is 1/L. In a spatially parallel system with N copies of the hardware, the throughput is N/L. In a temporally parallel system, the task is ideally broken into N steps, or stages, of equal length. In such a case, the throughput is also N/L, and only one copy of the hardware is required. Finding N steps of equal length is often impractical. If the longest step has a latency L<sub>1</sub>, the pipelined throughput is 1/L<sub>1</sub>.

Pipelining (temporal parallelism) is particularly attractive because it speeds up a circuit without duplicating the hardware. Instead, registers are placed between blocks of combinational logic to divide the logic into shorter stages that can run with a faster clock. The registers prevent a token in one pipeline stage from catching up with and corrupting the token in the next stage.

### Pipelining Example:

The below circuit is an example of a circuit with no pipelining. It contains 4 blocks of combinational logic between the two registers. The critical path passes through blocks 2, 3, and 4. If the register has a clock-to-Q propagation delay of 0.3 ns and a setup time of 0.2 ns, then the cycle time is T<sub>c</sub> = 0.3 + 3 + 2 + 4 + 0.2 = 9.5 ns. The circuit has a latency of 9.5 ns and a throughput of 1/9.5 ns = 105 MHz.

<img width="344" height="224" alt="Screenshot 2026-03-30 at 4 44 27 PM" src="https://github.com/user-attachments/assets/0fab4529-f1ca-4ae4-b159-0f4d8242a087" />



