# 🔄 Lab 3: Iterative Structures (Loops)

## 🎯 Learning Objectives

By the end of this lab, you'll be able to:

✅ Understand why loops are fundamental to programming  
✅ Implement `while`, `do-while`, and `for` loops  
✅ Choose the appropriate loop type for each situation  
✅ Use `break` and `continue` for loop control  
✅ Write and debug nested loops  
✅ Recognize and apply common loop patterns  
✅ Avoid common loop pitfalls and infinite loops

---

## 💡 Why Loops Matter

### The Problem: Repetition Without Loops

Imagine you need to print numbers 1 to 100:

```c
printf("1\n");
printf("2\n");
printf("3\n");
// ... 97 more lines ...
printf("100\n");
```

**Problems with this approach:**
- **Tedious to write** — 100 lines of nearly identical code
- **Hard to maintain** — change one thing, change 100 lines
- **Not scalable** — what if you need 1000 numbers?
- **Not dynamic** — can't adjust based on user input
- **Error-prone** — easy to make typos or skip numbers

### The Solution: Loops

```c
for (int i = 1; i <= 100; i++) {
    printf("%d\n", i);
}
```

**Just 3 lines!** And it's:

- ✅ Easy to read and understand
- ✅ Simple to modify (change 100 to any number)
- ✅ Dynamic (can use variables)
- ✅ Less error-prone

---

## 🌍 Real-World Applications of Loops

### Where Loops Are Used

**1. Processing Collections**

```c
// Calculate average of all student grades
for (int i = 0; i < num_students; i++) {
    sum += grades[i];
}
average = sum / num_students;
```

**2. User Interfaces**

```c
// ATM menu - keep showing until user exits
do {
    display_menu();
    choice = get_user_choice();
    process_choice(choice);
} while (choice != EXIT);
```

**3. File Processing**

```c
// Read entire file
while (!feof(file)) {
    read_line(file);
    process_line();
}
```

**4. Game Development**

```c
// Main game loop
while (game_running) {
    handle_input();
    update_game_state();
    render_frame();
}
```

**5. Scientific Computing**

```c
// Numerical approximation
while (error > threshold) {
    new_estimate = calculate();
    error = abs(new_estimate - old_estimate);
    old_estimate = new_estimate;
}
```

---

## 🔁 The While Loop

### Concept and Syntax

```c
while (condition) {
    // code to repeat
}
```

**How it works:**

1. **Check condition** before entering loop
2. If **true** → execute body
3. Return to step 1
4. If **false** → skip loop entirely

### Execution Flow

```bash
        Start
          |
      [condition]  ←──┐
        /    \        │
     true   false     │
       |      |       │
   Execute  Exit      │
    body     |        │
       └──────┘       │
                     ↓
                   End
```

### Key Characteristics

- **Pre-test loop** — condition checked before execution
- **May not execute at all** — if condition initially false
- **Number of iterations unknown** — depends on condition
- **Must update condition** — or loop runs forever

---

## 📝 While Loop Examples

### Example 1: Count to 10

```c
int count = 1;

while (count <= 10) {
    printf("%d\n", count);
    count++;
}
```

**Step-by-step execution:**

```
Iteration 1: count=1, check 1<=10 (true), print 1, count becomes 2
Iteration 2: count=2, check 2<=10 (true), print 2, count becomes 3
...
Iteration 10: count=10, check 10<=10 (true), print 10, count becomes 11
Check: 11<=10 (false), EXIT loop
```

### Example 2: Input Validation

```c
int age;

printf("Enter age (1-120): ");
scanf("%d", &age);

while (age < 1 || age > 120) {
    printf("Invalid! Try again: ");
    scanf("%d", &age);
}

printf("Valid age: %d\n", age);
```

**Why while?**

- Don't know how many invalid attempts
- Might be valid first try (0 iterations)
- Keep asking until valid

### Example 3: Sum Until Negative

```c
int num, sum = 0;

printf("Enter numbers (negative to stop):\n");
scanf("%d", &num);

while (num >= 0) {
    sum += num;
    scanf("%d", &num);
}

printf("Sum: %d\n", sum);
```

