# 🔧 Lab 5 Exercises: Functions and Procedures

## Exercise 1: Simple Calculator ⭐

Write four functions to perform basic arithmetic operations:

```c
int add(int a, int b);
int subtract(int a, int b);
int multiply(int a, int b);
float divide(int a, int b);
```

**Requirements:**

- Each function takes two integers
- `divide` should return a float and handle division by zero
- Test all functions in `main()`

**Expected Output:**

```bash
5 + 3 = 8
5 - 3 = 2
5 * 3 = 15
5 / 3 = 1.67
5 / 0 = Error: Division by zero
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

// Function declarations
int add(int a, int b);
int subtract(int a, int b);
int multiply(int a, int b);
float divide(int a, int b);

int main() {
    int x = 5, y = 3;
    
    printf("%d + %d = %d\n", x, y, add(x, y));
    printf("%d - %d = %d\n", x, y, subtract(x, y));
    printf("%d * %d = %d\n", x, y, multiply(x, y));
    printf("%d / %d = %.2f\n", x, y, divide(x, y));
    printf("%d / 0 = ", x);
    divide(x, 0);
    
    return 0;
}

// Function definitions
int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int multiply(int a, int b) {
    return a * b;
}

float divide(int a, int b) {
    if (b == 0) {
        printf("Error: Division by zero\n");
        return 0;
    }
    return (float)a / b;
}
```

</details>

---

## Exercise 2: Prime Number Checker ⭐⭐

Write a function to check if a number is prime:

```c
int isPrime(int n);  // Returns 1 if prime, 0 otherwise
```

**Requirements:**

- Check divisibility from 2 to √n
- Handle edge cases: n < 2 (not prime)
- Test with: 1, 2, 7, 15, 17, 100

**Expected Output:**

```bash
1 is not prime
2 is prime
7 is prime
15 is not prime
17 is prime
100 is not prime
```

<details><summary>Solution</summary>

```c
#include <stdio.h>
#include <math.h>

int isPrime(int n);

int main() {
    int numbers[] = {1, 2, 7, 15, 17, 100};
    int size = 6;
    
    for (int i = 0; i < size; i++) {
        if (isPrime(numbers[i])) {
            printf("%d is prime\n", numbers[i]);
        } else {
            printf("%d is not prime\n", numbers[i]);
        }
    }
    
    return 0;
}

int isPrime(int n) {
    // Numbers less than 2 are not prime
    if (n < 2) {
        return 0;
    }
    
    // 2 is prime
    if (n == 2) {
        return 1;
    }
    
    // Even numbers are not prime
    if (n % 2 == 0) {
        return 0;
    }
    
    // Check odd divisors up to sqrt(n)
    int limit = (int)sqrt(n);
    for (int i = 3; i <= limit; i += 2) {
        if (n % i == 0) {
            return 0;
        }
    }
    
    return 1;
}
```

</details>

---

## Exercise 3: Temperature Converter ⭐

Write two conversion functions:

```c
float celsiusToFahrenheit(float celsius);
float fahrenheitToCelsius(float fahrenheit);
```

**Formulas:**

- F = (C × 9/5) + 32
- C = (F - 32) × 5/9

**Requirements:**

- Test with: 0°C, 100°C, 32°F, 212°F

**Expected Output:**

```bash
0°C = 32.00°F
100°C = 212.00°F
32°F = 0.00°C
212°F = 100.00°C
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

float celsiusToFahrenheit(float celsius);
float fahrenheitToCelsius(float fahrenheit);

int main() {
    float c1 = 0, c2 = 100;
    float f1 = 32, f2 = 212;
    
    printf("%.0f°C = %.2f°F\n", c1, celsiusToFahrenheit(c1));
    printf("%.0f°C = %.2f°F\n", c2, celsiusToFahrenheit(c2));
    printf("%.0f°F = %.2f°C\n", f1, fahrenheitToCelsius(f1));
    printf("%.0f°F = %.2f°C\n", f2, fahrenheitToCelsius(f2));
    
    return 0;
}

float celsiusToFahrenheit(float celsius) {
    return (celsius * 9.0 / 5.0) + 32.0;
}

float fahrenheitToCelsius(float fahrenheit) {
    return (fahrenheit - 32.0) * 5.0 / 9.0;
}
```

