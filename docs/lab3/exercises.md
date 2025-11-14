# 🔄 Lab 3: Practice Exercises - Iterative Structures

---

## Exercise 1: Sum of First N Numbers ⭐

### Problem

Calculate the sum of first N natural numbers (1 + 2 + 3 + ... + N).

### Sample Output

```bash
Enter N: 10
Sum = 55
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int n, sum = 0;
    do{
        printf("N must be positive. Please enter again.\n");
        printf("Enter N: ");
        scanf("%d", &n);
    }while(n <= 0);
    
    for (int i = 1; i <= n; i++) {
        sum += i;
    }
    
    printf("Sum = %d\n", sum);
    
    return 0;
}
```

</details>

---

## Exercise 2: Factorial Calculator ⭐

### Problem

Calculate N! (factorial) = N × (N-1) × (N-2) × ... × 1

### Sample Output

```
Enter N: 5
5! = 120
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int n;
    long long factorial = 1;
    
    printf("Enter N: ");
    scanf("%d", &n);
    
    for (int i = 1; i <= n; i++) {
        factorial *= i;
    }
    
    printf("%d! = %lld\n", n, factorial);
    
    return 0;
}
```

</details>

---

## Exercise 3: Multiplication Table ⭐

### Problem

Print multiplication table for a given number up to 10.

### Sample Output

```
Enter number: 5
5 × 1 = 5
5 × 2 = 10
5 × 3 = 15
...
5 × 10 = 50
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int num;
    
    printf("Enter number: ");
    scanf("%d", &num);
    
    for (int i = 1; i <= 10; i++) {
        printf("%d × %d = %d\n", num, i, num * i);
    }
    
    return 0;
}
```

</details>

---

## Exercise 4: Prime Number Checker ⭐⭐

### Problem

Check if a number is prime (only divisible by 1 and itself).

### Sample Output

```
Enter a number: 17
17 is prime

Enter a number: 15
15 is not prime (divisible by 3)
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int n, isPrime = 1;
    
    printf("Enter a number: ");
    scanf("%d", &n);
    
    if (n <= 1) {
        isPrime = 0;
    } else {
        for (int i = 2; i * i <= n; i++) {
            if (n % i == 0) {
                isPrime = 0;
                printf("%d is not prime (divisible by %d)\n", n, i);
                break;
            }
        }
    }
    
    if (isPrime && n > 1) {
        printf("%d is prime\n", n);
    } else if (n <= 1) {
        printf("%d is not prime\n", n);
    }
    
    return 0;
}
```

</details>

---

## Exercise 5: Fibonacci Sequence ⭐⭐

### Problem

Generate first N numbers in Fibonacci sequence (each number is sum of previous two).

### Sample Output

```
Enter N: 10
Fibonacci sequence:
0 1 1 2 3 5 8 13 21 34
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int n, first = 0, second = 1, next;
    
    printf("Enter N: ");
    scanf("%d", &n);
    
    printf("Fibonacci sequence:\n");
    
    for (int i = 0; i < n; i++) {
        if (i == 0) {
            printf("%d ", first);
        } else if (i == 1) {
            printf("%d ", second);
        } else {
            next = first + second;
            printf("%d ", next);
            first = second;
            second = next;
        }
    }
    printf("\n");
    
    return 0;
}
```

</details>

---

## Exercise 6: Reverse a Number ⭐⭐

### Problem

Reverse the digits of a number.

### Sample Output

```bash
Enter a number: 12345
Reversed: 54321
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int num, reversed = 0, remainder;
    
    printf("Enter a number: ");
    scanf("%d", &num);
    
    int original = num;  // Save original
    
    while (num != 0) {
        remainder = num % 10;
        reversed = reversed * 10 + remainder;
        num /= 10;
    }
    
    printf("Reversed: %d\n", reversed);
    
    return 0;
}
```

</details>

---

## Exercise 7: Palindrome Checker ⭐⭐

### Problem

Check if a number is palindrome (reads same forwards and backwards).

### Sample Output

```
Enter a number: 12321
12321 is a palindrome

Enter a number: 12345
12345 is not a palindrome
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int num, original, reversed = 0, remainder;
    
    printf("Enter a number: ");
    scanf("%d", &num);
    
    original = num;
    
    while (num != 0) {
        remainder = num % 10;
        reversed = reversed * 10 + remainder;
        num /= 10;
    }
    
    if (original == reversed) {
        printf("%d is a palindrome\n", original);
    } else {
        printf("%d is not a palindrome\n", original);
    }
    
    return 0;
}
```

