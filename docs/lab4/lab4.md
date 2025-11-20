# 📊 Lab 4: Arrays & Strings

---

## 🎯 Learning Objectives

By the end of this lab, you'll be able to:

**Arrays:**
✅ Declare and initialize arrays  
✅ Access and modify array elements  
✅ Process arrays using loops  
✅ Implement search and sort algorithms  
✅ Work with 2D arrays (matrices)  

**Strings:**
✅ Understand strings as character arrays  
✅ Use string library functions  
✅ Manipulate strings (copy, concatenate, compare)  
✅ Process strings character by character  

---

# Part 1: Arrays (Vectors)

## 💡 Why Arrays Matter

### The Problem Without Arrays

```c
int score1, score2, score3, score4, score5;
// ... 95 more variables for 100 students!

// Calculate average - impossible to scale!
float avg = (score1 + score2 + ... + score100) / 100;
```

**Problems:**

- Separate variable for each value
- Can't use loops
- Doesn't scale
- Unmaintainable

### The Solution: Arrays

```c
int scores[100];

int sum = 0;
for (int i = 0; i < 100; i++) {
    sum += scores[i];
}
float avg = sum / 100.0;
```

---

## 📦 What is an Array?

**Definition:** Collection of elements of the **same type**, stored in **contiguous memory**, accessed by **index**.

### Memory Layout

```bash
int arr[5] = {85, 92, 78, 95, 88};

Memory:
┌────┬────┬────┬────┬────┐
│ 85 │ 92 │ 78 │ 95 │ 88 │
└────┴────┴────┴────┴────┘
 [0]  [1]  [2]  [3]  [4]    ← indices

Address:
1000 1004 1008 1012 1016     ← each int takes 4 bytes
```

**Key Properties:**

- **Fixed size** — set at declaration
- **Same type** — all elements identical type
- **Contiguous** — stored consecutively in memory
- **Zero-indexed** — first element is index 0
- **Random access** — O(1) time to access any element

---

## 🔢 Array Declaration & Initialization

### Declaration

```c
type arrayName[size];
```

**Examples:**

```c
int numbers[10];      // 10 integers
float grades[5];      // 5 floats
char name[50];        // 50 characters
double prices[100];   // 100 doubles
```

### Initialization

**Method 1: Initialize all**

```c
int arr[5] = {10, 20, 30, 40, 50};
```

**Method 2: Partial (rest = 0)**

```c
int arr[5] = {10, 20};  // {10, 20, 0, 0, 0}
```

**Method 3: All zeros**

```c
int arr[5] = {0};  // All elements 0
```

**Method 4: Inferred size**

```c
int arr[] = {10, 20, 30};  // Size is 3
```

**Method 5: After declaration**

```c
int arr[3];
arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
```

---

## 🎯 Accessing Array Elements

### Indexing

```c
int arr[5] = {10, 20, 30, 40, 50};

// Read
int first = arr[0];   // 10
int third = arr[2];   // 30
int last = arr[4];    // 50

// Write
arr[0] = 100;         // arr = {100, 20, 30, 40, 50}
arr[2] = arr[1] + 5;  // arr = {100, 20, 25, 40, 50}
```

### ⚠️ Array Bounds

**C does NOT check array bounds!**

```c
int arr[5];
arr[10] = 100;  // OUT OF BOUNDS! Undefined behavior!
                // May crash, corrupt data, or appear to work
```

**Always ensure:** `0 <= index < size`

---

## 🔄 Processing Arrays with Loops

### Pattern 1: Traversal (Visit Each Element)

```c
int arr[5] = {10, 20, 30, 40, 50};

// Forward
for (int i = 0; i < 5; i++) {
    printf("%d ", arr[i]);
}

// Backward
for (int i = 4; i >= 0; i--) {
    printf("%d ", arr[i]);
}
```

### Pattern 2: Input Array

```c
int arr[5];
printf("Enter 5 numbers:\n");
for (int i = 0; i < 5; i++) {
    scanf("%d", &arr[i]);
}
```

### Pattern 3: Sum and Average

```c
int sum = 0;
for (int i = 0; i < 5; i++) {
    sum += arr[i];
}
float average = sum / 5.0;
```

### Pattern 4: Find Min/Max

```c
int arr[5] = {45, 23, 67, 12, 89};
int max = arr[0];  // Initialize with first

for (int i = 1; i < 5; i++) {
    if (arr[i] > max) {
        max = arr[i];
    }
}
```

---

## 🔍 Common Array Operations

### 1. Linear Search

Find if element exists and return position.

```c
int linearSearch(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i;  // Found at index i
        }
    }
    return -1;  // Not found
}
```

**Time complexity:** O(n)

