# 4-Bit Even Parity Checker (Moore Model FSM)

A **Moore Model** finite state machine that calculates even parity over groups of 4 input bits, received one bit at a time.

## Overview

The circuit receives 1 bit of input at a time and processes bits in **chunks of 4** (not a sliding window). After the 4th bit of each group is received, it outputs `1` if the group contained an **even number of 1s**, and `0` at all other times.

> `0000` is considered to have an even number of 1s.

Because this is a **Moore Model Machine**, the output depends only on state — meaning it cannot change until the next rising clock edge. This causes the output to appear delayed by one clock cycle.

### Example

```
Input:  0111 1000 1010 1100
Output: 0000 0000 0000 1000 1
```

---

## Inputs

| Pin | Size (bits) | Description |
|-----|:-----------:|-------------|
| `EnableIn` | 1 | Connect to the **enable** port of your registers/flip-flops. When `1`, the circuit operates normally. When `0`, the circuit does nothing. |
| `InputBitIn` | 1 | The current bit being input into the circuit. |
| `ClkIn` | 1 | Connect to the **clock** port of your registers/flip-flops. Do nothing else with this signal. |

## Outputs

| Pin | Size (bits) | Description |
|-----|:-----------:|-------------|
| `IsEvenOut` | 1 | `1` if there were an even number of 1s in the last group of 4 bits, `0` otherwise. |

---

## Design

### Step 1 — State Transition Diagram

We begin at starting state **S0**. On each clock cycle, we transition to the next state depending on whether the input bit is `0` or `1`.

![State Transition Diagram](https://github.com/user-attachments/assets/19c569f7-b712-47f2-8cc7-fab5e0daf081)

---

### Step 2 — State Encodings

We have **9 states**, so we need $\lceil \log_2 9 \rceil = 4$ bits of state.

| State | Encoding |
|:-----:|:--------:|
| S0 | `0000` |
| S1 | `0001` |
| S2 | `0010` |
| S3 | `0011` |
| S4 | `0100` |
| S5 | `0101` |
| S6 | `0110` |
| S7 | `0111` |
| S8 | `1000` |

---

### Step 3 — Transition Table

![Transition Table](https://github.com/user-attachments/assets/f448c3a7-4a76-4beb-8bed-c845efb5aea0)

---

### Step 4 — Circuit Implementation

![Circuit Implementation](https://github.com/user-attachments/assets/db8213af-993c-4c94-a091-2ca1c9767aed)

---

## Design Notes

- Implemented as a **Moore Model Machine** — `IsEvenOut` depends only on the current state, not directly on inputs.
- The circuit is **chunk-based**, not a sliding window — it evaluates parity over each successive group of 4 bits independently.
- The output appearing one cycle late is **expected Moore Model behavior**, not a bug.
- With 9 states, 4 flip-flops are required to store state (state encodings `0000` through `1000`).



