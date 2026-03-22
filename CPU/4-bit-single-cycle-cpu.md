## This is a 4-bit Single Cycle CPU

### Instruction Format:
Our CPU will be using fixed length instructions. Our CPU will also have two types of instruction formats: R-type and I-type. In R-type instructions both operands come from registers. In I-type instructions, the first operand comes from a register and the second will be contained within the instruction.

### Register File:
<img width="1061" height="516" alt="Screenshot 2026-03-22 at 12 33 40 PM" src="https://github.com/user-attachments/assets/9e5ec5c6-489f-4d59-a87b-72a8be000254" />

**Reg file inputs:**
* **A_Sel_In:** tells us the value of which register we want to read. If A_Sel_In is 3, then A_Out will be the value in register 3. Same thing for B.
* **Data_In:** is the value we want to store in register C. If Data_In is 20 and C is 2, we store value 20 in register 2.
* **Reg_Write_In:** do we actually want to save that value or not. If this is zero then don't save, and 1 then save.
* **Clk:** the clock

**Reg File Components:**

There are a bunch of values we need to save/store, so there are many flip flops/registers in the regfile.

All of the registers have an output, and we need to select one of them based on the input, so we need a multiplexer to pick one of these register values and get the one we want.

We have a bunch of registers in the regfile, and a giant mux on the right that all the registers feed into. Based on the A select bit (which is the register we want to read the value from) we send that register through the mux into A. The same logic is done for B.

All the registers receive the exact same data as shown in their data port (D).

We have a giant demux where we have our C_sel bits demuxing the register write control signal. Only one of the registers is going to have its WE port be set to 1 (assuming register write is 1 already; if register write is 0 then none of them are set because we are not writing). Only the register that has WE = 1 will have the value saved. The other ones will be disabled and the data is not saved.

Once the rising clock edge comes in, that register that is write enabled will save the value Data_In. And the value of C_sel is the register that is going to have the value saved to it.

### Implementation:
<img width="1067" height="463" alt="Screenshot 2026-03-22 at 12 35 27 PM" src="https://github.com/user-attachments/assets/f33c8dae-2095-4a60-874c-cc438aa04a7f" />

Our inputs are the instruction that is read in from memory and the clock. We divide our instruction into the opcode, C reg, A reg, and B reg and immediate. Depending on whether we have an R or I type instruction, bits 3-0 of the instruction can be a B register or immediate. We then send A and B through our register file and get the value in that register.

We then send A and either B or immediate through to the ALU and do the respective ALU computation based on the OpCode. The output of the ALU is the ALUResult. Depending on our OpCode, we may be instructed to do nothing on this clock cycle or cease the CPU. So we have outputs for those cases also.

We then feed the ALUResult back into the register file through Data_In. And this value is stored in the C register.

We also have a program counter on the bottom that tracks which instruction we are on. On each clock cycle we move forward one instruction. This CPU is word addressable so each clock cycle we add one to the current program counter to read the next instruction.

### ALU:
<img width="486" height="578" alt="Screenshot 2026-03-22 at 12 40 50 PM" src="https://github.com/user-attachments/assets/529549eb-6b12-476b-8cdc-8dd00e215cb5" />

The ALU accepts the Opcode which is the instruction we are performing and two values A and B. Depending on the instruction we perform an arithmetic operation with A and B (e.g. A and B, A or B, A + B, A - B ...). Because of this we use a giant mux. And the result is fed through to the result output pin. Note that we have two cases for the instruction: instruction = 0 and instruction = 1 where we cease CPU execution and do nothing, respectively.




