# 🔧 Lab 5: Functions and Procedures

---

## 🎯 Learning Objectives

By the end of this lab, you'll be able to:

✅ Understand why functions are essential  
✅ Declare and define functions  
✅ Use parameters and return values  
✅ Pass by value vs pass by reference  
✅ Work with arrays and functions  
✅ Apply recursion concepts  
✅ Design modular, reusable code  

---

## 💡 Why Functions Matter

### The Problem: Repetitive Code

**Without functions:**

```c
// Calculate area of circle 1
float area1 = 3.14159 * radius1 * radius1;

// Calculate area of circle 2
float area2 = 3.14159 * radius2 * radius2;

// Calculate area of circle 3
float area3 = 3.14159 * radius3 * radius3;

// ... repeated 100 times!
```

**Problems:**

- Repetitive code
- Hard to maintain (change formula everywhere)
- Error-prone (typo in one place)
- Difficult to test
- Not scalable

### The Solution: Functions

```c
float circleArea(float radius) {
    return 3.14159 * radius * radius;
}

// Use it
float area1 = circleArea(radius1);
float area2 = circleArea(radius2);
float area3 = circleArea(radius3);
```

**Benefits:**

- ✅ Write once, use many times
- ✅ Change in one place
- ✅ Easy to test
- ✅ Readable code
- ✅ Reusable across projects

---

## 🏗️ What is a Function?

### Definition

A **function** is a self-contained block of code that:

1. Has a name
2. Can receive inputs (parameters)
3. Performs a specific task
4. Can return a result

### Anatomy of a Function

```c
returnType functionName(parameterType1 param1, parameterType2 param2) {
    // Function body
    // Statements
    return value;  // Optional
}
```

**Parts:**

- **Return type** — What type of value it returns (or void for none)
- **Function name** — Identifier to call it
- **Parameters** — Input values (optional)
- **Function body** — Code to execute
- **Return statement** — Value to send back (if not void)

---

## 📝 Function Declaration vs Definition

### Declaration (Prototype)

Tells compiler function exists:
c
float circleArea(float radius);  // Declaration only

**Where:** Usually at top of file or in header (.h)

### Definition

Actual implementation:

```c
float circleArea(float radius) {  // Definition
    return 3.14159 * radius * radius;
}
```

**Where:** Can be anywhere after declaration

### Complete Example

```c
#include <stdio.h>

// Declaration (prototype)
int add(int a, int b);

int main() {
    int result = add(5, 3);
    printf("Result: %d\n", result);
    return 0;
}

// Definition
int add(int a, int b) {
    return a + b;
}
```

**Why separate?** Allows functions to call each other regardless of order!

---

## 🔄 Types of Functions

### 1. Functions with Return Value

```c
int square(int x) {
    return x * x;
}

// Usage
int result = square(5);  // result = 25
```

### 2. Void Functions (Procedures)

```c
void printMessage(char message[]) {
    printf("%s\n", message);
    // No return statement
}

// Usage
printMessage("Hello!");  // Prints, returns nothing
```

### 3. Functions with No Parameters

```c
int getRandomNumber() {
    return 42;  // Always returns 42 (joke!)
}

// Usage
int num = getRandomNumber();
### 4. Functions with Multiple Parameters

int max(int a, int b, int c) {
    int maximum = a;
    if (b > maximum) maximum = b;
    if (c > maximum) maximum = c;
    return maximum;
}

// Usage
int largest = max(10, 25, 18);  // 25
---
```

## 📊 Parameters and Arguments

### Terminology

**Parameters:** Variables in function definition (formal parameters)
```c
int add(int x, int y) {  // x and y are parameters
    return x + y;
}
```

**Arguments:** Actual values passed when calling (actual parameters)
```c
int result = add(5, 3);  // 5 and 3 are arguments
```

### Parameter Passing

**When function is called:**
1. Arguments are evaluated
2. Values copied to parameters
3. Function executes with parameter values
4. Function returns (parameters destroyed)
```c
int main() {
    int a = 5, b = 3;
    int sum = add(a, b);  // a and b copied to parameters
    // a and b unchanged in main
}
```
---

## 🔀 Pass by Value

### Default in C

**All basic types passed by value** — function receives a copy.

```c
void increment(int x) {
    x = x + 1;
    printf("Inside function: %d\n", x);  // 6
}

int main() {
    int num = 5;
    increment(num);
    printf("In main: %d\n", num);  // Still 5!
    return 0;
}
```

