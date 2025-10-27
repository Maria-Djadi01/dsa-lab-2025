# 🔀 Lab 2: Decision Making & Conditional Logic

## 🎯 Learning Objectives

By the end of this lab, you'll be able to:

✅ Understand how a computer makes decisions  
✅ Use relational operators (`==`, `>`, `<`, `!=`, etc.)  
✅ Use logical operators (`&&`, `||`, `!`)  
✅ Implement `if`, `if...else`, `else if`, and `switch` statements  
✅ Write programs that behave differently based on input data  
✅ Debug and test conditional logic effectively

---

## 💡 Why Decisions Matter in Programs

### Real-World Logic Meets Code

Think about how you make decisions every day:

> **"If it's raining → take an umbrella; otherwise → wear sunglasses."**

```bash
        Start
          |
    Is it raining?
      /        \
    Yes        No
     |          |
Take umbrella  Wear sunglasses
     |          |
        End
```

Programs need the same ability: **react differently based on conditions.**

### From Daily Life to Code

**Human decision:**

- "If I'm hungry, I'll eat; if I'm thirsty, I'll drink water."

**Program decision:**

```c
if (temperature > 30) {
    printf("It's hot! Stay hydrated.\n");
} else {
    printf("Weather is comfortable.\n");
}
```

**Why this matters:**

- **Without conditionals**, programs would be linear — same output every time
- **With conditionals**, programs become intelligent — they adapt to situations
- **Real applications:** Login systems, game logic, error handling, recommendations

---

## 🧱 Building Blocks of Decisions

### Relational Operators: Comparing Values

These operators compare two values and return **true** (1) or **false** (0):

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | TRUE |
| `!=` | Not equal to | `5 != 3` | TRUE |
| `>` | Greater than | `7 > 10` | FALSE |
| `<` | Less than | `3 < 4` | TRUE |
| `>=` | Greater or equal | `4 >= 4` | TRUE |
| `<=` | Less or equal | `5 <= 2` | FALSE |

### ⚠️ The Most Common Beginner Bug

```c
// WRONG - Assignment, not comparison!
if (x = 5) {  // This assigns 5 to x, always true!
    printf("This always runs!\n");
}

// CORRECT - Comparison
if (x == 5) {  // This checks if x equals 5
    printf("x is 5\n");
}
```

**Why this is dangerous:**

- `=` is assignment (gives a value)
- `==` is comparison (checks equality)
- `if (x = 5)` assigns 5 to x, then evaluates (5 is non-zero = true)
- The condition is **always true**!

**How to avoid:**

```c
// Some programmers write constants first (Yoda style)
if (5 == x) {  // If you accidentally write =, it won't compile!
    // ...
}
```

### Understanding Truth in C

**C doesn't have a boolean type** (until C99's `_Bool`/`bool`). Instead:

- **0 means false**
- **Any non-zero value means true**

```c
if (5) {        // TRUE (5 is non-zero)
    // executes
}

if (0) {        // FALSE (0 is zero)
    // skipped
}

if (-3) {       // TRUE (non-zero)
    // executes
}
```

---

## 🧠 Logical Operators: Combining Conditions

Sometimes you need to check multiple conditions at once:

| Operator | Description | Example | When True |
|----------|-------------|---------|-----------|
| `&&` | AND | `(x > 0 && x < 10)` | Both conditions must be true |
| `\|\|` | OR | `(x > 0 \|\| y < 0)` | At least one condition is true |
| `!` | NOT | `!(x > 0)` | Reverses the truth value |

### AND Operator (`&&`)

**Both conditions must be true:**

```c
int age = 20;
int hasLicense = 1;  // 1 = true

if (age >= 18 && hasLicense) {
    printf("Can drive\n");
}
```

**Truth table:**

| Condition A | Condition B | A && B |
|-------------|-------------|--------|
| TRUE | TRUE | TRUE |
| TRUE | FALSE | FALSE |
| FALSE | TRUE | FALSE |
| FALSE | FALSE | FALSE |

**Real example:**

```c
// Check if year is leap year
if (year % 4 == 0 && year % 100 != 0) {
    printf("Leap year\n");
}
```

### OR Operator (`||`)

**At least one condition must be true:**

```c
char choice;
if (choice == 'y' || choice == 'Y') {
    printf("You said yes\n");
}
```

**Truth table:**

| Condition A | Condition B | A \|\| B |
|-------------|-------------|----------|
| TRUE | TRUE | TRUE |
| TRUE | FALSE | TRUE |
| FALSE | TRUE | TRUE |
| FALSE | FALSE | FALSE |

**Real example:**

```c
// Check if it's weekend
if (day == 6 || day == 7) {
    printf("It's weekend!\n");
}
```

### NOT Operator (`!`)

