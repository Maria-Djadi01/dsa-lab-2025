# 🔄 Lab 3: Homework Assignment

## Problem: Prime Numbers and Statistics Calculator

Create a program that analyzes prime numbers in a given range and calculates various statistics.

---

## Requirements

Your program must:

1. **Accept input:** Start and end of range (inclusive)
2. **Find all prime numbers** in that range
3. **Calculate and display statistics:**
   - List all prime numbers found
   - Total count of primes
   - Sum of all primes
   - Average of all primes
   - Largest and smallest prime in range
   - Count of twin primes (primes that differ by 2, like 11 and 13)

---

## Example Output

```bash
=== Prime Number Analyzer ===

Enter start of range: 10
Enter end of range: 50

Analyzing range [10, 50]...

Prime Numbers Found:
11 13 17 19 23 29 31 37 41 43 47

=== Statistics ===
Total Primes: 11
Sum: 311
Average: 28.27
Smallest: 11
Largest: 47

Twin Prime Pairs:
(11, 13)
(17, 19)
(29, 31)
(41, 43)
Total Twin Prime Pairs: 4
```

---

## Requirements Checklist

Your program must:

- [ ] Use a function (or loop) to check if a number is prime
- [ ] Use a for loop to iterate through the range
- [ ] Use accumulators to track sum and count
- [ ] Find min and max primes
- [ ] Identify twin prime pairs
- [ ] Display results in a clear format
- [ ] Handle edge cases (no primes in range, invalid input)

---

## Test Cases

### Test Case 1: Small Range

```bash
Input: 1 to 20
Expected:
  Primes: 2 3 5 7 11 13 17 19
  Count: 8
  Twin pairs: (3,5), (5,7), (11,13), (17,19)
```

### Test Case 2: No Primes

```bash
Input: 24 to 28
Expected:
  Primes: None
  Count: 0
  Message: "No primes found in range"
```

### Test Case 3: Large Range

```bash
Input: 1 to 100
Expected:
  Count: 25
  Sum: 1060
  Average: 42.40
```

---

## Grading Rubric (100 points)

### Correctness (60%)

- [ ] Correctly identifies all primes (20%)
- [ ] Statistics calculated correctly (20%)
- [ ] Twin primes identified correctly (10%)
- [ ] Edge cases handled (10%)

### Code Quality (25%)

- [ ] Clean, readable code (5%)
- [ ] Proper variable names (5%)
- [ ] Good comments (5%)
- [ ] Efficient algorithm (5%)
- [ ] No compiler warnings (5%)

### Output Format (15%)

- [ ] Clear section headers (5%)
- [ ] Proper formatting (5%)
- [ ] Professional appearance (5%)

---

## Submission

1. Accept GitHub Classroom assignment: [Accept assignment on GitHub Classroom](https://classroom.github.com/a/flWwVSX1)
2. Clone your repository
3. Write your code in `prime_analyzer.c`
4. Test with all test cases above
5. Commit and push:

   ```bash
   git add prime_analyzer.c
   git commit -m "Complete prime analyzer"
   git push
   ```

---

## Tips

### Start Simple

1. First, just find and print primes
2. Then add statistics (sum, count, average)
3. Then add min/max
4. Finally add twin primes

### Debugging

- Test prime checking separately first
- Print primes as you find them
- Verify calculations manually for small ranges

### Efficiency

```c
// Optimization: Only check up to √n
for (int i = 2; i * i <= num; i++) {
    // Much faster than checking all numbers up to num
}
```

### Common Mistakes to Avoid

- Not handling the case where no primes exist
- Off-by-one errors in range (inclusive vs exclusive)
- Integer division in average calculation (use float!)
- Forgetting to break after finding a divisor

---

## Mathematical Background

### What is a Prime Number?

A prime number is a natural number greater than 1 that has no positive divisors other than 1 and itself.

**Examples:**

- 2, 3, 5, 7, 11, 13, 17, 19, 23, 29...

**Not prime:**

- 1 (by definition)
- 4 = 2 × 2
- 6 = 2 × 3
- 9 = 3 × 3

### Twin Primes

Two prime numbers that differ by 2.

**Examples:**

- (3, 5), (5, 7), (11, 13), (17, 19), (29, 31)

**Fun fact:** It's unknown if there are infinitely many twin primes!

### Why Check Only Up to √n?

If n = a × b and a ≤ √n, then b ≥ √n.

So if n has a divisor, at least one must be ≤ √n.

**Example:** For n = 36

- √36 = 6
- Divisors: 2, 3, 4, 6, 9, 12, 18
- We only need to check 2, 3, 4, 5, 6
- If no divisor found up to 6, then 36 is prime (it's not, but the logic holds)

---

**Good luck! Start early and test thoroughly!**