---

## ⚠️ Common While Loop Mistakes

### Mistake 1: Infinite Loop (Forgot to Update)

```c
int i = 1;
while (i <= 10) {
    printf("%d\n", i);
    // Forgot i++!
}
// Prints 1 forever!
```

**Why it happens:**

- `i` never changes
- Condition always true
- Loop never exits

**How to fix:**

```c
int i = 1;
while (i <= 10) {
    printf("%d\n", i);
    i++;  // Update the condition variable!
}
```

### Mistake 2: Wrong Condition

```c
int i = 1;
while (i != 10) {
    printf("%d\n", i);
    i += 2;  // 1, 3, 5, 7, 9, 11...
}
// Infinite! i skips over 10
```

**Fix: Use < or <=**

```c
while (i < 10) {
    printf("%d\n", i);
    i += 2;
}
```

### Mistake 3: Semicolon After While

```c
int i = 0;
while (i < 5);  // Semicolon creates empty loop!
{
    printf("%d\n", i);
    i++;
}
// Infinite empty loop, never reaches printf
```

**Fix: Remove semicolon**

```c
while (i < 5) {
    printf("%d\n", i);
    i++;
}
```

---

## 🔄 The Do-While Loop

### Concept and Syntax

```c
do {
    // code to repeat
} while (condition);  // Note the semicolon!
```

**How it works:**
1. **Execute body first** (always at least once)
2. **Then check condition**
3. If **true** → repeat from step 1
4. If **false** → exit loop

### Execution Flow

```
        Start
          |
      Execute  ←──┐
       body       │
          |       │
    [condition]   │
        /    \    │
     true   false │
       └────┘     │
                  ↓
                End
```

### Key Characteristics

- **Post-test loop** — condition checked after execution
- **Always executes at least once** — guaranteed
- **Good for menus** — show menu before checking choice
- **Still needs condition update** — to avoid infinite loop

---

## 📋 Do-While Loop Examples

### Example 1: Menu System

```c
int choice;

do {
    printf("\n=== Main Menu ===\n");
    printf("1. Start Game\n");
    printf("2. Load Game\n");
    printf("3. Settings\n");
    printf("4. Exit\n");
    printf("Choice: ");
    scanf("%d", &choice);
    
    switch (choice) {
        case 1: start_game(); break;
        case 2: load_game(); break;
        case 3: settings(); break;
        case 4: printf("Goodbye!\n"); break;
        default: printf("Invalid choice!\n");
    }
    
} while (choice != 4);
```

**Why do-while?**

- Menu must display at least once
- User can't choose without seeing options
- Check happens after displaying

### Example 2: Password Attempt

```c
int password = 1234;
int attempt;
int tries = 0;

do {
    printf("Enter password: ");
    scanf("%d", &attempt);
    tries++;
    
    if (attempt != password) {
        printf("Wrong! Try again.\n");
    }
    
} while (attempt != password && tries < 3);

if (attempt == password) {
    printf("Access granted!\n");
} else {
    printf("Too many failed attempts!\n");
}
```

### Example 3: Play Again?

```c
char playAgain;

do {
    play_game();
    
    printf("Play again? (y/n): ");
    scanf(" %c", &playAgain);
    
} while (playAgain == 'y' || playAgain == 'Y');
```

---

## 🆚 While vs Do-While

### The Critical Difference

**while:** Check first, maybe execute

```c
int x = 10;
while (x < 5) {
    printf("Never prints\n");
}
// Loop body never executes
```

**do-while:** Execute first, then check

```c
int x = 10;
do {
    printf("Prints once\n");
} while (x < 5);
// Loop body executes once, then exits
```

### When to Use Each

| Use While When | Use Do-While When |
|----------------|-------------------|
| May not need to execute at all | Must execute at least once |
| Input validation (might be valid first try) | Menu systems (must show options) |
| Reading until condition met | "Try this, then check" scenarios |
| Don't know if any iterations needed | Game loops (run once before checking quit) |

### Conversion Between Them

**Any do-while can become while:**

