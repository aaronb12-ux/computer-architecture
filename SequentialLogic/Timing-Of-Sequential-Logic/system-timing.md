## System Timing

The **clock period** or **cycle time**, T<sub>c</sub>, is the time between rising edges of a repetitive clock signal. Its reciprocal, f<sub>c</sub> = 1/T<sub>c</sub>, is the clock frequency. All else being the same, increasing the clock frequency increases the work that a digital system can accomplish per unit time. Frequency is measured in units of Hertz (Hz), or cycles per second: 1 megahertz (MHz) = 10<sup>6</sup> Hz and 1 gigahertz (GHz) = 10<sup>9</sup> Hz.

The below image illustrates a generic path in a synchronous sequential circuit whose clock period we wish to calculate.

On the rising edge of the clock, register R1 produces output Q1. These signals enter a block of combinational logic, producing D2 which is the input to register R2.

The timing diagram shows that each output signal may start to change a contamination delay after its input changes and settles to its final value within a propagation delay after its input settles. The gray arrows represent the contamination delay through R1 and the combinational logic, and the blue arrows represent the propagation delay through R1 and the combinational logic.

<img width="373" height="175" alt="Screenshot 2026-03-21 at 1 31 31 AM" src="https://github.com/user-attachments/assets/9605f49e-3fd6-4514-94f8-b799bd33d706" />

After the rising clock edge, there is contamination delay, and the output of R1, Q1, begins to change after this contamination delay. After the propagation delay from the clock edge, Q1 settles. Q1 then enters a block of combinational logic, which has its own contamination delay. After the contamination delay from this logic, the output D2 begins to change. It then settles after the propagation delay from when Q1 settled.

## Setup Time Constraint

The figure below is the timing diagram showing only the maximum delay through the path, indicated by the blue arrows. To satisfy the setup time of R2, D2 must settle no later than the setup time before the next clock edge. Hence we find an equation for the minimum clock period:

<img width="535" height="568" alt="Screenshot 2026-03-21 at 1 46 07 AM" src="https://github.com/user-attachments/assets/3a598e0d-6460-437f-8455-6c7824e45f91" />

**T<sub>c</sub> ≥ t<sub>pcq</sub> + t<sub>pd</sub> + t<sub>setup</sub>**

Where:
- t<sub>pcq</sub> = propagation delay from the rising clock edge to when the output of R1 settles
- t<sub>pd</sub> = propagation delay through the combinational logic
- t<sub>setup</sub> = setup time of the next register (R2)

## Hold Time Constraint

The register R2 in the above figure also has a hold time constraint. Its input, D2, must not change until some time, t<sub>hold</sub>, after the rising edge of the clock. According to the below figure, D2 might change as soon as t<sub>ccq</sub> (contamination delay from rising clock edge) + t<sub>cd</sub> (contamination delay from combinational logic) after the rising edge of the clock. Hence we find:

<img width="551" height="621" alt="Screenshot 2026-03-21 at 1 51 03 AM" src="https://github.com/user-attachments/assets/baa833b8-c5d3-4d57-a968-3e638c3565ff" />

**t<sub>ccq</sub> + t<sub>cd</sub> ≥ t<sub>hold</sub>**

D2 must not change until at least t<sub>hold</sub> after the clock edge. A reliable flip-flop must have a hold time shorter than its contamination delay.

Hold time constraints are critically important. If they are violated, the only solution is to increase the contamination delay through the logic, which requires redesigning the circuit.

## Putting It All Together

Sequential circuits have setup and hold time constraints that dictate the maximum and minimum delays of the combinational logic between flip-flops. The maximum delay constraint limits the number of consecutive gates on the critical path of a high-speed circuit, because a high clock frequency means a short clock period.



