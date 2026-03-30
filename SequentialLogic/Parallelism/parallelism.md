Parallelism

The speed of a system is characterized by the latency and throughput of information moving through it.
We define a token to be a group of inputs that are processed to produce a group of outputs. The term conjured up the notion of placing subway tokens on a circuit diagram and moving them around to visualize data moving through the circuit. The latency of a system is the time required for one token to pass through the system from start to end. The throughput is the number of tokens
that can be produced per unit time.

Throughput can be improved by processing several tokens at the same time. This is called parallelism, and it comes in two forms: spatial and temporal.

Spatial Parallelism:
multiple copies of the hardware are provided so that multiple tasks can be done at the same time

Temporal Parallelism:
a task is broken into stages, like an assembly line. Multiple tasks can be spread across the stages. Temporal parallelism is commonly called pipelining. Spatial parallelism is sometimes just called parallelism.

