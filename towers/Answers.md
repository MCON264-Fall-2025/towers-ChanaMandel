#  MCON 264 — Recursion Assignment: Towers of Hanoi × 3


##  Overview

In this lab, you implemented three recursive versions of the Towers of Hanoi problem and (optionally) one iterative version.  
Each part reinforces a key concept of recursion — base case, recursive case, and growth pattern — and illustrates how recursion can be refactored or replaced by iteration.

---

## Part 1 — Classic Towers of Hanoi (`TowersOfHanoi.java`)

### 1. Base Case
_Describe the base condition that stops recursion (for example, what happens when `n == 0`?)._

> when the base condition is zero, there is nothing on the first tower, the method returns and exits 

### 2. Recursive Case
_Explain the sequence of recursive calls and what each represents._

> 1. move all the disks except the biggestfrom the original tower to the aux tower,
> 2. and then we record the moves in the moves list
> 3. when we do moves.add... we are moving the biggest disk from the original to the to peg
> 4. we move the smaller disks from the aux on to the to peg

### 3. Sample Trace (for n = 3)

| Move # | From | To |
|:--:|:--:|:--:|
| 1 | A | C |
| 2 | A | B |
| 3 | C | B |
| … |  |  |

_Total moves = 2ⁿ − 1 = 7 (for n = 3)_
Move 1 move disk 1 from A to C 
Move 2 move disk 2 from A to B
Move 3 move disk 1 from C to B
Move 4 move disk 3 from A to C
Move 5 move disk 1 from B to A
Move 6 move disk 2 from B to C
Move 7 move disk 1 from A to C

## Part 2 — Counting Moves (`TowersExercise21.java`)

### 1. Approach
_How did you modify the standard recursion to count rather than print moves?_

>  I added a count variable and incremented it

### 2. Verification of Formula
_Complete the table and verify that count = 2ⁿ − 1._

| n | Expected (2ⁿ − 1) | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 1 |       1        |       Y        |
| 2 | 3 |       3        |       Y        |
| 3 | 7 |       7        |       Y        |
| 4 | 15 |       15       |       Y        |
| 5 | 31 |       31       |       Y        |

### 3. Reflection
_What changes when you replace printed moves with a counter? What are the pros and cons?_

> Instead of recording the moves as a string, a counter variable is incremented for each
> move, this is faster and more memory efficient, but you can not see the actual sequence
> of moves, only the number of moves

---

## Part 3 — Hanoi Variation (`TowersVariations.java`)

### 1. New Rule
_Every move must pass through the middle peg. How does this alter the recursion?_

> You need 3 recursive calls instead of 2 to move a big disk from 1 to 3 

### 2. Observed Move Counts

| n | Expected ≈ 3ⁿ − 1 | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 2 |       2        |       Y        |
| 2 | 8 |       8        |       Y        |
| 3 | 26 |       26       |       Y        |
| 4 | 80 |       80       |       Y        |

### 3. Analysis
_Why does this variation grow faster than the standard version? How do additional move constraints affect complexity?_

> It grows faster because for each disk you add you are adding an additional 3 moves

---

## Comparative Analysis

### 1. Growth Patterns

| Version | Approx. Formula | Growth Type |
|:--|:--|:--|
| Standard | 2ⁿ − 1 | Exponential |
| Variation | 3ⁿ − 1 | Exponential (faster) |
| Iterative (Optional) | 2ⁿ − 1 | Same as recursive but loop based |

### 2. Stack Depth and Memory
_Estimate the maximum recursion depth before StackOverflowError and discuss how stack size (–Xss flag) affects this._

> You hit maximum recursion depth pretty early because the algorithm makes more than one recursive call

---

## Part 4 — Beyond Recursion (Extra Credit)

### Iterative / Explicit-Stack Version (`TowersIterative.java`)

1. How does your iterative version simulate recursion?
2. How did you track pending calls or frames?
3. Which version (r vs iterative) is clearer? Why?

> ✎ Your answer here

---

## Discussion &amp; Reflection

1. What three questions can you use to verify a recursive solution works?
2. How do the base case and recursive case cooperate to guarantee termination?
3. What is the trade-off between elegance and efficiency in recursion?

> ✎ Your answers here

---

## References (APA or MLA format)

- Dale, N., Joyce, D., &amp; Weems, C. (2016). *Object-Oriented Data Structures Using Java* (Ch. 3 Recursion). Jones &amp; Bartlett.
- Additional videos or websites you consulted (YouTube CS50 Recursion, GeeksForGeeks Hanoi, etc.)

---

 **Submission Checklist**

- [ ] `TowersOfHanoi.java` — implemented and tested
- [ ] `TowersExercise21.java` — counts moves correctly
- [ ] `TowersVariations.java` — middle-peg constraint implemented
- [ ] (Extra Credit) `TowersIterative.java` — loop or explicit stack solution
- [ ] All JUnit tests pass (green on GitHub Actions)
- [ ] This `ANSWERS.md` file completed and committed to repo  