</details>
---

## Exercise 4: Array Reversal ⭐⭐

Write a function to reverse an array in place:

```c
void reverseArray(int arr[], int size);
```

**Requirements:**

- Modify the original array
- Swap elements from both ends
- Test with: {1, 2, 3, 4, 5} and {10, 20, 30}

**Expected Output:**

```bash
Original: 1 2 3 4 5
Reversed: 5 4 3 2 1

Original: 10 20 30
Reversed: 30 20 10
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

void reverseArray(int arr[], int size);
void printArray(int arr[], int size);

int main() {
    int arr1[] = {1, 2, 3, 4, 5};
    int size1 = 5;
    
    int arr2[] = {10, 20, 30};
    int size2 = 3;
    
    printf("Original: ");
    printArray(arr1, size1);
    reverseArray(arr1, size1);
    printf("Reversed: ");
    printArray(arr1, size1);
    printf("\n");
    
    printf("Original: ");
    printArray(arr2, size2);
    reverseArray(arr2, size2);
    printf("Reversed: ");
    printArray(arr2, size2);
    
    return 0;
}

void reverseArray(int arr[], int size) {
    int start = 0;
    int end = size - 1;
    
    while (start < end) {
        // Swap elements
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        
        start++;
        end--;
    }
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
```

</details>
---

## Exercise 5: Even or Odd ⭐

Write a function that determines if a number is even or odd.

```c
int isEven(int n);  // Returns 1 if even, 0 if odd
```

**Requirements:**

- Use modulo operator (%)
- Test with: -4, -3, 0, 7, 10

**Expected Output:**

```bash
-4 is even
-3 is odd
0 is even
7 is odd
10 is even
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int isEven(int n);

int main() {
    int numbers[] = {-4, -3, 0, 7, 10};
    int size = 5;
    
    for (int i = 0; i < size; i++) {
        if (isEven(numbers[i])) {
            printf("%d is even\n", numbers[i]);
        } else {
            printf("%d is odd\n", numbers[i]);
        }
    }
    
    return 0;
}

int isEven(int n) {
    return (n % 2 == 0);
}
```

</details>
---

## Exercise 6: Bubble Sort Array ⭐⭐⭐

Write a function to sort an array using bubble sort algorithm:

```c
void bubbleSort(int arr[], int size);
```

**Requirements:**

- Sort array in ascending order
- Implement bubble sort algorithm
- Modify array in place
- Test with: {64, 34, 25, 12, 22, 11, 90}

**Expected Output:**

```bash
Original array: 64 34 25 12 22 11 90
Sorted array:   11 12 22 25 34 64 90
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

void bubbleSort(int arr[], int size);
void printArray(int arr[], int size);

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int size = 7;
    
    printf("Original array: ");
    printArray(arr, size);
    
    bubbleSort(arr, size);
    
    printf("Sorted array:   ");
    printArray(arr, size);
    
    return 0;
}

void bubbleSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        // Flag to optimize (stop if no swaps made)
        int swapped = 0;
        
        for (int j = 0; j < size - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap elements
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = 1;
            }
        }
        
        // If no swaps made, array is sorted
        if (!swapped) {
            break;
        }
    }
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
```

</details>
---

## Exercise 7: Find Maximum ⭐

Write a function to find the maximum of three numbers:

```c
int max3(int a, int b, int c);
```

**Requirements:**

- Compare all three numbers
- Return the largest
- Test with: (5, 2, 8), (10, 10, 5), (-1, -5, -3)

**Expected Output:**

