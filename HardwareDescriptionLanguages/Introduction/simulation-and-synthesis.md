# Simulation and Synthesis

The two primary purposes of Hardware Description Languages (HDLs) are:
- **Simulation**
- **Synthesis**

---

## Simulation

**Logic simulation** is used to test a system before it is physically built.

- Inputs are applied to a module  
- Outputs are observed and verified  
- Ensures correct functionality before hardware implementation  

### Example

Waveforms from a simulation of a Verilog module:

- Output `y` is TRUE when inputs `(a, b, c)` are:
  - `000`
  - `100`
  - `101`

![Simulation Waveform](https://github.com/user-attachments/assets/42e91726-38ee-4ec9-8d4b-83e309887da2)

---

## Synthesis

**Logic synthesis** transforms HDL code into actual hardware representations.

- Converts code into a **netlist**
- Netlist describes:
  - Logic gates  
  - Connections (wires)  

### Key Points
- Synthesis tools may **optimize** the design to reduce hardware usage  
- Output may be:
  - A text-based netlist  
  - A schematic diagram  

### Example: Synthesized Circuit

![Synthesized Circuit](https://github.com/user-attachments/assets/0316d3d7-bc03-4b3c-a5c9-b9b482db5f0a)

---

## Important Notes

- HDL code resembles programming code, but it represents **hardware**, not software  
- **Not all HDL constructs are synthesizable**  

---

## Design Structure

HDL designs are typically divided into:

### 1. Synthesizable Modules
- Describe actual hardware  
- Used for synthesis  

### 2. Testbench
- Applies inputs to the design  
- Verifies outputs  
- Reports mismatches between expected and actual results  
- **Used only for simulation (not synthesizable)**  

---

## Design Approach

Before writing HDL code:
- Think in terms of:
  - Combinational logic  
  - Registers  
  - Finite State Machines (FSMs)  
- Sketch the system as interconnected blocks  

---

## Idioms

HDLs use standard patterns for describing logic called **idioms**.

- Idioms represent common ways to model hardware structures  
- Using proper idioms helps ensure code is **synthesizable and efficient**
