## What are Combinational Circuits?
Combinational circuits are circuits where the output depends solely on the input.
All combinational circuits can be described using Boolean equations.

### Terminology
**Product (AND):**
- An ANDing of two or more literals is called a **product**
- A product involving all the literals in a function is called a **minterm**

**Sum (OR):**
- An ORing of two or more literals is called a **sum**
- A sum involving all of the literals in a function is called a **maxterm**

### Minterms
For a minterm, wherever the value is 1, use the positive form; where it's 0, negate.

**Example: Minterm for decimal 11**
| 8 | 4 | 2 | 1 |
|---|---|---|---|
| A | B | C | D |
| 1 | 0 | 1 | 1 |

**Minterm:** A · B̄ · C · D

**Example: Minterm for decimal 14**
| 8 | 4 | 2 | 1 |
|---|---|---|---|
| A | B | C | D |
| 1 | 1 | 1 | 0 |

**Minterm:** A · B · C · D̄

### Maxterms
For a maxterm, anywhere there is a 0, use the positive form of that value; where it's 1, use the negative form.

**Example: Maxterm for decimal 11**
| 8 | 4 | 2 | 1 |
|---|---|---|---|
| A | B | C | D |
| 1 | 0 | 1 | 1 |

**Maxterm:** Ā + B + C̄ + D̄

### Key Differences:
- **Minterm:** Uses AND (·), 1 → positive, 0 → negative
  - A minterm is true for one row only
- **Maxterm:** Uses OR (+), 0 → positive, 1 → negative
  - A maxterm is false for one row only

### Sum of Products (SOP) and Product of Sums (POS)

**To find SOP:** Sum all the products (minterms) in the truth table whose output is 1

**To find POS:** Multiply all the sums (maxterms) in the truth table whose output is 0

### Example:

| A | B | C | Out |
|---|---|---|-----|
| 0 | 0 | 0 |  0  |
| 0 | 0 | 1 |  0  |
| 0 | 1 | 0 |  0  |
| 0 | 1 | 1 |  1  |
| 1 | 0 | 0 |  1  |
| 1 | 0 | 1 |  0  |
| 1 | 1 | 0 |  1  |
| 1 | 1 | 1 |  1  |

**SOP: Σ(m3, m4, m6, m7)**

- m3 = Ā · B · C
- m4 = A · B̄ · C̄
- m6 = A · B · C̄
- m7 = A · B · C

**SOP Expression:** Ā·B·C + A·B̄·C̄ + A·B·C̄ + A·B·C

The above minterms are summed (OR'd) together to get the SOP.

**POS: Π(M0, M1, M2, M5)**

- M0 = A + B + C
- M1 = A + B + C̄
- M2 = A + B̄ + C
- M5 = Ā + B + C̄

**POS Expression:** (A+B+C) · (A+B+C̄) · (A+B̄+C) · (Ā+B+C̄)

The above maxterms are multiplied (AND'd) together to get the POS.


  