```bash
Max of 5, 2, 8 = 8
Max of 10, 10, 5 = 10
Max of -1, -5, -3 = -1
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int max3(int a, int b, int c);

int main() {
    printf("Max of 5, 2, 8 = %d\n", max3(5, 2, 8));
    printf("Max of 10, 10, 5 = %d\n", max3(10, 10, 5));
    printf("Max of -1, -5, -3 = %d\n", max3(-1, -5, -3));
    
    return 0;
}

int max3(int a, int b, int c) {
    int maximum = a;
    
    if (b > maximum) {
        maximum = b;
    }
    
    if (c > maximum) {
        maximum = c;
    }
    
    return maximum;
}
```

</details>
---

## Exercise 8: Count Digits ⭐⭐

Write a function to count the number of digits in an integer:

```c
int countDigits(int n);
```

**Requirements:**

- Handle negative numbers (count digits only)
- Handle 0 (has 1 digit)
- Test with: 0, 5, -123, 45678

**Expected Output:**

```bash
0 has 1 digit
5 has 1 digit
-123 has 3 digits
45678 has 5 digits
```

<details><summary>Solution</summary>

```c
#include <stdio.h>
#include <stdlib.h>

int countDigits(int n);

int main() {
    int numbers[] = {0, 5, -123, 45678};
    int size = 4;
    
    for (int i = 0; i < size; i++) {
        printf("%d has %d digit", numbers[i], countDigits(numbers[i]));
        if (countDigits(numbers[i]) != 1) {
            printf("s");
        }
        printf("\n");
    }
    
    return 0;
}

int countDigits(int n) {
    // Handle 0 as special case
    if (n == 0) {
        return 1;
    }
    
    // Make number positive for counting
    n = abs(n);
    
    int count = 0;
    while (n > 0) {
        count++;
        n = n / 10;
    }
    
    return count;
}
```

</details>
---

## Exercise 9: Array Sum ⭐

Write a function to calculate the sum of array elements:

```c
int arraySum(int arr[], int size);
```

**Requirements:**

- Use loop to sum all elements
- Test with: {1, 2, 3, 4, 5} and {10, -5, 3, 7}

**Expected Output:**

```bash
Array: 1 2 3 4 5
Sum = 15

Array: 10 -5 3 7
Sum = 15
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int arraySum(int arr[], int size);
void printArray(int arr[], int size);

int main() {
    int arr1[] = {1, 2, 3, 4, 5};
    int size1 = 5;
    
    int arr2[] = {10, -5, 3, 7};
    int size2 = 4;
    
    printf("Array: ");
    printArray(arr1, size1);
    printf("Sum = %d\n\n", arraySum(arr1, size1));
    
    printf("Array: ");
    printArray(arr2, size2);
    printf("Sum = %d\n", arraySum(arr2, size2));
    
    return 0;
}

int arraySum(int arr[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
```

</details>
---

## Exercise 10: Array Statistics ⭐⭐⭐

Write functions to calculate array statistics:

```c
int findMin(int arr[], int size);
int findMax(int arr[], int size);
float findAverage(int arr[], int size);
void printStatistics(int arr[], int size);
```

**Requirements:**

- `printStatistics` should call the other three functions
- Test with: {5, 12, 3, 18, 7, 1, 15}

**Expected Output:**

```bash
Array: 5 12 3 18 7 1 15
Minimum: 1
Maximum: 18
Average: 8.71
Sum: 61
Count: 7
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int findMin(int arr[], int size);
int findMax(int arr[], int size);
float findAverage(int arr[], int size);
void printStatistics(int arr[], int size);
void printArray(int arr[], int size);

int main() {
    int arr[] = {5, 12, 3, 18, 7, 1, 15};
    int size = 7;
    
    printStatistics(arr, size);
    
    return 0;
}

int findMin(int arr[], int size) {
    int min = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
    }
    return min;
}

int findMax(int arr[], int size) {
    int max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    return max;
}

float findAverage(int arr[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return (float)sum / size;
}

void printStatistics(int arr[], int size) {
    printf("Array: ");
    printArray(arr, size);
    printf("Minimum: %d\n", findMin(arr, size));
    printf("Maximum: %d\n", findMax(arr, size));
    printf("Average: %.2f\n", findAverage(arr, size));
    
    // Calculate sum
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    printf("Sum: %d\n", sum);
    printf("Count: %d\n", size);
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
```

