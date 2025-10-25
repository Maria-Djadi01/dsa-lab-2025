# 🧩 Lab 1: Basic Concepts & Basic Actions  

## 🚀 Welcome to C Programming

C is a **general-purpose programming language** created in **1972 by Dennis Ritchie** at Bell Labs.  
It's the foundation of many modern languages including **C++**, **Java**, and **Python** and is still widely used today because it's:

- **Fast and efficient** — gives you direct access to memory and hardware.  
- **Powerful and flexible** — used in OS kernels (Linux, Windows), databases, and embedded systems.  
- **Fundamental for learning algorithms and data structures.**

> Learning C helps you understand how computers *really* work — memory, logic, and performance at their core.

### 🤔 Why C Still Matters in 2025

**Historical Significance:**

- C was designed to rewrite the UNIX operating system, making it portable across different machines
- Before C, operating systems were written in assembly language — tied to specific hardware
- C introduced the revolutionary concept of "write once, compile anywhere"

**Modern Relevance:**

- **Operating Systems:** Linux kernel, Windows NT kernel, macOS core components
- **Embedded Systems:** Your smartphone, car, microwave — all run C code
- **Performance-Critical Applications:** Databases (PostgreSQL, MySQL), game engines, compilers
- **IoT and Edge Computing:** Resource-constrained devices need C's efficiency

**Why Learn C First?**

1. **No magic, no hidden complexity** — every operation is explicit
2. **Teaches memory management** — you understand what happens "under the hood"
3. **Foundation for understanding higher-level languages** — Java's JVM, Python's CPython interpreter are written in C
4. **Algorithmic thinking** — forces you to think about efficiency and resources

---

## 🎯 Why Learn C?

### The Philosophy of C

C follows the principle: **"Trust the programmer."**

- Gives you complete control but expects responsibility
- Doesn't protect you from mistakes — you learn by debugging
- Minimal runtime overhead — your code runs close to hardware speed

### What Makes C Different?

| Aspect | C | Higher-Level Languages |
|--------|---|------------------------|
| **Memory Management** | Manual (you allocate/free) | Automatic (garbage collection) |
| **Performance** | Direct hardware access | Runtime interpretation overhead |
| **Abstraction Level** | Low-level (close to machine) | High-level (abstract concepts) |
| **Compilation** | Compiles to native code | Often interpreted or JIT compiled |
| **Learning Curve** | Steeper (more concepts) | Gentler (many details hidden) |

### Real-World Impact

**Example:** Why is Linux written in C?

- **Performance:** Kernel needs to be fast — C compiles to efficient machine code
- **Portability:** Linux runs on everything from phones to supercomputers
- **Control:** Direct hardware access without abstraction layers
- **Predictability:** No unexpected garbage collection pauses

---

## 🧰 Development Environment Setup

### Understanding the Compilation Process

Before we write code, let's understand what happens when you "run" a C program:

```
Source Code (.c) → Preprocessor → Compiler → Assembler → Linker → Executable
```

1. **Preprocessor** — Handles `#include` and `#define` directives
2. **Compiler** — Converts C code to assembly language
3. **Assembler** — Converts assembly to machine code (object files)
4. **Linker** — Combines object files with libraries into final executable

### Choosing Your Tools

#### **Code Editors:**

- **Code::Blocks** 
- **Visual Studio Code**
- **Dev-C++**

### First Compilation

```bash
# Compile a program
gcc hello.c -o hello

# With warnings enabled (ALWAYS do this!)
gcc -Wall -Wextra hello.c -o hello

# Run the program
./hello
```

**What do these flags mean?**

- `-Wall` — Enable all common warnings
- `-Wextra` — Enable extra warnings
- `-o hello` — Name the output file "hello"
- `-lm` — Link math library (needed for math.h functions)

**Why enable warnings?**

- Catches potential bugs before runtime
- Teaches you good practices
- Professional code always compiles without warnings

---

## 🧩 Anatomy of a Simple C Program

```c
#include <stdio.h>   // Include standard input/output library

int main() {         // Program execution starts here
    printf("Hello, world!\n");  // Display output
    return 0;        // End program successfully
}
```

