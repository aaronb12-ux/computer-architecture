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

**Key Difference:**
- **Minterm:** Uses AND (·), 1 → positive, 0 → negative
- **Maxterm:** Uses OR (+), 0 → positive, 1 → negative
- a minterm is true for one row only, and a maxterm is false for one row, and one row only
- to find a SOP, you sum all the products in the truth table whos output is 1.
- to find a POS, you multiply all the sums in the trutht table whos output is 0.