**Reverses the truth value:**

```c
int isRaining = 0;  // false

if (!isRaining) {
    printf("No rain, let's go out!\n");
}
```

**Examples:**

```c
!TRUE  → FALSE
!FALSE → TRUE
!(x > 5) → TRUE if x <= 5
```

### Short-Circuit Evaluation

**Important optimization:**

```c
if (x != 0 && 10 / x > 2) {
    // Safe! If x is 0, the second part never executes
}
```

**How it works:**

- **AND (`&&`)**: If first condition is false, second is never checked
- **OR (`||`)**: If first condition is true, second is never checked

**Why it matters:**

```c
// Prevents division by zero
if (denominator != 0 && numerator / denominator > 1) {
    // ...
}

// Prevents null pointer access
if (ptr != NULL && *ptr > 0) {
    // ...
}
```

### Complex Conditions

**Use parentheses for clarity:**

```c
// Unclear
if (x > 0 && y > 0 || z > 0)  // Which grouping?

// Clear
if ((x > 0 && y > 0) || z > 0)  // Now it's obvious
```

**Real example:**

```c
// Eligible for scholarship
if ((gpa >= 3.5 && age < 25) || specialCase) {
    printf("Eligible\n");
}
```

---

## ✅ The Basic `if` Statement

### Making Your First Decision

**Syntax:**

```c
if (condition) {
    // code to execute if condition is true
}
```

**Flowchart:**

```bash
    Start
      |
   Check condition
      |
    Is it true?
    /        \
  Yes        No
   |          |
Execute    Skip
block      block
   |          |
    End
```

### Simple Example

```c
int age = 20;

if (age >= 18) {
    printf("You are an adult\n");
}

printf("Program continues\n");
```

**What happens:**

1. Program checks: `age >= 18`
2. Condition is true (20 >= 18)
3. Message "You are an adult" is printed
4. Program continues to next statement

### ✅ Always Use Braces

```c
// Bad style (works, but risky)
if (x > 0)
    printf("Positive\n");

// Good style (clear and safe)
if (x > 0) {
    printf("Positive\n");
}
```

**Why braces matter:**

```c
// Looks like both are in the if, but only first line is!
if (x > 0)
    printf("Positive\n");
    printf("This always prints!\n");  // NOT in the if!

// Correct:
if (x > 0) {
    printf("Positive\n");
    printf("This is inside the if\n");
}
```

### Multiple Statements

```c
int score = 85;

if (score >= 60) {
    printf("You passed!\n");
    printf("Score: %d\n", score);
    printf("Congratulations!\n");
}
```

---

## 🔄 The `if...else` Statement

### Handling Both Outcomes

**When one condition must lead to two opposite results:**

```c
if (condition) {
    // code if condition is TRUE
} else {
    // code if condition is FALSE
}
```

**Flowchart:**

```bash
    Start
      |
   Check condition
      |
    Is it true?
    /        \
  Yes        No
   |          |
Execute    Execute
if block   else block
   |          |
      End
```

### Example

```c
int temperature = 35;

if (temperature > 30) {
    printf("It's hot outside\n");
} else {
    printf("It's cool outside\n");
}
```

**What happens:**

- One and only one block executes
- They are **mutually exclusive**
- No way for both to run

### Real-World Example: Login System

```c
int password = 1234;
int input;

printf("Enter password: ");
scanf("%d", &input);

if (input == password) {
    printf("Access granted\n");
} else {
    printf("Access denied\n");
}
```

### 🌡️ Best Practices

**Define clear boundaries:**

```c
// Vague
if (temp > 30) {
    printf("Hot\n");
} else {
    printf("Not hot\n");
}

// Clear
if (temp >= 30) {
    printf("Hot (30°C or above)\n");
} else {
    printf("Comfortable (below 30°C)\n");
}
```

---

## 🔢 The `if...else if...else` Chain

### Choosing Among Many Outcomes

**When you have multiple distinct cases:**

```c
if (condition1) {
    // code if condition1 is true
} else if (condition2) {
    // code if condition2 is true
} else if (condition3) {
    // code if condition3 is true
} else {
    // code if none are true
}
```

### How It Works

**Order matters!** Conditions are checked **from top to bottom**:

1. First true condition executes
2. All others are **skipped**
3. Final `else` is the default case

### Example: Grade System

```c
int score = 85;

if (score >= 90) {
    printf("Grade: A\n");
} else if (score >= 80) {
    printf("Grade: B\n");
} else if (score >= 70) {
    printf("Grade: C\n");
} else if (score >= 60) {
    printf("Grade: D\n");
} else {
    printf("Grade: F\n");
}
```

**For score = 85:**

1. Check `score >= 90`: FALSE, skip
2. Check `score >= 80`: TRUE, print "B", **stop checking**
3. Never checks remaining conditions

