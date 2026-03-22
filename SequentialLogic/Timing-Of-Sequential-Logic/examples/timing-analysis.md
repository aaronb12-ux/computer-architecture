## Timing Analysis:

### Question:
Ben Bitdiddle designed the circuit below. According to the data sheets for the components he is using, flip-flops have a clock-to-Q contamination delay of 30 ps and a propagation delay of 80 ps. They have a setup time of 50 ps and a hold time of 60 ps. Each logic gate has a propagation delay of 40 ps and a contamination delay of 25 ps. Help Ben determine the maximum clock frequency and whether any hold time violations could occur. This process is called timing analysis.

<img width="500" height="332" alt="Screenshot 2026-03-22 at 1 11 06 PM" src="https://github.com/user-attachments/assets/37a19429-e2ec-4323-9682-75a5be4e55b0" />

### Solution:

**Max Clock Frequency:**

We understand that the maximum clock frequency is found by: T<sub>c</sub> ≥ t<sub>pcq</sub> + t<sub>pd</sub> + t<sub>setup</sub> where t<sub>pcq</sub> is the clock-to-Q propagation delay, t<sub>pd</sub> is the propagation delay of any logic, and t<sub>setup</sub> is the setup time.

The critical path (max clock frequency) occurs when B = 1, C = 0, D = 0, and when A rises from 0 to 1. We claim that A rises from 0 to 1 because when A rises from 0 to 1, it instantiates the propagation delay. If A is already 1 then there would be no propagation delay because it has already occurred since the signal is continuously flowing through.

So the clock-to-Q propagation delay (t<sub>pcq</sub>) of the A flip flop is 80 ps, and this causes A to rise after this propagation delay. Now we travel through the first AND gate with the A and B inputs which has a propagation delay of 40 ps, after this delay n1 rises at 120 ps (80 ps + 40 ps). We then traverse through one more logic gate accounting for 40 ps. This causes X' to rise at 160 ps. Then there is a final logic gate of 40 ps that causes Y' to fall at 200 ps. Y' falls because before it is a NOR gate with 2 inputs. The inputs are 1 and 0 which causes the output to be 0, which then is the input to Y'.

**Illustration of the Critical Path:**

<img width="498" height="770" alt="Screenshot 2026-03-22 at 1 39 05 PM" src="https://github.com/user-attachments/assets/3a19e4a1-982f-4ee2-9375-0e590f3d7f99" />

We see our total is 250 ps → T<sub>c</sub> ≥ t<sub>pcq</sub> + t<sub>pd</sub> + t<sub>setup</sub> = 80 + (3 × 40) + 50 = 250 ps. Now clock frequency is equal to 1/T<sub>c</sub> so we have Clock Frequency = 1/250 ps. Now to convert this to GHz we do 1000/250 = 4 GHz. **4 GHz is the maximum clock frequency.**

**Hold Time Violation:**

t<sub>ccq</sub> (contamination delay from rising clock edge) + t<sub>cd</sub> (contamination delay from combinational logic) ≥ t<sub>hold</sub>

*Note that a reliable flip-flop must have a hold time shorter than its contamination delay*

A short path occurs when A = 0 and C rises, causing X' to rise. The short path only contains one logic gate. So we have t<sub>ccq</sub> + t<sub>cd</sub> = 30 ps + 25 ps = 55 ps. And our hold time for the flip flop is 60 ps. We have 55 ps ≥ 60 ps. This is not true. **There is a hold time violation.** X' did not hold stable long enough to capture the value into X.

**Why the hold time for the flip flop must be shorter than its contamination delay:**

The hold time is a requirement, it's like saying:
* **Hold time** = the flip-flop saying "I need my input to stay stable for this long after the clock edge"

and the contamination delay acts as a buffer saying:
* **Contamination delay** = the circuit's natural protection that says "don't worry, the output won't even start changing until after this time"

**Timeline:**
1. Clock edge arrives → flip-flop captures input
2. Hold time window opens → input must stay stable
3. Contamination delay fires → output starts to change

As long as step 3 happens after step 2's window closes → no violation

