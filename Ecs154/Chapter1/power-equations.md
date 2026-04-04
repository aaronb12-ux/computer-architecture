## Power Consumption

Circuits consume dynamic and static power. Dynamic power is the power that is used when doing the computation. It is the energy used to charge a transistor to change it from 0 to 1.

Static power is the energy used just from having the system on:
- Power is used because the transistors aren't perfect switches and so leak a small amount of current

### Dynamic Power

If a transistor has C capacitance and switches between 0 and 1 at frequency f, then the dynamic power usage is:

**P<sub>dynamic</sub> = 0.5 × f × C × V<sub>dd</sub>²**

The 0.5 is here because it only costs energy to charge the transistor (charge from 0 to 1). Discharging the transistor (1 to 0) is free.

### Static Power

If I<sub>dd</sub> is the leakage current, then:

**P<sub>static</sub> = I<sub>dd</sub> × V<sub>dd</sub>**

### Total Power Consumed

**P<sub>total</sub> = P<sub>dynamic</sub> + P<sub>static</sub>**

### Reducing Power Consumption

To reduce the amount of energy the device is utilizing, you should reduce V<sub>dd</sub>.

**Note:** Reducing V<sub>dd</sub> has a quadratic effect on dynamic power (since it's squared in the equation) but only a linear effect on static power.