### Deep Dive: What's Really Happening?

#### `#include <stdio.h>`

**What it does:**

- Includes the Standard Input/Output header file
- Contains declarations for `printf()`, `scanf()`, etc.

**Why angle brackets `< >`?**

- Tells compiler to look in system directories
- Use quotes `" "` for your own header files: `#include "myheader.h"`

**What's in stdio.h?**

- Function declarations (prototypes)
- Macro definitions
- Type definitions

#### `int main()`

**Why `int`?**

- `main()` returns an integer to the operating system
- `0` means success, non-zero means error
- This is how shell scripts check if commands succeeded

**The Operating System Connection:**

```c
int main() {
    // Your code here
    return 0;  // Tell OS: "Everything went fine"
}
```

When you run `./program`, the OS:

1. Loads your executable into memory
2. Calls `main()`
3. Receives the return value
4. Uses it to determine if program succeeded

#### `printf("Hello, world!\n");`

**How does printf work?**

- It's a **variadic function** — takes variable number of arguments
- Interprets format specifiers at runtime
- Sends output to **standard output** (stdout)

**Why the `\n`?**

- Newline character — moves cursor to next line
- This is called "line buffering"

#### Comments

```c
// Single-line comment — ignored by compiler

/*
 * Multi-line comment
 * Can span multiple lines
 * Often used for documentation
 */
```

**Best Practices:**

- Comment *why*, not *what* — code shows what you're doing
- Bad: `x = x + 1; // Increment x`
- Good: `x++; // Move to next array position after processing`

---

## 🧮 Data Types and Variables

### Understanding Memory

**The fundamental concept:** Variables are named locations in memory.

```text
Memory (RAM):
┌─────┬─────┬─────┬─────┬─────┐
│  ?  │  ?  │  ?  │  ? │  ?  │  (Uninitialized)
└─────┴─────┴─────┴─────┴─────┘
Address: 1000  1004  1008  1012  1016

int age = 20;
┌─────┬─────┬─────┬─────┬─────┐
│ 20  │  ?  │  ?  │  ?  │  ?  │
└─────┴─────┴─────┴─────┴─────┘
        ↑
      "age" lives here (address 1000)
```

### Data Types: Why Do We Need Them?

**The Problem:**
Memory is just a sequence of bytes (0s and 1s). How does the computer know if `01000001` means:

- The number 65?
- The letter 'A'?
- Part of a larger number?

**The Solution: Data Types**
Types tell the compiler:

1. **How much memory to allocate**
2. **How to interpret the bits**
3. **What operations are valid**

### Integer Types

| Type | Size | Range | Why Use It? |
|------|------|-------|-------------|
| `char` | 1 byte | -128 to 127 | Single characters, small numbers |
| `short` | 2 bytes | -32,768 to 32,767 | When you need to save memory |
| `int` | 4 bytes | -2,147,483,648 to 2,147,483,647 | Default choice for integers |
| `long` | 8 bytes | Very large numbers | Big data, timestamps, IDs |
| `long long` | 8 bytes | Guaranteed 64-bit | Portable large integers |

**unsigned variants:**

```c
unsigned int age = 25;  // Only positive: 0 to 4,294,967,295
```

**Why unsigned?**

- Doubles the positive range
- Use when negative values are impossible (age, count, array indices)
- Bit operations often use unsigned

**Common Pitfall:**

```c
unsigned int x = 0;
x = x - 1;  // Underflow! x is now 4,294,967,295 (wraps around)
```

### Floating-Point Types

| Type | Size | Precision | Why Use It? |
|------|------|-----------|-------------|
| `float` | 4 bytes | ~7 digits | Graphics, games (where speed > precision) |
| `double` | 8 bytes | ~15 digits | Scientific calculations, default choice |
| `long double` | 10-16 bytes | ~19 digits | Extreme precision needs |

**Why are floats "approximate"?**
Floats use IEEE 754 format — stores numbers in scientific notation:

```text
3.14159 = 3.14159 × 10^0
        = Sign × Mantissa × 2^Exponent
```

**Consequence:** Some numbers can't be represented exactly

```c
float x = 0.1 + 0.2;  // x might be 0.30000001, not exactly 0.3!
```

**When to use double vs float?**

- **Use double by default** — modern CPUs are optimized for it
- **Use float** when memory is critical (large arrays, embedded systems)
- **Never use float for money** — use integers (cents instead of dollars)

### Character Type

```c
char grade = 'A';  // Single quotes for characters!
```

**What's really stored?**

- ASCII code: 'A' = 65, 'B' = 66, etc.
- You can do arithmetic: `'A' + 1 = 'B'`

---

## 📦 Variable Declaration and Initialization

### Declaration vs Initialization

```c
int age;           // Declaration — reserves memory
age = 20;          // Initialization — stores value

int height = 175;  // Declaration + Initialization
```

**What happens in memory?**

```text
Declaration:
int age;
┌─────┐
│  ?  │  ← Garbage value (whatever was there before)
└─────┘

Initialization:
age = 20;
┌─────┐
│ 20  │  ← Known value
└─────┘
```

### The Danger of Uninitialized Variables

```c
int x;              // Declared but not initialized
printf("%d", x);    // UNDEFINED BEHAVIOR! Prints garbage
```

**Why is this dangerous?**

- May print 0, 42, -1573829, or crash
- Depends on what was previously in that memory location
- **Always initialize variables before use, or ensure they're assigned a value before being read!**

### Multiple Declarations

```c
int a, b, c;           // All uninitialized
int x = 1, y = 2, z;   // x=1, y=2, z is garbage!
```

**Best Practice:**

```c
int a = 0;  // One per line, always initialize
int b = 0;
int c = 0;
```

---

## 🔒 Constants

### Why Use Constants?

**Bad Code:**

```c
area = 3.14159 * radius * radius;
circumference = 2 * 3.14159 * radius;
volume = (4.0 / 3.0) * 3.14159 * radius * radius * radius;
// What if you type 3.14159 wrong somewhere?
```

**Good Code:**

```c
const double PI = 3.14159265359;
area = PI * radius * radius;
circumference = 2 * PI * radius;
volume = (4.0 / 3.0) * PI * radius * radius * radius;
```

### Two Ways to Define Constants

#### 1. Preprocessor Directive

```c
#define PI 3.14159
#define MAX_STUDENTS 100
```

**How it works:**

- Preprocessor literally replaces text before compilation
- `#define PI 3.14159` → Every `PI` becomes `3.14159`
- No type checking
- No memory allocated
- No semicolon!

**When to use:**

- Simple value substitutions
- Conditional compilation
- Macro functions

#### 2. Const Keyword

```c
const double PI = 3.14159265359;
const int MAX_STUDENTS = 100;
```

**How it works:**

- Creates a read-only variable
- Type-checked by compiler
- Takes memory space
- Can't be modified

**When to use:**

- Prefer this for modern C code
- When you need type safety
- When you need to pass by reference

### Comparison

| Feature | `#define` | `const` |
|---------|-----------|---------|
| Type checking | No | Yes |
| Debugger visibility | No | Yes |
| Memory usage | None | Yes (tiny) |
| Scope | Global | Block/function |
| Preferred? | Legacy code | Modern C |

---

## 🖥️ Input and Output

### Understanding Standard I/O

Programs interact with three streams:

- **stdin** (standard input) — keyboard by default
- **stdout** (standard output) — terminal/console
- **stderr** (standard error) — error messages

```text
Keyboard → stdin → Program → stdout → Screen
                            → stderr → Screen
```

### printf() Deep Dive

```c
printf("I am %d years old\n", age);
```

**How it works:**

1. Scans format string for `%` specifiers
2. Replaces them with corresponding arguments
3. Sends result to stdout

**Format Specifier Syntax:**

```text
%[flags][width][.precision][length]type
```

Examples:

```c
printf("%d", 42);        // Simple: 42
printf("%5d", 42);       // Width 5:    42
printf("%-5d", 42);      // Left-aligned: 42   
printf("%05d", 42);      // Zero-padded: 00042
printf("%.2f", 3.14159); // 2 decimals: 3.14
printf("%8.2f", 3.14);   // Width 8, 2 decimals:     3.14
```

### Common Format Specifiers

| Specifier | Type | Example Output |
|-----------|------|----------------|
| `%d` or `%i` | Signed int | -42 |
| `%u` | Unsigned int | 42 |
| `%f` | Float/double | 3.140000 |
| `%lf` | Double (scanf only!) | 3.140000 |
| `%c` | Char | A |
| `%s` | String | Hello |
| `%p` | Pointer address | 0x7ffe5467e044 |
| `%x` | Hex (lowercase) | 2a |
| `%X` | Hex (uppercase) | 2A |
| `%%` | Literal % | % |

### scanf() Deep Dive

```c
int age;
scanf("%d", &age);  // Note the &
```

**Why the `&` (address-of operator)?**

```text
Memory:
┌─────┐
│  ?  │  age lives at address 1000
└─────┘
   ↑
   1000

scanf needs to know WHERE to store input.
&age gives it the address: 1000
```

Without `&`:

```c
scanf("%d", age);  // WRONG! Passes value of age (garbage)
                   // scanf tries to write to random memory → CRASH
```

**Reading Multiple Values:**

```c
int day, month, year;
scanf("%d %d %d", &day, &month, &year);
// Input: 25 10 2025
```

**Reading Characters (Tricky!):**

```c
char ch;
scanf(" %c", &ch);  // Space before %c to skip whitespace!
```

**Why the space?**

- `scanf` leaves newline in buffer after previous input
- ` %c` tells it to skip whitespace first

### Common scanf() Pitfalls

**Problem 1: Leftover newlines**

```c
int num;
char ch;
scanf("%d", &num);   // User types: 5<Enter>
scanf("%c", &ch);    // Reads <Enter>, not next char!

// Solution:
scanf("%d", &num);
scanf(" %c", &ch);   // Space skips whitespace
```

**Problem 2: Buffer overflow**

```c
char name[50];
scanf("%s", name);  // Dangerous if input > 49 chars!

// Safer:
scanf("%49s", name);  // Limit to 49 chars (+ null terminator)
```

---

## ➕ Arithmetic Operators

### The Five Basic Operations

```c
int a = 10, b = 3;

printf("%d\n", a + b);  // 13
printf("%d\n", a - b);  // 7
printf("%d\n", a * b);  // 30
printf("%d\n", a / b);  // 3  ← Integer division!
printf("%d\n", a % b);  // 1  ← Remainder
```

### Integer Division: The Source of Many Bugs

**The Rule:** If both operands are integers, result is integer (truncated, not rounded).

```c
int result = 5 / 2;     // 2 (not 2.5!)
float result = 5 / 2;   // 2.0 (division happens first, then assigned)
float result = 5.0 / 2; // 2.5 (float division)
float result = (float)5 / 2;  // 2.5 (cast one operand)
```

**Why does this happen?**

- Efficiency: Integer division is faster than floating-point
- Historical: Matches how CPU arithmetic works
- Predictable: Same behavior across all C compilers

**Real-world bug example:**

```c
// Calculate average of exam scores
int score1 = 85, score2 = 90, score3 = 78;
int sum = score1 + score2 + score3;  // 253
float average = sum / 3;              // 84.0 (WRONG!)

// Correct:
float average = (float)sum / 3;       // 84.33
// Or:
float average = sum / 3.0;            // 84.33
```

### Modulus Operator (%)

**What it does:** Returns remainder after division

```c
10 % 3 = 1   // 10 ÷ 3 = 3 remainder 1
15 % 4 = 3   // 15 ÷ 4 = 3 remainder 3
20 % 5 = 0   // 20 ÷ 5 = 4 remainder 0
```

**Common Uses:**

1. **Check even/odd:**

```c
if (num % 2 == 0) {
    printf("Even");
} else {
    printf("Odd");
}
```

