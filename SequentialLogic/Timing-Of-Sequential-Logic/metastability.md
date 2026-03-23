## Metastability

It is not always possible to guarantee that the input to a sequential circuit is stable during the aperture time, especially when the input arrives from the external world.

Consider a button connected to the input of a flip-flop as shown in the below figure. When the button is not pressed, D = 0. When the button is pressed, D = 1. A monkey presses the button at some random time relative to the rising edge of CLK. We want to know the output Q after the rising edge of CLK.

<img width="301" height="218" alt="Screenshot 2026-03-23 at 1 17 01 PM" src="https://github.com/user-attachments/assets/9b178f21-3ed2-4371-97df-40103805433e" />

**First Case:**
We notice that D rises (button was pressed) much earlier than the rising CLK edge. This causes Q = 1.

**Second Case:**
D rises (button was pressed) much after the rising CLK edge, and Q = 0.

**Third Case:**
D rises sometime between t<sub>setup</sub> before CLK and t<sub>hold</sub> after clock, the input violates the dynamic discipline and the output is undefined. The dynamic discipline limits a signal from changing during aperture time, which is what's happening in Case 3.

<img width="339" height="727" alt="Screenshot 2026-03-23 at 1 23 47 PM" src="https://github.com/user-attachments/assets/46db4510-844c-4964-92e7-79866149aa38" />

### Metastable State:

When a flip-flop samples an input that is changing during its aperture, the output Q may momentarily take on a voltage between 0 and V<sub>dd</sub> that is in the forbidden zone. This is called a **metastable state**. Eventually the flip-flop will resolve the output to a stable state of either 0 or 1. However, the resolution time required to reach the stable state is unbounded.

The metastable state of a flip-flop is analogous to a ball on the summit of a hill between two valleys as shown in the below example. The two valleys are stable states, because a ball in the valley will remain there as long as it is not disturbed. The top of the hill is called metastable because the ball would remain there if it were perfectly balanced. But because nothing is perfect, the ball will eventually roll to one side or the other. The time required for this change to occur depends on how nearly well balanced the ball originally was. Every bistable device has a metastable state between the two stable states.

<img width="359" height="252" alt="Screenshot 2026-03-23 at 1 29 16 PM" src="https://github.com/user-attachments/assets/9fcc5093-7b1e-43fc-8d20-7d351820244b" />

### Resolution Time:

If a flip-flop input changes at a random time during the clock cycle, the resolution time, t<sub>res</sub>, required to resolve to a stable state is also a random variable. If the input changes outside the aperture, then t<sub>res</sub> = t<sub>pcq</sub> (propagation delay). But if the input happens to change within the aperture, t<sub>res</sub> can be substantially longer. Theoretical and experimental analyses have shown that the probability that the resolution time, t<sub>res</sub>, exceeds some arbitrary time, t, decreases exponentially with t:

**P(t<sub>res</sub> > t) = (T<sub>0</sub> / T<sub>c</sub>)e<sup>-t/τ</sup>**

where T<sub>c</sub> is the clock period, and T<sub>0</sub> and τ are characteristics of the flip-flop. The equation is valid only for t substantially longer than t<sub>pcq</sub>.

T<sub>0</sub>/T<sub>c</sub> describes the probability that the input changes at a bad time (during aperture time); this probability decreases with the cycle time, T<sub>c</sub>. τ is a time constant indicating how fast the flip-flop moves away from the metastable state; it is related to the delay through the cross-coupled gates in the flip-flop.

In summary, if the input to a bistable device such as a flip-flop changes during the aperture time, the output may take on a metastable value for some time before resolving to a stable 0 or 1. The amount of time required to resolve is unbounded, because for any finite time, t, the probability that the flip-flop is still metastable is nonzero. However, this probability drops off exponentially as t increases. Therefore, if we wait long enough, much longer than t<sub>pcq</sub>, we can expect with exceedingly high probability that the flip-flop will reach a valid logic level.

