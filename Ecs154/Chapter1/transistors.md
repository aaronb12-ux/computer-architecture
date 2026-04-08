## Transistors

Transistors are the technology that made modern computers possible.  
They behave like electrical switches, but have **no moving parts**.

They are formed by embedding **positive (p-type)** and **negative (n-type)** regions into a semiconductor material.

### Types of Transistors

- **nMOS**
- **pMOS**

**MOS** stands for **Metal-Oxide-Semiconductor**.

<img width="355" height="216" alt="Screenshot 2026-04-07 at 6 28 35 PM" src="https://github.com/user-attachments/assets/6ba62881-992a-4e72-a005-54bfe5026e7c" />

---

## nMOS Transistor

- The **substrate (body)** is connected to **ground (0)**.
- When the **gate is 0**:
  - There is no electric field between the gate and substrate
  - No channel forms
  - **Source and drain are disconnected**
- When a **positive voltage (1)** is applied to the gate:
  - Electrons are attracted toward the gate
  - The region under the gate becomes effectively **negatively charged**
  - A **conductive channel forms**
  - **Source and drain become connected**, allowing current to flow

> If no voltage is applied to the gate, there is not enough electrical potential to form a channel, so current cannot flow between source and drain.

---

## pMOS Transistor

- The **opposite behavior of nMOS**
- The **substrate (body)** is connected to **Vdd (1)**

<img width="331" height="148" alt="Screenshot 2026-04-07 at 6 32 37 PM" src="https://github.com/user-attachments/assets/918c393f-127f-45cf-b2a2-5ac8244655cc" />

---

## Behavior

### nMOS
- Gate = 0 → **OFF** (no connection, no current flow)
- Gate = 1 → **ON** (connection formed, current flows)

### pMOS
- Gate = 0 → **ON** (connection formed, current flows)
- Gate = 1 → **OFF** (no connection, no current flow)

<img width="319" height="229" alt="Screenshot 2026-04-07 at 6 34 47 PM" src="https://github.com/user-attachments/assets/618c9759-6926-40e4-9acd-eace550997b0" />

---

## Building Gates with Transistors

- **nMOS transistors**
  - Good at passing **0 (logic low)**
  - Poor at passing **1**
  - Act as **pull-down devices** (toward ground)

- **pMOS transistors**
  - Good at passing **1 (logic high)**
  - Poor at passing **0**
  - Act as **pull-up devices** (toward Vdd)

- Because of this, we combine them so each operates in its **strong region**

### CMOS (Complementary MOS)

- Uses both **nMOS and pMOS together**
- “C” stands for **complementary**
- Ensures:
  - Strong 0s and 1s
  - Reliable logic behavior

- **Only one network conducts at a time**:
  - Either the pull-up (pMOS) network is ON  
  - Or the pull-down (nMOS) network is ON  
  - **Never both at the same time** (prevents short circuits)

<img width="258" height="246" alt="Screenshot 2026-04-07 at 6 40 38 PM" src="https://github.com/user-attachments/assets/6458ef4d-f9d9-46cd-a78b-a2d1ff3cfc87" />
  