**What happens:**
1. num (5) is copied to parameter x
2. x is incremented to 6 (copy modified)
3. Function ends, x destroyed
4. num in main unchanged

### Visualization

main():                increment():
┌──────┐              ┌──────┐
│ num  │   copy →     │  x   │
│  5   │              │  6   │
└──────┘              └──────┘
                      ← destroyed after function
---

## 📮 Pass by Reference (Using Pointers)

### Modifying Original Variables

**Use pointers to pass address:**

```c
void increment(int *x) {  // Pointer parameter
    *x = *x + 1;  // Modify value at address
}

int main() {
    int num = 5;
    increment(&num);  // Pass address
    printf("%d\n", num);  // 6 (modified!)
    return 0;
}
```

**What happens:**
1. Address of num passed to function
2. Function accesses original num via pointer
3. Modifies original value
4. Change persists after function

### Visualization

main():
┌──────┐
│ num  │  ← increment() modifies this directly
│  6   │     via pointer
└──────┘
### When to Use

**Pass by value** (default):
- Function doesn't need to modify original
- Small data (int, float, char)
- Want to protect original

**Pass by reference** (pointers):
- Function needs to modify original
- Large data (avoid copying)
- Multiple return values needed

---

## 📦 Arrays and Functions

### Arrays Always Passed by Reference

**Arrays are automatically passed as pointers!**

```c
void modifyArray(int arr[], int size) {
    arr[0] = 100;  // Modifies original!
}

int main() {
    int numbers[5] = {1, 2, 3, 4, 5};
    modifyArray(numbers, 5);
    printf("%d\n", numbers[0]);  // 100 (changed!)
    return 0;
}
```

**Why?** Array name is actually a pointer to first element.

### Must Pass Size Separately

```c
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
}

int main() {
    int nums[5] = {10, 20, 30, 40, 50};
    printArray(nums, 5);  // Must pass size!
    return 0;
}
```

**Why?** Function doesn't know array size automatically.

---

## 🌳 Scope and Lifetime

### Variable Scope

**Local variables:** Only accessible within function

```c
void func() {
    int x = 10;  // Local to func
    // x only exists here
}

int main() {
    // Cannot access x from func
}
```

**Global variables:** Accessible everywhere (avoid when possible)

```c
int globalVar = 100;  // Global

void func() {
    printf("%d", globalVar);  // Can access
}

int main() {
    printf("%d", globalVar);  // Can access
}
```

### Variable Lifetime

**Automatic (local):** Created when function called, destroyed when function returns

```c
void func() {
    int x = 10;  // Created
    // ...
}  // x destroyed here
```

**Static:** Persists between function calls


```c
void counter() {
    static int count = 0;  // Initialized once
    count++;
    printf("%d ", count);
}

int main() {
    counter();  // 1
    counter();  // 2
    counter();  // 3
    return 0;
}
```

---

## 🎨 Function Design Principles

### 1. Single Responsibility

**Bad:** Function does too much

```c
void processStudent() {
    // Read input
    // Calculate average
    // Assign grade
    // Print report
    // Save to file
    // Send email
    // Too much!
}
```

**Good:** Each function has one job

```c
float calculateAverage(int scores[], int size);
char assignGrade(float average);
void printReport(Student s);
void saveToFile(Student s);
```

### 2. Meaningful Names

**Bad:**
```c
int calc(int a, int b);  // Calc what?
void process(int x);      // Process how?
```

**Good:**

```c
int calculateArea(int width, int height);
void validateInput(int userAge);
```

### 3. Keep Functions Short

**Rule of thumb:** If function doesn't fit on one screen, consider splitting.

### 4. Avoid Side Effects

**Bad:** Modifies global state unexpectedly

```c
int total = 0;  // Global

int add(int a, int b) {
    total += a + b;  // Side effect!
    return a + b;
}
```

**Good:** Pure function (no side effects)

```c
int add(int a, int b) {
    return a + b;  // Only returns result
}
```

---

## 🔧 Common Function Patterns

### Pattern 1: Validation Functions

```c
int isValidAge(int age) {
    return (age >= 0 && age <= 120);
}

int isLeapYear(int year) {
    return (year % 4 == 0 && year % 100 != 0) || 
           (year % 400 == 0);
}
```

**Returns:** 1 (true) or 0 (false)

### Pattern 2: Conversion Functions

```c
float celsiusToFahrenheit(float celsius) {
    return (celsius * 9.0 / 5.0) + 32.0;
}

int stringToInt(char str[]) {
    // Convert string to integer
}
```