2. **Cycle through array:**

```c
index = (index + 1) % arraySize;  // Wraps around: 0,1,2,0,1,2...
```

3. **Extract digits:**

```c
int lastDigit = num % 10;     // 12345 → 5
num = num / 10;                // 12345 → 1234
```

4. **Check divisibility:**

```c
if (year % 4 == 0) {
    // Might be leap year...
}
```

**Important:** Modulus only works with integers!

```c
float x = 7.5 % 2.5;  // COMPILATION ERROR!
float x = fmod(7.5, 2.5);  // Use fmod() for floats
```

---

## 📝 Assignment Operators

### Basic Assignment

```c
int x = 10;  // Assigns 10 to x
```

### Compound Assignment Operators

Instead of:

```c
x = x + 5;
x = x - 3;
x = x * 2;
x = x / 4;
x = x % 3;
```

Write:

```c
x += 5;  // Same as x = x + 5
x -= 3;  // Same as x = x - 3
x *= 2;  // Same as x = x * 2
x /= 4;  // Same as x = x / 4
x %= 3;  // Same as x = x % 3
```

**Why use compound operators?**

1. **Shorter, more readable** — less typing
2. **Compiler optimization** — sometimes generates faster code
3. **Less error-prone** — can't accidentally use wrong variable

### Increment and Decrement

**Post-increment/decrement:**

```c
int x = 5;
int y = x++;  // y = 5, then x = 6 (use then increment)
```

**Pre-increment/decrement:**

```c
int x = 5;
int y = ++x;  // x = 6, then y = 6 (increment then use)
```

**Visualization:**

```c
// Post-increment (x++)
int x = 5;
int y = x++;
// Steps:
// 1. Evaluate x (5)
// 2. Assign to y (y = 5)
// 3. Increment x (x = 6)

// Pre-increment (++x)
int x = 5;
int y = ++x;
// Steps:
// 1. Increment x (x = 6)
// 2. Evaluate x (6)
// 3. Assign to y (y = 6)
```

**When does it matter?**

```c
int x = 5;
x++;        // Same as
++x;        // Same as
x += 1;     // Same as
x = x + 1;  // All produce x = 6

// Only matters in expressions:
arr[i++];   // Use i, then increment
arr[++i];   // Increment i, then use
```

**Best Practice:** Use standalone when possible to avoid confusion

```c
// Clear:
x++;
doSomething(x);

// Confusing:
doSomething(x++);  // Is x incremented before or after the call?
```

---

## 🎯 Operator Precedence

When you write:

```c
int result = 2 + 3 * 4;
```

Which happens first, addition or multiplication?

### Precedence Table (Simplified)

| Priority | Operators | Example |
|----------|-----------|---------|
| 1 (Highest) | `()` Parentheses | `(a + b)` |
| 2 | `++` `--` (prefix) | `++x` |
| 3 | `*` `/` `%` | `a * b` |
| 4 | `+` `-` | `a + b` |
| 5 (Lowest) | `=` `+=` `-=` etc. | `x = 5` |

### Examples

```c
2 + 3 * 4        // = 2 + 12 = 14 (not 20!)
(2 + 3) * 4      // = 5 * 4 = 20
10 / 2 * 3       // = 5 * 3 = 15 (left to right)
10 - 5 - 2       // = 5 - 2 = 3 (left to right)
```

**Why precedence exists:**

- Matches mathematical conventions (PEMDAS)
- Makes code less verbose (fewer parentheses needed)
- Standardized across programming languages

**Best Practice: When in doubt, use parentheses!**

```c
// Unclear:
result = a + b * c - d / e;

// Clear:
result = a + (b * c) - (d / e);
```

---

## 🔄 Type Casting

### Implicit vs Explicit Casting

**Implicit (Automatic):**

```c
int x = 5;
float y = x;  // Compiler automatically converts 5 to 5.0
```

**Explicit (Manual):**

```c
float x = 7.8;
int y = (int)x;  // You explicitly request conversion to int
```

### Type Conversion Rules

**Promotion Hierarchy:**