### 2. Count Occurrences

```c
int count = 0;
for (int i = 0; i < size; i++) {
    if (arr[i] == target) {
        count++;
    }
}
```

### 3. Reverse Array

```c
void reverse(int arr[], int size) {
    for (int i = 0; i < size / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[size - 1 - i];
        arr[size - 1 - i] = temp;
    }
}
```

### 4. Copy Array

```c
void copyArray(int source[], int dest[], int size) {
    for (int i = 0; i < size; i++) {
        dest[i] = source[i];
    }
}
```

### 5. Remove Duplicates

```c
int removeDuplicates(int arr[], int size) {
    int newSize = 0;
    for (int i = 0; i < size; i++) {
        int isDuplicate = 0;
        for (int j = 0; j < newSize; j++) {
            if (arr[i] == arr[j]) {
                isDuplicate = 1;
                break;
            }
        }
        if (!isDuplicate) {
            arr[newSize++] = arr[i];
        }
    }
    return newSize;
}
```

---

## 📈 Sorting Algorithms

### Bubble Sort

Compare adjacent elements and swap if needed.

```c
void bubbleSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        for (int j = 0; j < size - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```

**How it works:**
```bash
Pass 1: {5,2,8,1,9} → {2,5,1,8,9} (9 bubbles to end)
Pass 2: {2,5,1,8,9} → {2,1,5,8,9} (8 in place)
Pass 3: {2,1,5,8,9} → {1,2,5,8,9} (5 in place)
Done: {1,2,5,8,9}
```

**Time complexity:** O(n²)

### Selection Sort

Find minimum and place at front.

```c
void selectionSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < size; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        // Swap arr[i] with arr[minIndex]
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
}
```

**Time complexity:** O(n²)

---

## 📊 Two-Dimensional Arrays (Matrices)

### Declaration

```c
int matrix[3][4];  // 3 rows, 4 columns
```

### Memory Layout

```bash
int matrix[2][3] = {{1,2,3}, {4,5,6}};

Logical view:
  Col0 Col1 Col2
Row0:  1    2    3
Row1:  4    5    6

Memory (contiguous):
[1][2][3][4][5][6]
```

### Initialization

```c
// Method 1: Row by row
int matrix[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};

// Method 2: Flat (same result)
int matrix[2][3] = {1, 2, 3, 4, 5, 6};

// Method 3: Partial
int matrix[2][3] = {{1, 2}, {4}};  // Rest are 0
```

### Accessing Elements

```c
int matrix[2][3] = {{1,2,3}, {4,5,6}};

int element = matrix[1][2];  // 6 (row 1, col 2)
matrix[0][1] = 10;           // Change to 10
```

### Processing with Nested Loops

**Print matrix:**

```c
for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
        printf("%3d", matrix[i][j]);
    }
    printf("\n");
}
```

**Sum all elements:**

```c
int sum = 0;
for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
        sum += matrix[i][j];
    }
}
```

**Transpose:**

```c
int transpose[cols][rows];
for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
        transpose[j][i] = matrix[i][j];
    }
}
```

---

## 🔧 Arrays and Functions

### Passing Arrays to Functions

```c
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};
    printArray(numbers, 5);
    return 0;
}
```

**Important:** Arrays are passed by reference (pointer), not by value!

- Changes inside function affect original array
- Must pass size separately

### Example: Modifying Array

```c
void doubleValues(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        arr[i] *= 2;
    }
}

int main() {
    int arr[3] = {1, 2, 3};
    doubleValues(arr, 3);
    // arr is now {2, 4, 6}
}
```

---

## ⚠️ Common Array Mistakes

### 1. Out of Bounds Access

```c
int arr[5];
arr[5] = 10;  // ERROR! Valid indices: 0-4
arr[-1] = 5;  // ERROR! Negative index
```

### 2. Forgetting Array Size

```c
void process(int arr[]) {
    // No way to know size inside function!
    // Always pass size as parameter
}
```

### 3. Comparing Arrays with ==

```c
int arr1[3] = {1, 2, 3};
int arr2[3] = {1, 2, 3};

if (arr1 == arr2) {  // WRONG! Compares addresses
    // ...
}

// Correct: Compare element by element
int equal = 1;
for (int i = 0; i < 3; i++) {
    if (arr1[i] != arr2[i]) {
        equal = 0;
        break;
    }
}
```

### 4. Returning Local Array

```c
int* createArray() {
    int arr[5] = {1, 2, 3, 4, 5};
    return arr;  // DANGER! Returns pointer to local variable
}
// arr is destroyed when function returns!
```

---

# Part 2: Strings

---

## 📝 What Are Strings in C?

### String Definition