### 🧮 Critical: Order Your Conditions Correctly

**Wrong order:**

```c
if (score >= 60) {          // This catches everything!
    printf("Grade: D\n");
} else if (score >= 70) {   // Never reached
    printf("Grade: C\n");
} else if (score >= 80) {   // Never reached
    printf("Grade: B\n");
}
```

**For score = 85:**

- First condition (>= 60) is TRUE
- Prints "D" (wrong!)
- Never checks other conditions

**Correct order: Most restrictive first:**

```c
if (score >= 90) {          // Highest first
    printf("Grade: A\n");
} else if (score >= 80) {   // Then next highest
    printf("Grade: B\n");
}
// ... and so on
```

### Avoid Overlapping Ranges

**Confusing:**

```c
if (score >= 75 && score < 100) {  // 75-99
    printf("Good\n");
} else if (score >= 70 && score <= 80) {  // 70-80, overlaps!
    printf("Fair\n");
}
```

**Clear:**

```c
if (score >= 75) {
    printf("Good\n");
} else if (score >= 70) {  // Only checked if < 75
    printf("Fair\n");
}
```

---

## 🪆 Nested `if` Statements

### Layered Logic for Dependent Checks

**When one test is meaningless without another:**

```c
if (outer_condition) {
    if (inner_condition) {
        // Both must be true
    }
}
```

### Example: Scholarship Eligibility

```c
int year = 3;
float gpa = 3.8;

if (year >= 2) {  // Must be at least 2nd year
    if (gpa >= 3.5) {  // AND have high GPA
        printf("Eligible for scholarship\n");
    } else {
        printf("GPA too low\n");
    }
} else {
    printf("Must complete 2 years first\n");
}
```

**Why nested?**

- Checking GPA is pointless if they're first year
- Outer condition **gates** the inner condition

### 🧩 Keep Nesting Shallow

**Too deep (hard to read):**

```c
if (a) {
    if (b) {
        if (c) {
            if (d) {
                // Where am I?
            }
        }
    }
}
```

**Better: Use logical operators:**

```c
if (a && b && c && d) {
    // Much clearer!
}
```

**When to nest:**

- ✅ When conditions have different error messages
- ✅ When one test is expensive (check cheap condition first)
- ❌ When you can combine with `&&` or `||`

---

## ⚡ The Ternary Operator

### Compact One-Line Conditional

**Syntax:**

```c
variable = (condition) ? value_if_true : value_if_false;
```

**Example:**

```c
int age = 20;
char *status = (age >= 18) ? "Adult" : "Minor";
printf("%s\n", status);
```

### When to Use

**Good use:**

```c
// Simple value assignment
int max = (a > b) ? a : b;
int abs = (x >= 0) ? x : -x;
```

**Bad use (too complex):**

```c
// Don't do this!
result = (x > 0) ? ((y > 0) ? 1 : 2) : ((z > 0) ? 3 : 4);
```

### Ternary vs if-else

```c
// Using if-else (clear for complex logic)
if (balance > 0) {
    status = "Positive";
} else {
    status = "Negative";
}

// Using ternary (concise for simple cases)
status = (balance > 0) ? "Positive" : "Negative";
```

**Guidelines:**

- ✅ Use for simple value assignments
- ✅ One level deep only
- ❌ Don't chain multiple ternaries
- ❌ Don't use for complex logic

---

## 🔀 The `switch` Statement

### Decision Making with Multiple Discrete Choices

**When you have fixed possible values:**

```c
switch (expression) {
    case constant1:
        // code
        break;
    case constant2:
        // code
        break;
    default:
        // code if no case matches
}
```

### How It Works

1. **Expression is evaluated once**
2. **Compared to each case label**
3. **Match found** → execute that block
4. **`break`** → exit the switch
5. **No match** → execute `default`

### Example: Menu System

```c
int choice;
printf("1. New Game\n2. Load Game\n3. Exit\n");
scanf("%d", &choice);

switch (choice) {
    case 1:
        printf("Starting new game...\n");
        break;
    case 2:
        printf("Loading saved game...\n");
        break;
    case 3:
        printf("Goodbye!\n");
        break;
    default:
        printf("Invalid choice\n");
}
```

### ⚠️ The Importance of `break`

**Without `break` (fall-through):**

```c
int day = 2;
switch (day) {
    case 1:
        printf("Monday\n");
    case 2:
        printf("Tuesday\n");  // Prints this
    case 3:
        printf("Wednesday\n"); // Also prints this!
    default:
        printf("Other\n");     // And this!
}
// Output: Tuesday, Wednesday, Other
```

**With `break` (correct):**