```text
char → int → long → float → double
```

**In mixed expressions:**

```c
int + float   → float
int + double  → double
float + double → double
```

Example:

```c
int a = 5;
float b = 2.5;
double result = a + b;  // a promoted to float, then to double
// result = 7.5
```

### Common Casting Scenarios

**1. Avoiding Integer Division:**

```c
int a = 5, b = 2;
float result = a / b;           // 2.0 (WRONG)
float result = (float)a / b;    // 2.5 (CORRECT)
float result = a / (float)b;    // 2.5 (CORRECT)
float result = (float)(a / b);  // 2.0 (TOO LATE!)
```

**2. Truncating Decimals:**

```c
float price = 19.99;
int dollars = (int)price;  // 19 (truncates, doesn't round!)

// To round:
int rounded = (int)(price + 0.5);  // 20
```

**3. Character-Number Conversion:**

```c
char letter = 'A';
int ascii = (int)letter;  // 65

int code = 65;
char letter = (char)code;  // 'A'
```

**4. Pointer Casting (Advanced):**

```c
void* ptr = malloc(100);
int* intPtr = (int*)ptr;  // Cast void pointer to int pointer
```

### Dangers of Casting

**Loss of Precision:**

```c
double pi = 3.14159;
int truncated = (int)pi;  // 3 (lost decimal part forever!)
```

**Overflow:**

```c
int large = 50000;
short small = (short)large;  // Might overflow! Undefined behavior
```

**Sign Issues:**

```c
int negative = -1;
unsigned int positive = (unsigned)negative;  // 4294967295 (wraps around!)
```

---

## 📐 Mathematical Functions

### Why We Need math.h

Basic operators (+, -, *, /, %) are limited. For complex math:

```c
#include <math.h>
```

**What math.h provides:**

- Trigonometry (sin, cos, tan)
- Powers and roots (pow, sqrt)
- Logarithms (log, log10)
- Rounding (ceil, floor, round)
- Constants (M_PI, M_E)

### Common Functions

#### Power and Root

```c
double result;
result = pow(2.0, 3.0);   // 8.0 (2³)
result = sqrt(16.0);      // 4.0 (√16)
result = cbrt(27.0);      // 3.0 (∛27)
```

**Why pass doubles?**

- Math functions work with doubles for precision
- Integers are automatically promoted

#### Rounding Functions

```c
double x = 4.7;
ceil(x);    // 5.0 (rounds up)
floor(x);   // 4.0 (rounds down)
round(x);   // 5.0 (rounds to nearest)
trunc(x);   // 4.0 (removes decimals)
```

**Use cases:**

- `ceil()`: Calculating number of pages, buckets needed
- `floor()`: Converting prices, array indices
- `round()`: Statistical rounding
- `trunc()`: Like (int) cast but returns double

#### Absolute Value

```c
int abs(int x);         // For integers
float fabs(float x);    // For floats
double fabs(double x);  // For doubles

int x = -42;
int positive = abs(x);  // 42

double y = -3.14;
double positive = fabs(y);  // 3.14
```

#### Trigonometry (Radians!)

```c
double angle_degrees = 45.0;
double angle_radians = angle_degrees * M_PI / 180.0;

double sine = sin(angle_radians);
double cosine = cos(angle_radians);
double tangent = tan(angle_radians);
```

**Common mistake:** Forgetting to convert degrees to radians!

```c
sin(45);  // WRONG! sin expects radians
sin(45 * M_PI / 180);  // CORRECT
```

### Compilation with math.h

**On Linux/Mac:**

```bash
gcc program.c -lm -o program
```

The `-lm` flag **links the math library**.

**Why is this needed?**

- Math functions are in a separate library (`libm.so` or `libm.a`)
- Linker needs to be told to include it
- On Windows (most IDEs), this happens automatically

**Without -lm:**

```
undefined reference to `sqrt'
undefined reference to `pow'
```

---

## 🧠 Putting It All Together

### A Complete Example: Quadratic Formula

