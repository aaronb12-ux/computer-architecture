## Boolean Algebra

### Simplify the Equation

A'B'C' + A'BC' + ABC' + AB'C' + A'B'C + AB'C

#### Step-by-Step Simplification

1. **C'(A'B' + A'B + AB + AB') + B'C(A' + A)**  (Distributive Law)

2. **C'(A'(B' + B) + A(B + B')) + B'C(A' + A)**  (Distributive Law)

3. **C'(A'(1) + A(1)) + B'C(1)**  (Complement Law: B' + B = 1)

4. **C'(A' + A) + B'C**  (Identity Law: A·1 = A)

5. **C'(1) + B'C**  (Complement Law: A' + A = 1)

6. **C' + B'C**  (Identity Law: 1·C' = C')

**Final Simplified Expression: C' + B'C**

---

## Karnaugh Maps (K-Maps)

K-maps provide an easy way to visually simplify Boolean expressions by grouping adjacent terms.

- They help identify common factors between terms
- Adjacent cells (differing by only one variable) can be grouped together
- Larger groups (powers of 2) lead to simpler expressions

K-maps make it easier to spot reductions that may not be obvious algebraically.

### Converting a Boolean Equation into a K-Map:

**Example:** Ā·B·C + C̄·D̄·B + A·B·C

**K-Map:**

|  AB\CD  |  00  |  01  |  11  |  10  |
|---------|------|------|------|------|
|   00    |  0   |  1   |  1   |  0   |
|   01    |  0   |  0   |  0   |  0   |
|   11    |  0   |  1   |  1   |  0   |
|   10    |  0   |  1   |  1   |  0   |

This equation is written as a SOP (Sum of Products).

**Term 1: Ā·B·C**

For this equation to be true for this term: A must be 0, B = 1, and C = 1.
- A = 0 and B = 1 → in the 1st row (AB = 01)
- C = 1 → in the 3rd and 4th columns (CD = 11 or 10 where C = 1)

**Term 2: C̄·D̄·B**

For this equation to be true for this term: C and D must be 0 and B = 1.
- B = 1 → in rows where B = 1 (AB = 01, 11)
- C and D = 0 → in the 1st column (CD = 00)

**Term 3: A·B·C**

For this equation to be true for this term: all must be 1.
- A = 1 and B = 1 → in the 3rd row (AB = 11)
- C = 1 → in the 3rd and 4th columns (CD = 11 or 10 where C = 1)

Everything else is 0's.

**Reading from K-Map:**

Looking at the pattern of 1's, we can group:
- The middle column (CD = 01) has all 1's in rows 00, 10, 11 → this simplifies to B·C̄·D
- Or we can identify other groupings to further simplify

---

### K-Map Grouping Rules:

1. Groups must contain 1, 2, 4, 8, or 16 cells (powers of 2)
2. Groups should be as large as possible
3. Groups can wrap around edges
4. Each group eliminates one or more variables
5. All 1's must be covered, but cells can be in multiple groups