```c
// do-while
do {
    code();
} while (condition);

// Equivalent while
code();  // Execute once first
while (condition) {
    code();
}
```

**But while can't always become do-while** (if zero iterations needed)

---

## 🔢 The For Loop

### Concept and Syntax

```c
for (initialization; condition; update) {
    // code to repeat
}
```

**Three parts:**

1. **Initialization** — runs once before loop starts
2. **Condition** — checked before each iteration
3. **Update** — runs after each iteration

### Execution Flow

```bash
         Start
           |
    [Initialize]
           |
      [Condition] ←────┐
         /    \        │
      true   false     │
        |      |       │
    Execute  Exit      │
     body     |        │
        |     |        │
    [Update]  |        │
        └──────────────┘
```

### How It Works

```c
for (i = 1; i <= 5; i++) {
    printf("%d\n", i);
}
```

**Step-by-step:**

```bash
1. i = 1          (initialization, once)
2. Check 1 <= 5   (true)
3. Print 1        (body)
4. i++            (update, i becomes 2)
5. Check 2 <= 5   (true)
6. Print 2        (body)
7. i++            (update, i becomes 3)
... continues until i = 6
8. Check 6 <= 5   (false)
9. EXIT loop
```

---

## 🎯 For Loop Examples

### Example 1: Count Forward

```c
for (int i = 1; i <= 10; i++) {
    printf("%d ", i);
}
// Output: 1 2 3 4 5 6 7 8 9 10
```

### Example 2: Count Backward

```c
for (int i = 10; i >= 1; i--) {
    printf("%d ", i);
}
printf("Blastoff!\n");
// Output: 10 9 8 7 6 5 4 3 2 1 Blastoff!
```

### Example 3: Custom Step

```c
// Multiples of 5
for (int i = 0; i <= 50; i += 5) {
    printf("%d ", i);
}
// Output: 0 5 10 15 20 25 30 35 40 45 50
```

### Example 4: Characters

```c
for (char c = 'A'; c <= 'Z'; c++) {
    printf("%c ", c);
}
// Output: A B C D ... X Y Z
```

### Example 5: Process Array

```c
int scores[] = {85, 92, 78, 95, 88};
int sum = 0;

for (int i = 0; i < 5; i++) {
    sum += scores[i];
}

float average = sum / 5.0;
printf("Average: %.2f\n", average);
```

---

## 🔄 For Loop Variations

### Standard (Most Common)

```c
for (int i = 0; i < n; i++) {
    // Forward iteration from 0 to n-1
}
```

### Backward Iteration

```c
for (int i = n-1; i >= 0; i--) {
    // Backward from n-1 to 0
}
```

### Skip Values

```c
for (int i = 0; i < n; i += 2) {
    // Process even indices: 0, 2, 4, 6...
}
```

### Multiple Variables (Comma Operator)

```c
for (int i = 0, j = 10; i < j; i++, j--) {
    printf("i=%d, j=%d\n", i, j);
}
// i counts up, j counts down simultaneously
```

### Infinite Loop

```c
for (;;) {
    // All three parts optional
    // Same as while(1)
    if (condition) break;
}
```

### Empty Body

```c
for (int i = 0; i < n; i++);  // Semicolon makes empty loop
// Used rarely for delays or intentional no-op
```

---

## 🤔 Choosing the Right Loop

### Decision Matrix

```bash
Do you know the exact number of iterations?
│
├─ YES → Use for loop
│   ├─ Processing array? → for (i = 0; i < size; i++)
│   ├─ Count n times? → for (i = 1; i <= n; i++)
│   └─ Range of values? → for (i = start; i <= end; i++)
│
└─ NO → Is condition based or indefinite?
    │
    ├─ Must execute at least once?
    │   ├─ YES → Use do-while
    │   │   ├─ Menu system? → do-while with choice check
    │   │   └─ Try-then-check? → do-while
    │   │
    │   └─ NO → Use while
    │       ├─ Input validation? → while (invalid)
    │       ├─ Read until EOF? → while (!eof)
    │       └─ Condition-based? → while (condition)
    │
    └─ Complex condition? → while is clearest
```