```c
#include <stdio.h>
#include <math.h>

int main() {
    double a, b, c;
    double discriminant, root1, root2;
    
    // Input coefficients
    printf("Enter coefficients (a b c): ");
    scanf("%lf %lf %lf", &a, &b, &c);
    
    // Calculate discriminant
    discriminant = b * b - 4 * a * c;
    
    // Calculate roots (assuming real roots)
    root1 = (-b + sqrt(discriminant)) / (2 * a);
    root2 = (-b - sqrt(discriminant)) / (2 * a);
    
    // Output
    printf("Root 1: %.2f\n", root1);
    printf("Root 2: %.2f\n", root2);
    
    return 0;
}
```
---

## 🎓 Learning Strategies

### Understanding vs Memorizing

**Don't just memorize syntax — understand the concepts:**

❌ **Bad approach:** "I need to write `scanf("%d", &x)` because that's the rule"

✓ **Good approach:** "scanf needs the memory address where to store input, so I use &"

### The Three-Step Learning Process

1. **Read and Understand**
   - Why does this concept exist?
   - What problem does it solve?
   - How is it used in real programs?

2. **Experiment**
   - Modify example code
   - Try edge cases (what if input is 0? negative? huge?)
   - Break things intentionally and see what happens

3. **Apply**
   - Write programs from scratch
   - Solve problems without looking at examples
   - Explain concepts to others (teaching = learning)

### Common Beginner Mistakes and How to Avoid Them

#### 1. Forgetting Semicolons

```c
printf("Hello")  // Error: expected ';' before 'return'
return 0;
```

**Why it happens:** Coming from Python or other languages without semicolons  
**Solution:** Configure editor to highlight missing semicolons

#### 2. Missing & in scanf

```c
int age;
scanf("%d", age);  // Dangerous! Writes to random memory
```

**Why it happens:** Confusion about pointers  
**Solution:** Remember: scanf needs the **address**, not the value

#### 3. Integer Division Surprise

```c
float avg = 5 / 2;  // 2.0, not 2.5!
```

**Why it happens:** Not understanding type conversion timing  
**Solution:** Cast at least one operand `(float)5 / 2` or `5.0 / 2`

#### 4. Uninitialized Variables

```c
int x;
printf("%d", x);  // Undefined behavior!
```

**Why it happens:** Assuming variables default to 0  
**Solution:** Always initialize: `int x = 0;`

#### 5. Wrong Format Specifier

```c
float pi = 3.14;
printf("%d", pi);  // Garbage output!
```

**Why it happens:** Mixing up format codes  
**Solution:** Create a reference card:

- `%d` = int
- `%f` = float/double  
- `%c` = char
- `%s` = string

---

## 🔬 Debugging Techniques

### Using printf() for Debugging

**The simplest debugging tool:**

```c
printf("DEBUG: x = %d, y = %d\n", x, y);
```

**Track program flow:**

```c
printf("Before calculation\n");
result = complex_formula();
printf("After calculation: result = %f\n", result);
```

**Check variable values:**

```c
printf("a=%d b=%d c=%d\n", a, b, c);
calculation();
printf("After: a=%d b=%d c=%d\n", a, b, c);
```

### Understanding Compiler Errors

**Example error:**

```bash
error: expected ';' before 'return'
```

**How to read it:**

1. **Line number** — where error was detected (might be previous line!)
2. **Error type** — what went wrong
3. **Context** — surrounding code that helps locate issue

**Common pattern:**

```
program.c:10:5: error: 'x' undeclared
```

- `program.c` — file name
- `10` — line number
- `5` — column number
- `error:` — type of message
- Description — what's wrong

### Compiler Warning Flags

**Compile with warnings enabled:**

```bash
gcc -Wall -Wextra -Werror program.c
```

- `-Wall` — Enable all warnings
- `-Wextra` — Extra warnings
- `-Werror` — Treat warnings as errors

**Why this matters:**

```c
int x;
if (x = 5) {  // Warning: assignment in condition
    // ...
}
// Should be: if (x == 5)
```

Without warnings, this compiles but has a bug!

---

## 💡 Best Practices

### Code Style and Readability

