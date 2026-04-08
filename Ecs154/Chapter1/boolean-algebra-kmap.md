## Boolean Algebra

### Simplify the Equation

\[
\sim A \sim B \sim C + \sim A B \sim C + A B \sim C + A \sim B \sim C + \sim A \sim B C + A \sim B C
\]

#### Step-by-Step Simplification

\[
\sim C(\sim A \sim B + \sim A B + A B + A \sim B) + \sim B C(\sim A + A) \quad \text{(Distributive Law)}
\]

\[
\sim C(\sim A(\sim B + B) + A(B + \sim B)) + \sim B C(\sim A + A) \quad \text{(Distributive Law)}
\]

\[
\sim C(\sim A(1) + A(1)) + \sim B C(1) \quad \text{(Complement Law)}
\]

\[
\sim C(1) + \sim B C \quad \text{(Identity Law)}
\]

\[
\sim C + \sim B C \quad \text{(Final Simplified Expression)}
\]

---

## Karnaugh Maps (K-Maps)

K-maps provide an easy way to visually simplify Boolean expressions by grouping adjacent terms.

- They help identify common factors between terms.
- Adjacent cells (differing by only one variable) can be grouped together.
- Larger groups (powers of 2) lead to simpler expressions.

K-maps make it easier to spot reductions that may not be obvious algebraically.