</details>

---

## Exercise 11: Factorial (Iterative) ⭐⭐

Write a function to calculate factorial using iteration:

```c
long factorial(int n);
```

**Requirements:**

- Use loop (not recursion)
- Handle n = 0 (should return 1)
- Test with: 0, 1, 5, 10

**Expected Output:**

```bash
0! = 1
1! = 1
5! = 120
10! = 3628800
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

long factorial(int n);

int main() {
    int numbers[] = {0, 1, 5, 10};
    int size = 4;
    
    for (int i = 0; i < size; i++) {
        printf("%d! = %ld\n", numbers[i], factorial(numbers[i]));
    }
    
    return 0;
}

long factorial(int n) {
    // 0! = 1 by definition
    if (n == 0) {
        return 1;
    }
    
    long result = 1;
    for (int i = 1; i <= n; i++) {
        result *= i;
    }
    
    return result;
}
```

</details>
---

## Exercise 12: Array Search ⭐⭐

Write a function to search for an element in an array:

```c
int linearSearch(int arr[], int size, int target);
```

**Requirements:**

- Return index if found, -1 if not found
- Test with array {10, 25, 30, 45, 50}
- Search for: 30, 99

**Expected Output:**

```bash
Array: 10 25 30 45 50
Searching for 30: Found at index 2
Searching for 99: Not found (-1)
```
<details><summary>Solution</summary>

```c
#include <stdio.h>

int linearSearch(int arr[], int size, int target);
void printArray(int arr[], int size);

int main() {
    int arr[] = {10, 25, 30, 45, 50};
    int size = 5;
    
    printf("Array: ");
    printArray(arr, size);
    
    int target1 = 30;
    int index1 = linearSearch(arr, size, target1);
    if (index1 != -1) {
        printf("Searching for %d: Found at index %d\n", target1, index1);
    } else {
        printf("Searching for %d: Not found (%d)\n", target1, index1);
    }
    
    int target2 = 99;
    int index2 = linearSearch(arr, size, target2);
    if (index2 != -1) {
        printf("Searching for %d: Found at index %d\n", target2, index2);
    } else {
        printf("Searching for %d: Not found (%d)\n", target2, index2);
    }
    
    return 0;
}

int linearSearch(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i;  // Return index if found
        }
    }
    return -1;  // Not found
}

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}
```

</details>
---

## Exercise 13: Matrix Operations ⭐⭐⭐

Write functions to work with 2D arrays (matrices):

```c
void readMatrix(int matrix[][10], int rows, int cols);
void printMatrix(int matrix[][10], int rows, int cols);
int sumMatrix(int matrix[][10], int rows, int cols);
```

**Requirements:**

- Read values into a matrix
- Display matrix in grid format
- Calculate sum of all elements
- Test with a 3×3 matrix

**Expected Output:**

```bash
Enter 3x3 matrix:
1 2 3
4 5 6
7 8 9

Matrix:
 1  2  3
 4  5  6
 7  8  9

Sum of all elements: 45
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

void readMatrix(int matrix[][10], int rows, int cols);
void printMatrix(int matrix[][10], int rows, int cols);
int sumMatrix(int matrix[][10], int rows, int cols);

int main() {
    int matrix[10][10];
    int rows = 3, cols = 3;
    
    printf("Enter %dx%d matrix:\n", rows, cols);
    readMatrix(matrix, rows, cols);
    
    printf("\nMatrix:\n");
    printMatrix(matrix, rows, cols);
    
    printf("\nSum of all elements: %d\n", sumMatrix(matrix, rows, cols));
    
    return 0;
}

void readMatrix(int matrix[][10], int rows, int cols) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            scanf("%d", &matrix[i][j]);
        }
    }
}

void printMatrix(int matrix[][10], int rows, int cols) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            printf("%2d ", matrix[i][j]);
        }
        printf("\n");
    }
}

int sumMatrix(int matrix[][10], int rows, int cols) {
    int sum = 0;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            sum += matrix[i][j];
        }
    }
    return sum;
}
```

</details>
---