#### 1. Meaningful Variable Names

```c
// Bad
int x, y, z;
float a, b, c;

// Good
int age, height, weight;
float price, tax, total;
```

#### 2. Consistent Indentation

```c
// Bad
int main() {
int x = 5;
if (x > 0) {
printf("Positive");
}
return 0;
}

// Good
int main() {
    int x = 5;
    if (x > 0) {
        printf("Positive");
    }
    return 0;
}
```

#### 3. One Statement Per Line

```c
// Bad
int x = 5; int y = 10; int z = x + y;

// Good
int x = 5;
int y = 10;
int z = x + y;
```

#### 4. Spaces Around Operators

```c
// Bad
x=5+3*2;

// Good
x = 5 + 3 * 2;
```

#### 5. Comments That Add Value

```c
// Bad
x = x + 1;  // Increment x

// Good
x++;  // Move to next student in array
```

### Program Structure

**Organize your code logically:**

```c
#include <stdio.h>
#include <math.h>

// Constants at the top
#define MAX_SIZE 100
const double PI = 3.14159265359;

int main() {
    // 1. Variable declarations
    int age;
    float height;
    
    // 2. Input
    printf("Enter age: ");
    scanf("%d", &age);
    
    // 3. Processing
    float yearsToRetirement = 65 - age;
    
    // 4. Output
    printf("Years to retirement: %.0f\n", yearsToRetirement);
    
    return 0;
}
```

### Testing Your Programs

**Test with different inputs:**

1. **Normal cases**
    - Typical expected values
    - Example: age = 25

2. **Edge cases**
    - Minimum/maximum valid values
    - Example: age = 0, age = 120

3. **Invalid inputs**
    - What if user enters negative number?
    - What if they enter text instead of number?

4. **Boundary values**
    - Just above/below limits
    - Example: age = 64, 65 (retirement age)

**Example test plan for average calculator:**

```bash
Test 1: scores = 85, 90, 78 → expected: 84.33
Test 2: scores = 100, 100, 100 → expected: 100.00
Test 3: scores = 0, 0, 0 → expected: 0.00
Test 4: scores = 33, 34, 33 → expected: 33.33
```

---

## 📚 Going Deeper

### Recommended Reading

**Books:**

- *The C Programming Language* by Kernighan & Ritchie
    - Written by C's creators
    - Concise and authoritative
  
- *C Programming: A Modern Approach* by K.N. King
    - More beginner-friendly
    - Excellent examples and exercises

**Online Resources:**

- [cppreference.com](https://en.cppreference.com/w/c) — Comprehensive reference
- [Learn-C.org](https://www.learn-c.org/) — Interactive tutorials
- [GeeksforGeeks C](https://www.geeksforgeeks.org/c-programming-language/) — Examples and explanations

## 📎 Appendix: Quick Reference

### Common Format Specifiers

```c
%d or %i    signed int
%u          unsigned int
%f          float/double (printf)
%lf         double (scanf)
%c          char
%s          string
%p          pointer
%x          hexadecimal
%%          literal %
```

### Arithmetic Operators

```c
+   addition
-   subtraction
*   multiplication
/   division (integer if both operands are int)
%   modulus (remainder)
```

### Assignment Operators

```c
=   simple assignment
+=  add and assign
-=  subtract and assign
*=  multiply and assign
/=  divide and assign
%=  modulus and assign
```

### Type Sizes (Typical)

```c
char        1 byte
short       2 bytes
int         4 bytes
long        4-8 bytes
float       4 bytes
double      8 bytes
```

### Math Functions (math.h)

```c
pow(x, y)   x raised to y
sqrt(x)     square root
ceil(x)     round up
floor(x)    round down
fabs(x)     absolute value
sin(x)      sine (radians)
cos(x)      cosine (radians)
```

### Compilation Commands

```bash
# Basic compilation
gcc program.c -o program

# With warnings
gcc -Wall -Wextra program.c -o program

# With math library
gcc program.c -lm -o program

# All together
gcc -Wall -Wextra program.c -lm -o program
```

---