### Quick Reference Table

| Scenario | Best Loop | Example |
|----------|-----------|---------|
| Process array of size n | `for` | `for (i = 0; i < n; i++)` |
| Read numbers until negative | `while` | `while (num >= 0)` |
| Show menu at least once | `do-while` | `do { menu(); } while(choice != 0)` |
| Count from 1 to 100 | `for` | `for (i = 1; i <= 100; i++)` |
| Read file until EOF | `while` | `while (!feof(file))` |
| Password with retry limit | `do-while` | `do { } while (wrong && tries < 3)` |
| Search array | `for` + `break` | Find element, exit early |

---

## 🛑 Loop Control Statements

### The `break` Statement

**Purpose:** Exit loop immediately, regardless of condition

```c
while (1) {  // Infinite loop
    scanf("%d", &num);
    
    if (num < 0) {
        break;  // Exit when negative
    }
    
    process(num);
}
```

**What happens:**

1. Loop condition (1) is always true
2. When `num < 0`, `break` executes
3. Control jumps to after loop
4. Rest of loop body skipped

### Break in Different Loops

**In for loop:**

```c
for (int i = 0; i < 100; i++) {
    if (found_it) {
        break;  // Exit early, don't check all 100
    }
}
```

**In while loop:**

```c
while (condition) {
    if (error_occurred) {
        break;  // Exit on error
    }
}
```

**In nested loops:**

```c
for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
        if (found) {
            break;  // Only exits inner loop!
        }
    }
    // break lands here
}
```

**Important:** `break` only exits the **innermost** loop!

---

### The `continue` Statement

**Purpose:** Skip rest of current iteration, go to next

```c
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) {
        continue;  // Skip even numbers
    }
    printf("%d\n", i);  // Only prints odd
}
// Output: 1 3 5 7 9
```

**What happens:**

1. When `i` is even, `continue` executes
2. Rest of loop body skipped
3. Update (i++) still happens
4. Condition checked for next iteration

### Continue vs Break

```c
// break: Stop loop entirely
for (int i = 1; i <= 5; i++) {
    if (i == 3) break;
    printf("%d ", i);
}
// Output: 1 2

// continue: Skip to next iteration
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;
    printf("%d ", i);
}
// Output: 1 2 4 5
```

### When to Use Each

| Use `break` When | Use `continue` When |
|------------------|---------------------|
| Found what you're looking for | Skip invalid items |
| Error condition, must stop | Skip certain values |
| Early exit optimization | Process only matching items |
| Search complete | Filter within loop |

---

## 🎯 Common Loop Patterns

### Pattern 1: Accumulator

**Purpose:** Build up a result over iterations

```c
// Sum of numbers
int sum = 0;
for (int i = 1; i <= 100; i++) {
    sum += i;
}
printf("Sum: %d\n", sum);  // 5050
```

**Key steps:**

1. Initialize accumulator before loop (often to 0)
2. Update accumulator in loop body
3. Use accumulated result after loop

**Variations:**

```c
// Product
int product = 1;  // Start with 1, not 0!
for (int i = 1; i <= n; i++) {
    product *= i;  // Factorial
}

// String concatenation
char result[100] = "";
for (int i = 0; i < n; i++) {
    strcat(result, words[i]);
}
```

---

### Pattern 2: Counter

**Purpose:** Count items meeting a condition

```c
// Count even numbers
int count = 0;
for (int i = 1; i <= 100; i++) {
    if (i % 2 == 0) {
        count++;
    }
}
printf("Even numbers: %d\n", count);
```

**Common uses:**

- Count occurrences
- Count valid items
- Track frequency
- Statistics

```c
// Count vowels in string
int vowels = 0;
for (int i = 0; str[i] != '\0'; i++) {
    char c = tolower(str[i]);
    if (c=='a' || c=='e' || c=='i' || c=='o' || c=='u') {
        vowels++;
    }
}
```

---

### Pattern 3: Find Min/Max

**Purpose:** Track extreme values

