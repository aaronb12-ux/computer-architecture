## Fixing Hold Time Violations:

Alyssa P. Hacker proposes to fix Ben's circuit by adding buffers to slow down the short paths, as shown in the below figure. The buffers have the same delays as other gates. Determine the maximum clock frequency and whether any hold time problems could occur.

### Updated Circuit:
<img width="500" height="379" alt="Screenshot 2026-03-22 at 2 22 11 PM" src="https://github.com/user-attachments/assets/f624eb25-f7bc-468d-9811-165814a1ec84" />

### Maximum Clock Frequency:

The maximum clock frequency does not change. The critical path from A to Y is not affected as it does not pass through any of the new buffers. It is still 4 GHz.

### Hold Time Violations:

With the new buffers, that adds 25 ps to our previous contamination delay. So now we have 55 ps + 25 ps which is equal to 80 ps and 80 ps ≥ 60 ps. This resolves our previous hold time violation.

### Timing Diagram With Buffers:
<img width="499" height="374" alt="Screenshot 2026-03-22 at 2 24 26 PM" src="https://github.com/user-attachments/assets/76807606-40d1-44c5-a889-656fc909cb3a" />

### My Work:
![CamScanner 3-22-26 14 25n](https://github.com/user-attachments/assets/0556f615-c5d2-4632-af95-9334771ef3aa)
