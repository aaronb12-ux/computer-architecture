## Analog - The Layer Below Digital

Analog circuits are the technology that digital circuits are built on top of.

Analog circuits produce a continuous (as opposed to discrete) output:
- The values are between 0 (ground) and V<sub>dd</sub> (max value the circuit can produce)
- We pick some threshold between ground and V<sub>dd</sub>, and if the value of the signal is below the threshold we take the value to be 0, and if above the threshold we consider it to be a 1

### Real Life Complications - Noise

<img width="361" height="203" alt="Screenshot 2026-04-01 at 1 57 45 PM" src="https://github.com/user-attachments/assets/c38fa86a-9397-42c3-b710-c0ffcdeca13b" />

Circuits deal with noise, contamination in the signal.

In the above example, the driver produces some value between ground (GND) and V<sub>OL</sub>. Anything in this range is false, logical 0. Anything that is produced between V<sub>OH</sub> and V<sub>DD</sub> is interpreted as true, logical 1.

The receiver interprets any value between V<sub>IH</sub> and V<sub>DD</sub> as being a logic true. It interprets any value between V<sub>0</sub> (ground) and V<sub>IL</sub> as being a logical false.

In order for these circuits to work together, V<sub>IH</sub> of the receiver must always be lower than V<sub>OH</sub> of the driver. Also, the receiver's V<sub>IL</sub> must always be greater than the driver's V<sub>OL</sub>.

The goal is not to minimize the forbidden zone, but to maximize the noise that the circuit can tolerate and still work correctly.

**To summarize the above:**
V<sub>OL</sub> must always be lower than V<sub>IL</sub> and V<sub>OH</sub> must always be higher than V<sub>IH</sub> for the circuit to function correctly.

Let NM<sub>L</sub> be the amount of noise that can be tolerated in a logical 0 and NM<sub>H</sub> be the amount of noise that can be tolerated in a logical 1, then:

**NM<sub>L</sub> = V<sub>IL</sub> - V<sub>OL</sub>**

**NM<sub>H</sub> = V<sub>OH</sub> - V<sub>IH</sub>**

**The max noise tolerated by the circuit is min(NM<sub>L</sub>, NM<sub>H</sub>)**

**Note that we care about the driver's outputs and receiver's inputs**

### Example:

|        | V<sub>OL</sub> | V<sub>IL</sub> | V<sub>OH</sub> | V<sub>IH</sub> |
|--------|------|------|------|------|
| Driver | 3    | 2    | 16   | 12   |
| Receiver | 5  | 4    | 18   | 10   |

**Max Noise:**
- NM<sub>L</sub> = 4 - 3 = 1
- NM<sub>H</sub> = 16 - 10 = 6
- **We can tolerate 1 volt of noise** (the minimum of the two)
