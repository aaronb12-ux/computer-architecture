## Multiplexer and Demultiplexer

### Multiplexer

A multiplexer selects **one of its data inputs** to forward to the output based on the select signal.

It behaves like an if-statement from programming.

S    Output  
0    D0  
1    D1  

<img width="244" height="159" alt="Screenshot 2026-04-14 at 6 03 40 PM" src="https://github.com/user-attachments/assets/934a69b2-dc02-4638-92e9-60c3249aff89" />

- If the select bit = 0 → output is D0  
- If the select bit = 1 → output is D1  

### Multiplexer Implementation:

### Larger Multiplexers

- In general, a multiplexer has **2ⁿ data inputs** and therefore requires **n select bits**.
- Examples: 2:1, 4:1, 8:1, etc.

<img width="184" height="219" alt="Screenshot 2026-04-14 at 6 08 34 PM" src="https://github.com/user-attachments/assets/dc69030b-13b9-4d88-8283-f9b8f3ea7e90" />

- Larger multiplexers can be constructed using logic gates or by combining smaller multiplexers in a tree structure.
- Sometimes wires represent multi-bit signals (buses), not just single bits.

### Question:

Given as many 2:1 multiplexers, build a 4:1 multiplexer.

<img width="291" height="194" alt="Screenshot 2026-04-14 at 6 14 37 PM" src="https://github.com/user-attachments/assets/b37bcd30-eadf-4a68-a36a-143df4394a6c" />

---

### Multiplexers - Uses

- Select a value  
- Implement a combinational function:
  - With **n select bits**, a mux can implement any function of **n variables** using only constants (power and ground)
  - With additional logic, a smaller mux may be used

---

### Demultiplexer

A demultiplexer functions like a railroad switch:
- It takes **one input** and routes it to **one of 2ⁿ outputs** based on the select bits.

Truth table for a 1:2 demultiplexer:

S   Out1   Out0  
0   0      D  
1   D      0  

- If select = 0 → D goes to Out0  
- If select = 1 → D goes to Out1  

<img width="513" height="343" alt="Screenshot 2026-04-14 at 6 41 41 PM" src="https://github.com/user-attachments/assets/94f1c585-d407-4ca1-ac85-75c15a88588e" />

**Note:**  
We typically do not demultiplex data signals directly; demultiplexers are primarily used for control signals.


  
