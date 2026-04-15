## Glitches

A glitch (or hazard) is when a change in a single input causes the output to change multiple times before settling.

A glitch is usually not a problem in combinational circuits, as long as we wait for the propagation delay for the output to stabilize.

A glitch occurs when transitioning between two adjacent groups (circles) on a K-Map that are not covered by a common implicant.

The glitch can be fixed by including a redundant term that overlaps the two groups.

Glitches can also occur if multiple inputs change simultaneously, but these cannot be removed by simply adding redundant hardware.

<img width="631" height="270" alt="Screenshot 2026-04-14 at 5 56 18 PM" src="https://github.com/user-attachments/assets/f93d008d-de8c-46a9-a3a8-111cd7422836" />

### How to Fix a Glitch:

- Add the redundant overlapping term between the adjacent groups.
- This ensures there is always at least one path producing a stable output during the transition.

Typically, we avoid doing this because:
- It increases hardware cost
- It breaks the minimal form (not the least number of gates)

Now, when we change the B input, the output does not glitch because the bottom AND gate continuously produces a 1.

<img width="586" height="173" alt="Screenshot 2026-04-14 at 5 58 31 PM" src="https://github.com/user-attachments/assets/1c417a88-962a-44ec-8434-e026efff9858" />

This hardware fix works when exactly one input changes.

If two or more inputs change simultaneously, glitches cannot be eliminated using this method.