</details>

---

## Exercise 8: GCD Calculator ⭐⭐

### Problem

Find Greatest Common Divisor (GCD) of two numbers using Euclidean algorithm.

### Sample Output

```
Enter two numbers: 48 18
GCD(48, 18) = 6
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int a, b, gcd;
    
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);
    
    int num1 = a, num2 = b;  // Save originals
    
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    
    gcd = a;
    printf("GCD(%d, %d) = %d\n", num1, num2, gcd);
    
    return 0;
}
```

</details>

---

## Exercise 9: Armstrong Number Checker ⭐⭐

### Problem

Check if a number is Armstrong number (sum of cubes of digits equals the number).
Example: 153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153

### Sample Output

```
Enter a number: 153
153 is an Armstrong number

Enter a number: 123
123 is not an Armstrong number
```

<details><summary>Solution</summary>

```c
#include <stdio.h>
#include <math.h>

int main() {
    int num, original, remainder, sum = 0, digits = 0;
    
    printf("Enter a number: ");
    scanf("%d", &num);
    
    original = num;
    
    // Count digits
    int temp = num;
    while (temp != 0) {
        digits++;
        temp /= 10;
    }
    
    // Calculate sum of powers
    temp = num;
    while (temp != 0) {
        remainder = temp % 10;
        sum += pow(remainder, digits);
        temp /= 10;
    }
    
    if (sum == original) {
        printf("%d is an Armstrong number\n", original);
    } else {
        printf("%d is not an Armstrong number\n", original);
    }
    
    return 0;
}
```

</details>

---

## Exercise 10: Pattern - Right Triangle ⭐

### Problem

Print a right triangle pattern of stars.

### Sample Output

```
Enter height: 5
*
**
***
****
*****
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int height;
    
    printf("Enter height: ");
    scanf("%d", &height);
    
    for (int i = 1; i <= height; i++) {
        for (int j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }
    
    return 0;
}
```

</details>

---

## Exercise 11: Pattern - Pyramid ⭐⭐

### Problem

Print a centered pyramid pattern.

### Sample Output

```
Enter height: 5
    *
   ***
  *****
 *******
*********
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int height;
    
    printf("Enter height: ");
    scanf("%d", &height);
    
    for (int i = 1; i <= height; i++) {
        // Print spaces
        for (int j = 1; j <= height - i; j++) {
            printf(" ");
        }
        // Print stars
        for (int j = 1; j <= 2*i - 1; j++) {
            printf("*");
        }
        printf("\n");
    }
    
    return 0;
}
```

</details>

---

## Exercise 12: Sum of Digits ⭐

### Problem

Calculate sum of all digits in a number.

### Sample Output

```
Enter a number: 12345
Sum of digits: 15
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int num, sum = 0, digit;
    
    printf("Enter a number: ");
    scanf("%d", &num);
    
    while (num != 0) {
        digit = num % 10;
        sum += digit;
        num /= 10;
    }
    
    printf("Sum of digits: %d\n", sum);
    
    return 0;
}
```

</details>

---

## Exercise 13: Count Digits ⭐

### Problem

Count number of digits in a number.

### Sample Output

```
Enter a number: 12345
Number of digits: 5
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int num, count = 0;
    
    printf("Enter a number: ");
    scanf("%d", &num);
    
    if (num == 0) {
        count = 1;
    } else {
        while (num != 0) {
            count++;
            num /= 10;
        }
    }
    
    printf("Number of digits: %d\n", count);
    
    return 0;
}
```

</details>

---

## Exercise 14: Perfect Number Checker ⭐⭐

### Problem

Check if a number is perfect (sum of divisors equals the number).
Example: 6 = 1 + 2 + 3

### Sample Output

```
Enter a number: 6
6 is a perfect number
Divisors: 1 2 3

Enter a number: 10
10 is not a perfect number
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int num, sum = 0;
    
    printf("Enter a number: ");
    scanf("%d", &num);
    
    printf("Divisors: ");
    for (int i = 1; i < num; i++) {
        if (num % i == 0) {
            printf("%d ", i);
            sum += i;
        }
    }
    printf("\n");
    
    if (sum == num) {
        printf("%d is a perfect number\n", num);
    } else {
        printf("%d is not a perfect number\n", num);
    }
    
    return 0;
}
```