### Pattern 3: Calculation Functions

```c
float calculateBMI(float weight, float height) {
    return weight / (height * height);
}

float calculateCompoundInterest(float principal, 
                                 float rate, 
                                 int years) {
    return principal * pow(1 + rate, years);
}
```

### Pattern 4: Search/Find Functions

```c
int findMax(int arr[], int size) {
    int max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}

int linearSearch(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i;  // Return index
        }
    }
    return -1;  // Not found
}
```

---

## 🚨 Common Mistakes

### 1. Missing Return Statement

```c
int square(int x) {
    int result = x * x;
    // Forgot return!
}  // Undefined behavior
```


**Fix:**

```c
int square(int x) {
    return x * x;
}
```

### 2. Wrong Return Type

```c
int divide(int a, int b) {
    return a / b;  // Integer division!
}

divide(5, 2);  // Returns 2, not 2.5
```

**Fix:**

```c
float divide(int a, int b) {
    return (float)a / b;  // 2.5
}
```

### 3. Modifying Array Without Intent

```c
void printArray(int arr[], int size) {
    arr[0] = 999;  // Oops! Modified original
    // ...
}
```

**Fix:** Use const if read-only

```c
void printArray(const int arr[], int size) {
    // arr[0] = 999;  // Compiler error!
    // ...
}
```

### 4. Infinite Recursion

```c
int bad(int n) {
    return n + bad(n - 1);  // No base case!
}
```

**Fix:** Always have base case

```c
int good(int n) {
    if (n == 0) return 0;  // Base case
    return n + good(n - 1);
}
```

### 5. Not Passing Size for Arrays

```c
void process(int arr[]) {
    // How many elements? Unknown!
}
```

**Fix:**

```c
void process(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        // ...
    }
}
```

---

## 📚 Standard Library Functions

### Already Available in C

**stdio.h:**

```c
printf()  // Output
scanf()   // Input
fgets()   // Read line
```

**math.h:**

```c
sqrt()    // Square root
pow()     // Power
sin()     // Sine
cos()     // Cosine
abs()     // Absolute value
```

**string.h:**

```c
strlen()  // String length
strcpy()  // String copy
strcmp()  // String compare
strcat()  // String concatenate
```

**ctype.h:**

```c
isalpha() // Is letter?
isdigit() // Is digit?
toupper() // To uppercase
tolower() // To lowercase
```

**stdlib.h:**

```c
rand()    // Random number
srand()   // Seed random
atoi()    // String to int
malloc()  // Allocate memory
free()    // Free memory
```

---

## 🎯 Modular Programming

### Breaking Programs into Functions

**Bad: Monolithic main()**

```c
int main() {
    // 200 lines of code
    // Everything in main
    // Hard to understand
    // Hard to test
    // Hard to reuse
}
```
**Good: Modular**

```c
void displayMenu();
int getUserChoice();
void processChoice(int choice);
void displayResults();

int main() {
    displayMenu();
    int choice = getUserChoice();
    processChoice(choice);
    displayResults();
    return 0;
}
```

**Benefits:**

- Each function small and focused
- Easy to test individually
- Easy to understand
- Reusable components

---

## 🔍 Debugging Functions

### Strategies

**1. Add Debug Prints**

```c
int factorial(int n) {
    printf("DEBUG: factorial(%d) called\n", n);

    if (n <= 1) {
        printf("DEBUG: returning 1\n");
        return 1;
    }

    int result = n * factorial(n - 1);
    printf("DEBUG: factorial(%d) = %d\n", n, result);
    return result;
}
```

**2. Test with Simple Inputs**

```c
// Test edge cases
factorial(0);   // Should return 1
factorial(1);   // Should return 1
factorial(5);   // Should return 120
```

**3. Verify Parameters**

```c
float divide(float a, float b) {
    if (b == 0) {
        printf("ERROR: Division by zero!\n");
        return 0;
    }
    return a / b;
}
```
---

## 📝 Summary

### Key Concepts

**Functions encapsulate reusable code**
Write once, use many times
Easier to maintain and test

**Pass by value vs pass by reference**
Value: Copy of data (default)
Reference: Via pointers (for modification)

**Arrays always passed by reference**
Array name is pointer
Always pass size separately

**Recursion = function calling itself**
Must have base case
Useful for tree/graph problems

**Good design principles**
Single responsibility
Meaningful names
Keep functions short
Avoid side effects

**Scope and lifetime**
Local variables destroyed after function
Static variables persist
Minimize global variables