```c
switch (day) {
    case 1:
        printf("Monday\n");
        break;
    case 2:
        printf("Tuesday\n");
        break;  // Stops here!
    case 3:
        printf("Wednesday\n");
        break;
}
// Output: Tuesday
```

### Intentional Fall-Through

**Sometimes useful:**

```c
char grade;
switch (grade) {
    case 'A':
    case 'B':
    case 'C':
        printf("Pass\n");
        break;
    case 'D':
    case 'F':
        printf("Fail\n");
        break;
}
```

### 💡 When to Use `switch`

**Good for:**

- ✅ Menu selections
- ✅ Fixed set of options (days, months)
- ✅ Character/integer matching
- ✅ Clean, readable code for many discrete values

**Not good for:**

- ❌ Range checking (`if (x > 10 && x < 20)`)
- ❌ String comparison (strings aren't constants in C)
- ❌ Float/double values
- ❌ Complex conditions

### Limitations

**`switch` only works with:**

- `int` (integers)
- `char` (characters)
- `enum` (enumerated types)

**NOT with:**

- `float` or `double`
- Strings (`char*` or `char[]`)
- Complex expressions

```c
// This WON'T work:
switch (name) {  // Can't switch on strings!
    case "Alice":
        // ...
}

// This WON'T work:
float x = 5.5;
switch (x) {  // Can't switch on float!
    case 5.5:
        // ...
}
```

---

## 📊 Switch vs. If-Else: When to Use What

| Use Case | Recommended Statement |
|----------|----------------------|
| Range of values (`x > 10 && x < 20`) | `if` / `else` |
| Exact discrete values (`x == 1, 2, 3`) | `switch` |
| Complex logic with `&&`, `\|\|` | `if` / `else` |
| Menu selection (1, 2, 3, 4) | `switch` |
| String comparison | `if` / `else` |
| Float/double checking | `if` / `else` |

### Example Comparison

**Using if-else:**

```c
if (choice == 1) {
    printf("Option 1\n");
} else if (choice == 2) {
    printf("Option 2\n");
} else if (choice == 3) {
    printf("Option 3\n");
} else {
    printf("Invalid\n");
}
```

**Using switch:**

```c
switch (choice) {
    case 1:
        printf("Option 1\n");
        break;
    case 2:
        printf("Option 2\n");
        break;
    case 3:
        printf("Option 3\n");
        break;
    default:
        printf("Invalid\n");
}
```

**Switch is cleaner for:** Many fixed integer/char values  
**If-else is better for:** Ranges, complex conditions, non-integer types

---

## 🐛 Common Mistakes and How to Avoid Them

### 1. Using `=` instead of `==`

```c
// WRONG
if (x = 5) {  // Assignment!
    // Always executes
}

// CORRECT
if (x == 5) {  // Comparison
    // Only if x equals 5
}
```

### 2. Forgetting Braces

```c
// Dangerous
if (x > 0)
    printf("Positive\n");
    x = 0;  // NOT in the if! Always executes

// Safe
if (x > 0) {
    printf("Positive\n");
    x = 0;  // Now inside the if
}
```

### 3. Wrong Operator Precedence

```c
// Wrong
if (x > 0 && < 10)  // Syntax error!

// Correct
if (x > 0 && x < 10)
```

### 4. Semicolon After if

```c
// WRONG - Semicolon ends the if statement!
if (x > 0);
{
    printf("This always prints!\n");
}

// CORRECT
if (x > 0) {
    printf("Positive\n");
}
```

### 5. Forgetting `break` in switch

```c
// Falls through to next case!
switch (choice) {
    case 1:
        printf("One\n");
    case 2:  // No break above!
        printf("Two\n");  // Prints even if choice was 1!
}
```

---

## 🧪 Testing Conditional Logic

### Test All Paths

**For this code:**

```c
if (score >= 90) {
    printf("A\n");
} else if (score >= 80) {
    printf("B\n");
} else {
    printf("C or lower\n");
}
```

**Test cases:**

- score = 95 (path 1)
- score = 85 (path 2)
- score = 75 (path 3)
- score = 90 (boundary)
- score = 80 (boundary)

### Boundary Value Testing

Always test:

- **Just below** the boundary
- **At** the boundary
- **Just above** the boundary

```c
// For: if (age >= 18)
Test with: 17, 18, 19
```

---

## 📚 Summary

### Key Takeaways

1. **Relational operators** (`==`, `!=`, `<`, `>`, `<=`, `>=`) compare values
2. **Logical operators** (`&&`, `||`, `!`) combine conditions
3. **`if`** executes code when condition is true
4. **`if...else`** handles binary decisions
5. **`if...else if...else`** chains handle multiple cases
6. **`switch`** is for discrete integer/char values
7. **Always use braces** for clarity and safety
8. **Test all paths** including boundaries
