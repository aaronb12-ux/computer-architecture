## Timing Of Sequential Logic

A flip flop copies the input D to the output Q on the rising edge of the clock. This process is called **sampling D on the clock edge**.

If D is stable at either 0 or 1 when the clock rises, this behavior is clearly defined. But what happens if D is changing at the same time the clock rises?

A sequential element has an **aperture time** around the clock edge, during which the input must be stable for the flip-flop to produce a well-defined output.

The aperture of a sequential element is defined by a **setup time** and a **hold time**, before and after the clock edge, respectively.

The **dynamic discipline** limits us to using signals that change outside the aperture time. By taking advantage of the dynamic discipline, we can think of time in discrete units called clock cycles, just as we think of signal levels as discrete 1's and 0's.

A signal may glitch and oscillate wildly for some bounded amount of time. Under dynamic discipline, we are concerned only about its final value at the end of the clock cycle, after it has settled to a stable value. Hence we can simply write A[n], the value of signal A at the end of the nth clock cycle, where n is an integer, rather than A(t), the value of A at some instant t, where t is any real number.

The clock period has to be long enough for all signals to settle. This sets a limit on the speed of the system. In real systems, the clock does not reach all flip-flops at precisely the same time. This variation in time, called **clock skew**, further increases the necessary clock period.

Sometimes it is impossible to satisfy the dynamic discipline, especially when interfacing with the real world. For example, consider a circuit with an input coming from a button. A monkey might press the button just as the clock rises. This can result in a phenomenon called **metastability**, where the flip-flop captures a value part way between 0 and 1 that can take an unlimited amount of time to resolve into a good logic value. The solution to such asynchronous inputs is to use a **synchronizer**, which has a very small (but nonzero) probability of producing an illegal logic value.