In C, a **string** is an **array of characters** terminated by the **null character** `'\0'`.

```c
char name[] = "Hello";

Memory:
┌───┬───┬───┬───┬───┬───┐
│ H │ e │ l │ l │ o │ \0│
└───┴───┴───┴───┴───┴───┘
 [0] [1] [2] [3] [4] [5]
```

**Key point:** `'\0'` marks the end of the string!

### Why Null Terminator?

Functions need to know where string ends:
```c
// Without \0, how would printf know when to stop?
printf("%s", name);  // Prints until \0 is found
```

---

## 🔤 String Declaration & Initialization

### Method 1: String Literal

```c
char name[] = "Alice";
// Automatically adds \0
// Size is 6: 'A','l','i','c','e','\0'
```

### Method 2: Character Array

```c
char name[] = {'A', 'l', 'i', 'c', 'e', '\0'};
// Must add \0 manually!
```

### Method 3: Specify Size

```c
char name[50] = "Alice";
// Size 50, but only first 6 used
// Rest are \0
```

### Method 4: Character Pointer

```c
char *name = "Alice";
// String literal (read-only!)
// Cannot modify: name[0] = 'B'; // ERROR!
```

---

## 📥 String Input/Output

### Output with printf

```c
char name[] = "Alice";
printf("%s\n", name);        // Alice
printf("Hello, %s!\n", name); // Hello, Alice!
```

### Input with scanf

```c
char name[50];
scanf("%s", name);  // No & needed! (array name is address)
```

**⚠️ Problem:** Stops at whitespace!

```bash
Input: "John Doe"
Result: name = "John" (stops at space!)
```

### Input with fgets (Better)

```c
char name[50];
fgets(name, 50, stdin);  // Reads entire line
// Includes newline \n at end!

// Remove newline:
name[strcspn(name, "\n")] = '\0';
```

### Input with scanf for whole line

```c
char name[50];
scanf("%[^\n]", name);  // Read until newline
// But leaves \n in buffer!
```

---

## 📚 String Library Functions

Include: `#include <string.h>`

### 1. strlen() - String Length

Returns length **without** `'\0'`.

```c
char str[] = "Hello";
int len = strlen(str);  // 5 (not 6!)
```

### 2. strcpy() - String Copy

```c
char source[] = "Hello";
char dest[20];

strcpy(dest, source);  // dest = "Hello"
```

**⚠️ Danger:** No bounds checking!

```c
char dest[5];
strcpy(dest, "Hello World");  // BUFFER OVERFLOW!
```

**Safer:** `strncpy()`

```c
strncpy(dest, source, sizeof(dest) - 1);
dest[sizeof(dest) - 1] = '\0';  // Ensure null termination
```

### 3. strcat() - String Concatenation

```c
char str1[50] = "Hello";
char str2[] = " World";

strcat(str1, str2);  // str1 = "Hello World"
```

**⚠️ Requirements:**

- str1 must have enough space!
- Both must be null-terminated

**Safer:** `strncat()`

### 4. strcmp() - String Comparison

```c
char str1[] = "Apple";
char str2[] = "Banana";

int result = strcmp(str1, str2);
// result < 0 if str1 < str2 (Apple < Banana)
// result = 0 if str1 == str2
// result > 0 if str1 > str2
```

**⚠️ Never use ==**

```c
if (str1 == str2)  // WRONG! Compares addresses
if (strcmp(str1, str2) == 0)  // CORRECT!
```

### 5. strchr() - Find Character

```c
char str[] = "Hello World";
char *ptr = strchr(str, 'o');  // Points to first 'o'

if (ptr != NULL) {
    printf("Found at position: %ld\n", ptr - str);  // 4
}
```

### 6. strstr() - Find Substring

```c
char str[] = "Hello World";
char *ptr = strstr(str, "World");

if (ptr != NULL) {
    printf("Found: %s\n", ptr);  // "World"
}
```

---

## 🔧 Manual String Operations

### 1. Manual strlen

```c
int my_strlen(char str[]) {
    int len = 0;
    while (str[len] != '\0') {
        len++;
    }
    return len;
}
```

### 2. Manual strcpy

```c
void my_strcpy(char dest[], char source[]) {
    int i = 0;
    while (source[i] != '\0') {
        dest[i] = source[i];
        i++;
    }
    dest[i] = '\0';  // Don't forget!
}
```

### 3. Manual strcmp

```c
int my_strcmp(char str1[], char str2[]) {
    int i = 0;
    while (str1[i] != '\0' && str2[i] != '\0') {
        if (str1[i] != str2[i]) {
            return str1[i] - str2[i];
        }
        i++;
    }
    return str1[i] - str2[i];
}
```

### 4. Manual strcat

