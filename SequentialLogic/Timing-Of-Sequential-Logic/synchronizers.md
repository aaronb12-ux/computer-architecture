## Synchronizers

Asynchronous inputs to a digital system from the real world are inevitable. Human input is asynchronous, for example. If handled carelessly, these asynchronous inputs can lead to metastable voltages within the system, causing erratic system failures that are extremely difficult to track down and correct.

The goal of a digital system designer should be to ensure that, given asynchronous inputs, the probability of encountering a metastable voltage is sufficiently small. To guarantee good logic levels, all asynchronous inputs should be passed through synchronizers.

A synchronizer, shown below, is a device that receives an asynchronous input D and a clock CLK. It produces an output Q within a bounded amount of time; the output has a valid logic level with extremely high probability. If D is stable during the aperture, Q should take on the same value as D. If D changes during the aperture, Q may take on either a HIGH or LOW value but must not be metastable.

<img width="360" height="446" alt="Screenshot 2026-03-23 at 1 46 30 PM" src="https://github.com/user-attachments/assets/c78d3fa6-d19c-40e3-a290-38505dce3d14" />

The figure below shows a simple way to build a synchronizer out of two flip-flops. F1 samples D on the rising edge of CLK. If D is changing at that time, the output D2 may be momentarily metastable. If the clock period is long enough, D2 will, with high probability, resolve to a valid logic level before the end of the period. F2 then samples D2, which is now stable, producing a good output Q.

<img width="357" height="362" alt="Screenshot 2026-03-23 at 1 49 13 PM" src="https://github.com/user-attachments/assets/e8da52c3-3a0a-4027-8cc8-9bddb199d0c5" />

**Parameters:**
- T<sub>c</sub> = clock period
- t<sub>res</sub> = resolution time required to resolve to a stable state if the output is metastable
- t<sub>setup</sub> = setup time for next clock cycle
- t<sub>pcq</sub> = propagation delay

The output D2 is momentarily metastable. The input (D) was changing during the aperture time, hence why there is a resolution time. After D2 becomes stable, there is setup time for the next flip flop. D2 passes through this flip flop with no metastability. This causes no additional resolution time. After the second flip flop there is our normal propagation delay and Q produces an output.

We say that a synchronizer fails if Q, the output of the synchronizer, becomes metastable. This may happen if D2 has not resolved to a valid level by the time it must setup at F2 -- that is, if t<sub>res</sub> > T<sub>c</sub> - t<sub>setup</sub>.

According to our previous equation, the probability of failure for a single input change at a random time is:

**P(failure) = (T<sub>0</sub>/T<sub>c</sub>) e<sup>-(T<sub>c</sub> - t<sub>setup</sub>)/τ</sup>**

The probability of failure P(failure) is the probability that the output Q will be metastable upon a single change in D. If D changes once per second, the probability of failure per second is just P(failure). However, if D changes N times per second, the probability of failure per second is N times as great:

**P(failure)/sec = N · (T<sub>0</sub>/T<sub>c</sub>) · e<sup>-(T<sub>c</sub> - t<sub>setup</sub>)/τ</sup>**

System reliability is usually measured in mean time between failures (MTBF). As the name suggests, MTBF is the average amount of time between failures of the system. It is the reciprocal of the probability that the system will fail in any given second:

**MTBF = 1 / (P(failure)/sec) = (T<sub>c</sub>/NT<sub>0</sub>) · e<sup>(T<sub>c</sub> - t<sub>setup</sub>)/τ</sup>**


