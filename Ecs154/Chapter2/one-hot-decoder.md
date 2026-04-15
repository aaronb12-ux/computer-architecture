## One Hot Decoder

A one-hot decoder has **n inputs** and **2ⁿ outputs**.

- Exactly one output will be 1 for each combination of inputs.
- Each output corresponds to a **minterm**.

Here is a 2:4 decoder:

<img width="1205" height="455" alt="Screenshot 2026-04-14 at 6 47 47 PM" src="https://github.com/user-attachments/assets/a81dee8b-2d54-4d8e-a857-459fd11b3f43" />

Only one of the outputs will be 1 at a time; all others will be 0.

Each output represents a minterm, meaning it answers:
> "Did this specific input pattern occur?"

- If input = 00 → output 0 = 1 → pattern 00 occurred  
- If input = 01 → output 1 = 1 → pattern 01 occurred  
- If input = 10 → output 2 = 1 → pattern 10 occurred  
- If input = 11 → output 3 = 1 → pattern 11 occurred  

To determine whether a specific bit pattern occurred, a decoder is useful.