```c
void my_strcat(char dest[], char source[]) {
    int i = 0, j = 0;
    
    // Find end of dest
    while (dest[i] != '\0') {
        i++;
    }
    
    // Copy source to end
    while (source[j] != '\0') {
        dest[i] = source[j];
        i++;
        j++;
    }
    
    dest[i] = '\0';
}
```

---

## 🔍 String Processing

### 1. Count Vowels

```c
int countVowels(char str[]) {
    int count = 0;
    for (int i = 0; str[i] != '\0'; i++) {
        char c = tolower(str[i]);
        if (c=='a' || c=='e' || c=='i' || c=='o' || c=='u') {
            count++;
        }
    }
    return count;
}
```

### 2. Reverse String

```c
void reverse(char str[]) {
    int len = strlen(str);
    for (int i = 0; i < len / 2; i++) {
        char temp = str[i];
        str[i] = str[len - 1 - i];
        str[len - 1 - i] = temp;
    }
}
```

### 3. Check Palindrome

```c
int isPalindrome(char str[]) {
    int len = strlen(str);
    for (int i = 0; i < len / 2; i++) {
        if (str[i] != str[len - 1 - i]) {
            return 0;  // Not palindrome
        }
    }
    return 1;  // Is palindrome
}
```

### 4. Count Words

```c
int countWords(char str[]) {
    int count = 0;
    int inWord = 0;
    
    for (int i = 0; str[i] != '\0'; i++) {
        if (str[i] != ' ' && !inWord) {
            count++;
            inWord = 1;
        } else if (str[i] == ' ') {
            inWord = 0;
        }
    }
    return count;
}
```

### 5. Convert to Uppercase

```c
void toUpper(char str[]) {
    for (int i = 0; str[i] != '\0'; i++) {
        if (str[i] >= 'a' && str[i] <= 'z') {
            str[i] = str[i] - 32;  // or use toupper()
        }
    }
}
```

---

## 🔤 Character Functions

Include: `#include <ctype.h>`

```c
isalpha(c)   // Is letter?
isdigit(c)   // Is digit?
isalnum(c)   // Is letter or digit?
isspace(c)   // Is whitespace?
isupper(c)   // Is uppercase?
islower(c)   // Is lowercase?

toupper(c)   // Convert to uppercase
tolower(c)   // Convert to lowercase
```

**Example:**

```c
char str[] = "Hello123";
for (int i = 0; str[i] != '\0'; i++) {
    if (isalpha(str[i])) {
        printf("%c is a letter\n", str[i]);
    } else if (isdigit(str[i])) {
        printf("%c is a digit\n", str[i]);
    }
}
```

---

## 📊 Array of Strings

### Declaration

```c
char names[3][20] = {
    "Alice",
    "Bob",
    "Charlie"
};
```

**Memory:** 3 rows × 20 columns

### Processing

```c
for (int i = 0; i < 3; i++) {
    printf("%s\n", names[i]);
}
```

### Sorting Strings

```c
void sortStrings(char arr[][20], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (strcmp(arr[j], arr[j+1]) > 0) {
                char temp[20];
                strcpy(temp, arr[j]);
                strcpy(arr[j], arr[j+1]);
                strcpy(arr[j+1], temp);
            }
        }
    }
}
```

---

## ⚠️ Common String Mistakes

### 1. Missing Null Terminator

```c
char str[5] = {'H', 'e', 'l', 'l', 'o'};  // No \0!
printf("%s\n", str);  // Undefined! Keeps reading memory
```

### 2. Buffer Overflow

```c
char str[5];
strcpy(str, "Hello World");  // OVERFLOW! Need 12 bytes
```

### 3. Comparing with ==

```c
char str1[] = "Hello";
char str2[] = "Hello";

if (str1 == str2)  // WRONG! Compares addresses
if (strcmp(str1, str2) == 0)  // CORRECT!
```

### 4. Modifying String Literals

```c
char *str = "Hello";
str[0] = 'h';  // CRASH! String literal is read-only
```

### 5. Not Passing Size

```c
void process(char str[]) {
    // How big is str? Unknown!
    // Can use strlen(), but safer to pass max size
}
```

---

## 📚 Summary

### Arrays

- Collection of same-type elements
- Fixed size, zero-indexed
- Use loops for processing
- Passed by reference to functions
- Common operations: search, sort, min/max

### Strings

- Character arrays ending with '\0'
- Use string.h functions
- Always null-terminate!
- Watch for buffer overflows
- Can process char-by-char with loops

### Key Takeaways

1. Arrays enable processing collections efficiently
2. Strings are special arrays of characters
3. Always check bounds
4. Use library functions when available
5. Understand manual implementations
6. Test with various inputs