</details>

---

## Exercise 15: Print All Primes Up to N ⭐⭐⭐

### Problem

Print all prime numbers from 1 to N.

### Sample Output

```
Enter N: 30
Prime numbers up to 30:
2 3 5 7 11 13 17 19 23 29
Total: 10 primes
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int n, count = 0;
    
    printf("Enter N: ");
    scanf("%d", &n);
    
    printf("Prime numbers up to %d:\n", n);
    
    for (int num = 2; num <= n; num++) {
        int isPrime = 1;
        
        for (int i = 2; i * i <= num; i++) {
            if (num % i == 0) {
                isPrime = 0;
                break;
            }
        }
        
        if (isPrime) {
            printf("%d ", num);
            count++;
        }
    }
    
    printf("\nTotal: %d primes\n", count);
    
    return 0;
}
```

</details>

---

## Exercise 16: LCM Calculator ⭐⭐

### Problem

Find Least Common Multiple (LCM) of two numbers.
Formula: LCM(a, b) = (a × b) / GCD(a, b)

### Sample Output

```
Enter two numbers: 12 18
LCM(12, 18) = 36
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int a, b, gcd, lcm;
    
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);
    
    int num1 = a, num2 = b;
    
    // Find GCD
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    gcd = a;
    
    // Calculate LCM
    lcm = (num1 * num2) / gcd;
    
    printf("LCM(%d, %d) = %d\n", num1, num2, lcm);
    
    return 0;
}
```

</details>

---

## Exercise 17: Power Calculator ⭐

### Problem

Calculate x^n (x raised to power n) without using pow().

### Sample Output

```
Enter base: 2
Enter exponent: 5
2^5 = 32
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int base, exponent;
    long long result = 1;
    
    printf("Enter base: ");
    scanf("%d", &base);
    printf("Enter exponent: ");
    scanf("%d", &exponent);
    
    for (int i = 0; i < exponent; i++) {
        result *= base;
    }
    
    printf("%d^%d = %lld\n", base, exponent, result);
    
    return 0;
}
```

</details>

---

## Exercise 18: Menu-Driven Calculator ⭐⭐

### Problem

Create a calculator with menu that loops until user exits.

### Sample Output

```
=== Calculator ===
1. Add
2. Subtract
3. Multiply
4. Divide
5. Exit
Choice: 1
Enter two numbers: 5 3
Result: 8

Choice: 5
Goodbye!
```

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int choice;
    float num1, num2, result;
    
    do {
        printf("\n=== Calculator ===\n");
        printf("1. Add\n");
        printf("2. Subtract\n");
        printf("3. Multiply\n");
        printf("4. Divide\n");
        printf("5. Exit\n");
        printf("Choice: ");
        scanf("%d", &choice);
        
        if (choice >= 1 && choice <= 4) {
            printf("Enter two numbers: ");
            scanf("%f %f", &num1, &num2);
        }
        
        switch (choice) {
            case 1:
                result = num1 + num2;
                printf("Result: %.2f\n", result);
                break;
            case 2:
                result = num1 - num2;
                printf("Result: %.2f\n", result);
                break;
            case 3:
                result = num1 * num2;
                printf("Result: %.2f\n", result);
                break;
            case 4:
                if (num2 != 0) {
                    result = num1 / num2;
                    printf("Result: %.2f\n", result);
                } else {
                    printf("Error: Division by zero!\n");
                }
                break;
            case 5:
                printf("Goodbye!\n");
                break;
            default:
                printf("Invalid choice!\n");
        }
        
    } while (choice != 5);
    
    return 0;
}
```

</details>

---


## 💡 Tips for Success

### Debugging Loops

**Add debug output:**

```c
for (int i = 0; i < n; i++) {
    printf("DEBUG: i=%d\n", i);
    // Your code
}
```

### Testing Strategy

Test each exercise with:

- Normal values
- Edge cases (0, 1, negative)
- Large values
- Boundary values

### Common Mistakes to Avoid

- Forgetting to update loop variable
- Off-by-one errors (`<` vs `<=`)
- Infinite loops
- Modifying loop counter inside body

---