```c
// Find maximum
int numbers[] = {45, 23, 67, 12, 89, 34};
int max = numbers[0];  // Initialize with first

for (int i = 1; i < 6; i++) {
    if (numbers[i] > max) {
        max = numbers[i];
    }
}
printf("Maximum: %d\n", max);
```

**Why start with first element?**

- Guarantees max is from the array
- Works even if all numbers negative
- No need for "impossible" initial value

**Tracking position:**

```c
int maxIndex = 0;
for (int i = 1; i < size; i++) {
    if (arr[i] > arr[maxIndex]) {
        maxIndex = i;  // Remember where it is
    }
}
printf("Max %d at position %d\n", arr[maxIndex], maxIndex);
```

---

### Pattern 4: Search

**Purpose:** Find if/where item exists

```c
// Linear search
int target = 42;
int found = 0;
int position = -1;

for (int i = 0; i < size; i++) {
    if (arr[i] == target) {
        found = 1;
        position = i;
        break;  // Stop once found
    }
}

if (found) {
    printf("Found at position %d\n", position);
} else {
    printf("Not found\n");
}
```

**Optimization:** Use `break` to exit early when found!

---

### Pattern 5: Validation

**Purpose:** Check all items meet condition

```c
// Check if array is sorted
int sorted = 1;  // Assume sorted

for (int i = 0; i < size - 1; i++) {
    if (arr[i] > arr[i+1]) {
        sorted = 0;  // Found violation
        break;
    }
}

if (sorted) {
    printf("Array is sorted\n");
} else {
    printf("Array is not sorted\n");
}
```

**Pattern:** Assume true, look for violations

---

## 🪆 Nested Loops

### Concept

**Loop inside another loop:**

```c
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        printf("(%d,%d) ", i, j);
    }
    printf("\n");
}
```

**Output:**

```bash
(1,1) (1,2) (1,3)
(2,1) (2,2) (2,3)
(3,1) (3,2) (3,3)
```

### How Nested Loops Execute

```bash
Outer i=1:
  Inner j=1: print (1,1)
  Inner j=2: print (1,2)
  Inner j=3: print (1,3)
  Print newline

Outer i=2:
  Inner j=1: print (2,1)
  Inner j=2: print (2,2)
  Inner j=3: print (2,3)
  Print newline

Outer i=3:
  Inner j=1: print (3,1)
  Inner j=2: print (3,2)
  Inner j=3: print (3,3)
  Print newline
```

**Key insight:** Inner loop completes fully for each outer iteration

### Total Iterations

```c
for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
        // ...
    }
}
```

**Total iterations = m × n**

Example: m=5, n=10 → 50 total iterations

---

## 📐 Nested Loop Examples

### Example 1: Multiplication Table

```c
printf("    ");
for (int i = 1; i <= 10; i++) {
    printf("%4d", i);
}
printf("\n");

for (int i = 1; i <= 10; i++) {
    printf("%3d:", i);
    for (int j = 1; j <= 10; j++) {
        printf("%4d", i * j);
    }
    printf("\n");
}
```

**Output:**

```bash
       1   2   3   4   5   6   7   8   9  10
  1:   1   2   3   4   5   6   7   8   9  10
  2:   2   4   6   8  10  12  14  16  18  20
  ...
```

### Example 2: Pattern Printing

**Right triangle:**
```c
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++) {
        printf("* ");
    }
    printf("\n");
}
```

**Output:**

```bash
*
* *
* * *
* * * *
* * * * *
```

**Pyramid:**

```c
int rows = 5;
for (int i = 1; i <= rows; i++) {
    // Spaces
    for (int j = 1; j <= rows - i; j++) {
        printf(" ");
    }
    // Stars
    for (int j = 1; j <= 2*i - 1; j++) {
        printf("*");
    }
    printf("\n");
}
```

**Output:**

```bash
    *
   ***
  *****
 *******
*********
```

### Example 3: Matrix Operations

**Print 2D array:**

```c
int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        printf("%3d", matrix[i][j]);
    }
    printf("\n");
}
```

---

## ⚠️ Common Loop Mistakes

### Mistake 1: Off-By-One Error

