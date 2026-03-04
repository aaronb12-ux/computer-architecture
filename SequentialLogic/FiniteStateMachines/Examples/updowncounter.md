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

## How It Works

In a Moore Model machine, the **current state (S)** is what is fed out of the registers as the `Count` output. The **combinational logic** subcircuits then compute the next state values S'0, S'1, and S'2. On each rising clock edge, the registers load S', which becomes the new current state S.

The full cycle:

```
S0 S1 S2 ──→ [Combinational Logic] ──→ S'0 S'1 S'2
    ↑                                        |
    |                                   [Registers]
    |                                        |
    └──────────────── (rising clock edge) ───┘
```

1. The initial S0 S1 S2 are fed into the combinational logic, which calculates S'0, S'1, and S'2.
2. These next-state values are stored in the registers.
3. On each **rising clock edge** (`0 → 1`), the registers load S' — it becomes the new current state S0 S1 S2.
4. These new values are immediately fed back into the combinational logic to compute the next S', and the process repeats.

> The **saturation logic** (stopping at `000` and `111`) is handled entirely within the combinational logic — it's simply a rule about how S' gets calculated based on the current state and inputs.

---

## Design

### State Transition Diagram & Current → Next State Table

![State Transition Diagram](https://github.com/user-attachments/assets/b1e95eeb-043a-4936-a765-96153436530a)

### K-Map Next State Equations

![K-Map](https://github.com/user-attachments/assets/f35a2c9a-cf0f-4678-b1bd-beb31100639d)

### Circuit Implementation

![Circuit](https://github.com/user-attachments/assets/4d868b4e-7c07-4f7d-b5e5-23456ad2f1b8)

---

## Design Notes

- Implemented as a **Moore Model Machine** — outputs depend only on the current state, not on inputs directly.
- The counter is **synchronous** — all state transitions are driven by `clkIn`.
- Saturation logic prevents overflow/underflow, making this a **non-wrapping** counter.