## Exercise 14: String Functions ⭐⭐⭐

Write functions to manipulate strings:

```c
int stringLength(char str[]);
void stringReverse(char str[]);
int countVowels(char str[]);
```

**Requirements:**

- Calculate string length without using strlen()
- Reverse string in place
- Count vowels (a, e, i, o, u - both upper and lower case)
- Test with: "Programming"

**Expected Output:**

```bash
Original string: Programming
Length: 11
Reversed: gnimmargorP
Number of vowels: 3 (o, a, i)
```

<details><summary>Solution</summary>

```c
#include <stdio.h>
#include <ctype.h>

int stringLength(char str[]);
void stringReverse(char str[]);
int countVowels(char str[]);

int main() {
    char str[] = "Programming";
    
    printf("Original string: %s\n", str);
    printf("Length: %d\n", stringLength(str));
    
    stringReverse(str);
    printf("Reversed: %s\n", str);
    
    // Reverse back for vowel counting
    stringReverse(str);
    printf("Number of vowels: %d\n", countVowels(str));
    
    return 0;
}

int stringLength(char str[]) {
    int length = 0;
    while (str[length] != '\0') {
        length++;
    }
    return length;
}

void stringReverse(char str[]) {
    int length = stringLength(str);
    int start = 0;
    int end = length - 1;
    
    while (start < end) {
        // Swap characters
        char temp = str[start];
        str[start] = str[end];
        str[end] = temp;
        
        start++;
        end--;
    }
}

int countVowels(char str[]) {
    int count = 0;
    
    for (int i = 0; str[i] != '\0'; i++) {
        char ch = tolower(str[i]);
        if (ch == 'a' || ch == 'e' || ch == 'i' || 
            ch == 'o' || ch == 'u') {
            count++;
        }
    }
    
    return count;
}
```

</details>
---

## Exercise 15: Student Grade System ⭐⭐⭐

Write a complete system with multiple functions:

```c
void readScores(int scores[], int size);
float calculateAverage(int scores[], int size);
char assignGrade(float average);
void displayReport(int scores[], int size);
```

**Grading Scale:**

- A: 16-20
- B: 14-15
- C: 12-13
- D: 10-11
- F: 0-9

**Requirements:**

- Read 5 subject scores
- Calculate average
- Assign letter grade
- Display complete report with all scores, average, and grade

**Expected Output:**

```bash
Enter 5 subject scores:
Math: 18
Physics: 16
Chemistry: 15
English: 14
Programming: 17

=== STUDENT REPORT ===
Scores: 18 16 15 14 17
Average: 16.00
Grade: A
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

void readScores(int scores[], int size);
float calculateAverage(int scores[], int size);
char assignGrade(float average);
void displayReport(int scores[], int size);

int main() {
    int scores[5];
    
    printf("Enter 5 subject scores:\n");
    readScores(scores, 5);
    
    displayReport(scores, 5);
    
    return 0;
}

void readScores(int scores[], int size) {
    char subjects[5][20] = {"Math", "Physics", "Chemistry", 
                            "English", "Programming"};
    
    for (int i = 0; i < size; i++) {
        printf("%s: ", subjects[i]);
        scanf("%d", &scores[i]);
        
        // Validate score
        while (scores[i] < 0 || scores[i] > 20) {
            printf("Invalid! Score must be 0-20. Try again: ");
            scanf("%d", &scores[i]);
        }
    }
}

float calculateAverage(int scores[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += scores[i];
    }
    return (float)sum / size;
}

char assignGrade(float average) {
    if (average >= 16) return 'A';
    if (average >= 14) return 'B';
    if (average >= 12) return 'C';
    if (average >= 10) return 'D';
    return 'F';
}

void displayReport(int scores[], int size) {
    float avg = calculateAverage(scores, size);
    char grade = assignGrade(avg);
    
    printf("\n=== STUDENT REPORT ===\n");
    printf("Scores: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", scores[i]);
    }
    printf("\n");
    printf("Average: %.2f\n", avg);
    printf("Grade: %c\n", grade);
}
```

</details>