```c
// Wrong: Misses last element
int arr[10];
for (int i = 0; i < 9; i++) {  // Should be i < 10
    arr[i] = 0;
}
// arr[9] is uninitialized!

// Wrong: Goes past array
for (int i = 0; i <= 10; i++) {  // Should be i < 10
    arr[i] = 0;  // arr[10] out of bounds!
}
```

**Fix:** Be careful with `<` vs `<=`

### Mistake 2: Modifying Loop Variable

```c
// Dangerous!
for (int i = 0; i < 10; i++) {
    printf("%d\n", i);
    i += 2;  // Also modifying i!
}
// Unpredictable behavior
```

**Fix:** Let loop control the variable

### Mistake 3: Wrong Loop Type

```c
// Using while when for is clearer
int i = 0;
while (i < n) {
    process(arr[i]);
    i++;
}

// Better: Use for
for (int i = 0; i < n; i++) {
    process(arr[i]);
}
```

### Mistake 4: Infinite Loop from Typo

```c
// Typo: ; instead of ,
for (int i = 0; i < 10; i++) ; {
    printf("%d\n", i);
}
// Semicolon creates empty infinite loop!
```

### Mistake 5: Nested Loop Break Confusion

```c
for (int i = 0; i < m; i++) {
    for (int j = 0; j < n; j++) {
        if (found) {
            break;  // Only exits inner loop!
        }
    }
    // Outer loop continues
}
```

**Solution:** Use flag or goto (rarely)

---

## 🧪 Testing Loops

### Test Cases to Try

**For any loop:**

1. **Zero iterations**

   ```c
   for (int i = 0; i < 0; i++) { }  // Never executes
   ```

2. **One iteration**

   ```c
   for (int i = 0; i < 1; i++) { }  // Executes once
   ```

3. **Normal case**

   ```c
   for (int i = 0; i < 10; i++) { }  // Typical
   ```

4. **Boundary values**

   ```c
   for (int i = 0; i <= n; i++) { }  // Test with n=0, n=1
   ```

5. **Large values**

   ```c
   for (int i = 0; i < 1000000; i++) { }  // Performance
   ```

### Debugging Loops

**Add debug output:**

```c
for (int i = 0; i < n; i++) {
    printf("DEBUG: iteration %d, i=%d\n", iteration++, i);
    // Your code
    printf("DEBUG: result so far=%d\n", result);
}
```

**Check loop invariants:**

```c
for (int i = 0; i < n; i++) {
    // Before body: i should be valid index
    assert(i >= 0 && i < n);
    
    // Your code
    
    // After body: check consistency
    assert(sum >= 0);  // If expecting positive sum
}
```

---

## 💪 Advanced Loop Techniques

### Loop Unrolling (Optimization)

**Normal loop:**

```c
for (int i = 0; i < 100; i++) {
    arr[i] = 0;
}
```

**Unrolled (faster for large arrays):**

```c
for (int i = 0; i < 100; i += 4) {
    arr[i] = 0;
    arr[i+1] = 0;
    arr[i+2] = 0;
    arr[i+3] = 0;
}
```

**Why?** Reduces loop overhead, but less readable.

### Sentinel-Controlled Loop

```c
// Process until special value
int num;
do {
    scanf("%d", &num);
    if (num != -999) {  // -999 is sentinel
        process(num);
    }
} while (num != -999);
```

### Early Loop Exit Optimization

```c
// Stop checking once impossible
int found = 0;
for (int i = 0; i < n && !found; i++) {
    if (arr[i] == target) {
        found = 1;
    }
}
```

---

## 📚 Summary

### Key Takeaways

**1. Three Loop Types:**

- `while` — condition first, may not execute
- `do-while` — execute first, at least once
- `for` — counted iterations, most common

**2. Common Mistakes:**

- Off-by-one errors
- Modifying loop variables
- Using wrong loop types
- Infinite loops from typos
- Nested loop break confusion

**3. Testing and Debugging:**

- Test with edge cases
- Add debug output
- Check loop invariants

**4. Advanced Techniques:**

- Loop unrolling for optimization
- Sentinel-controlled loops
- Early exit strategies