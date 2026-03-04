# 3-Bit Synchronous Up/Down Counter

A **Moore Model** finite state machine implementing a saturating 3-bit synchronous up/down counter.

## Overview

This circuit implements a 3-bit synchronous counter that counts up or down, but **stops (saturates) at the boundary values** rather than wrapping around:

- At `111` (7): counting up has no effect
- At `000` (0): counting down has no effect

> `CountUpIn` and `CountDownIn` will **never** both be `1` simultaneously.

---

## Inputs

| Pin | Size (bits) | Description |
|-----|:-----------:|-------------|
| `EnableIn` | 1 | Connect to the **enable** port of your registers/flip-flops. When `1`, the circuit operates normally. When `0`, the circuit does nothing. |
| `CountUpIn` | 1 | Increments the count by 1, unless the current count is `111`. |
| `CountDownIn` | 1 | Decrements the count by 1, unless the current count is `000`. |
| `clkIn` | 1 | Connect to the **clock** port of your registers/flip-flops. Do nothing else with this signal. |

## Outputs

| Pin | Size (bits) | Description |
|-----|:-----------:|-------------|
| `Count` | 3 | The current value of the counter. |

---

## Behavior

| Condition | Result |
|-----------|--------|
| `EnableIn = 0` | Counter holds current value (no change) |
| `EnableIn = 1`, `CountUpIn = 1`, `Count < 111` | Count increments by 1 |
| `EnableIn = 1`, `CountUpIn = 1`, `Count = 111` | Count stays at `111` |
| `EnableIn = 1`, `CountDownIn = 1`, `Count > 000` | Count decrements by 1 |
| `EnableIn = 1`, `CountDownIn = 1`, `Count = 000` | Count stays at `000` |

---

## Design Notes

- Implemented as a **Moore Model Machine** — outputs depend only on the current state, not on inputs directly.
- The counter is **synchronous** — all state transitions are driven by `clkIn`.
- Saturation logic prevents overflow/underflow, making this a **non-wrapping** counter.

State Transition Diagram and current -> next state table:


[CamScanner 3-3-26 22.44.pdf](https://github.com/user-attachments/files/25734103/CamScanner.3-3-26.22.44.pdf)


