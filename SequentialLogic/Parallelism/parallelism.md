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


This next circuit is the same as above but it is now partioned into a two-stage pipeline by adding a register between blocks 3 and 4. The first stage has a minimum clock period of 0.3 + 3 + 2 + 0.2 = 5.5ns. And the second stage has a minimum clock period of .3 + 4 + .2 = 4.5ns. The clock must be slow enough for all stages to work. Hence Tc = 5.5ns. The latency is two clock cycles, or 11ns. The throughput is 1/5.5ns = 182 Mhs. This example shows that, in a real circuit, pipelining with two stages almost doubles the throughput and slightly increases the latency. In comparison, ideal pipelining would exactly double the throughput at no penalty in latency. The disrepancy comes about because the circuit cannot be divided into two exactly equal halves and because the registers inroduce more sequencing overhead.

<img width="338" height="213" alt="Screenshot 2026-03-31 at 3 24 11 PM" src="https://github.com/user-attachments/assets/eecf4f5c-b827-4afe-a2c0-15ee45567314" />


This final example shows the same circuit paritioned into a three-stage pipline. Not that two more registers are needed to store the results of blocks 1 and 2 at the end of the first pipeline stage. The cycle time is now limited by the third stage to 4.5 ns. The latency is three cycles, or 4.5 x 3 = 13.5 ns. The throughput is 1/4.5 ns = 222 Mhz. Again, adding a pipeline stage imporves throughput at the expense of some latency.

<img width="342" height="200" alt="Screenshot 2026-03-31 at 3 26 08 PM" src="https://github.com/user-attachments/assets/ed76ef85-e766-4fc3-97bb-06dd5d7c2e5c" />

Although these techniques are powerful, they do not apply to all situations. The bane of parallelism is dependencies. If a current task is dependent on the result of a prior task, rather than just prior steps in the current task, the task cannot start until the prior task has completed. Parallelism is one of the most important techniques for designing high-performance digital systems.



