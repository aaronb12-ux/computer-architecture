## Cookie Parallelism

Ben Bitdiddle has hundreds of friends coming to his party and needs to bake cookies faster. He is considering using spatial and/or temporal parallelism.

**Spatial Parallelism:** Ben asks Alyssa P. Hacker to help out. She has her own cookie tray and oven.

**Temporal Parallelism:** Ben gets a second cookie tray. Once he puts one cookie tray in the oven, he starts rolling cookies on the other tray rather than waiting for the first tray to bake.

What is the throughput and latency using spatial parallelism? Using temporal parallelism? Using both?

### Solution:

**Latency:**
For both spatial and temporal parallelism, the latency is 1/3 hour (or 20 minutes) because latency is the time to complete one task from start to finish.

**Throughput:**

**Spatial Parallelism:** Both Ben and Alyssa produce 1 tray in 1/3 hour, resulting in a throughput of **6 trays per hour** (3 trays/hour × 2 people).

**Temporal Parallelism:** The throughput is **4 trays per hour** because Ben puts in a new tray every 15 minutes (60 minutes ÷ 15 minutes = 4 trays/hour).

**Both Spatial and Temporal:** With both Ben and Alyssa using temporal parallelism, the throughput is **8 trays per hour** (4 trays/hour × 2 people).

<img width="334" height="300" alt="Screenshot 2026-03-30 at 4 35 30 PM" src="https://github.com/user-attachments/assets/7dae6a0f-5309-4754-b443-12a01f2bd4c4" />

![CamScanner 3-30-26 16 36n](https://github.com/user-attachments/assets/43c84910-998e-415a-9ce8-d76244551436)
