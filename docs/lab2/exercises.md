# 🧪 Lab 2: Practice Exercises - Conditional Structures

**Course:** Data Structures & Algorithms 1 — 2025/2026  
**Department of Computer Science, USTHB**  
**Instructor:** Maria Djadi

---

## Exercise 1: Even or Odd Checker ⭐

### Problem

Write a program that asks the user for an integer and determines if it's even or odd.

### Sample Output

```
Enter an integer: 7
7 is odd

Enter an integer: 12
12 is even
```

### Hint

Use the modulus operator: `number % 2`
- If remainder is 0 → even
- If remainder is 1 → odd

---

### Solution

```c
#include <stdio.h>

int main() {
    int number;
    
    printf("Enter an integer: ");
    scanf("%d", &number);
    
    if (number % 2 == 0) {
        printf("%d is even\n", number);
    } else {
        printf("%d is odd\n", number);
    }
    
    return 0;
}
```

---

## Exercise 2: Grade Calculator ⭐⭐

### Problem

Write a program that converts a numerical score (0-100) to a letter grade:
- A: 90-100
- B: 80-89
- C: 70-79
- D: 60-69
- F: below 60

### Sample Output

```
Enter your score: 85
Your grade is: B

Enter your score: 55
Your grade is: F
```

---

### Solution

```c
#include <stdio.h>

int main() {
    int score;
    
    printf("Enter your score: ");
    scanf("%d", &score);
    
    printf("Your grade is: ");
    
    if (score >= 90) {
        printf("A\n");
    } else if (score >= 80) {
        printf("B\n");
    } else if (score >= 70) {
        printf("C\n");
    } else if (score >= 60) {
        printf("D\n");
    } else {
        printf("F\n");
    }
    
    return 0;
}
```

---

## Exercise 3: Leap Year Checker ⭐⭐

### Problem

Determine if a year is a leap year.

**Rules:**
- Divisible by 4 → leap year
- BUT divisible by 100 → NOT a leap year
- BUT divisible by 400 → IS a leap year

### Sample Output

```
Enter a year: 2024
2024 is a leap year

Enter a year: 1900
1900 is not a leap year

Enter a year: 2000
2000 is a leap year
```

---

### Solution

```c
#include <stdio.h>

int main() {
    int year;
    
    printf("Enter a year: ");
    scanf("%d", &year);
    
    if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
        printf("%d is a leap year\n", year);
    } else {
        printf("%d is not a leap year\n", year);
    }
    
    return 0;
}
```

---

## Exercise 4: Triangle Validator ⭐⭐

### Problem

Given three side lengths, determine:
1. If they form a valid triangle
2. What type: Equilateral, Isosceles, or Scalene

**Rules:**
- Valid if: a + b > c, b + c > a, a + c > b
- Equilateral: all sides equal
- Isosceles: two sides equal
- Scalene: all sides different

### Sample Output

```
Enter three sides: 5 5 5
Valid triangle: Equilateral

Enter three sides: 5 5 8
Valid triangle: Isosceles

Enter three sides: 3 4 5
Valid triangle: Scalene

Enter three sides: 1 2 10
Not a valid triangle
```

---

### Solution

```c
#include <stdio.h>

int main() {
    float a, b, c;
    
    printf("Enter three sides: ");
    scanf("%f %f %f", &a, &b, &c);
    
    // Check if valid triangle
    if (a + b > c && b + c > a && a + c > b) {
        printf("Valid triangle: ");
        
        // Determine type
        if (a == b && b == c) {
            printf("Equilateral\n");
        } else if (a == b || b == c || a == c) {
            printf("Isosceles\n");
        } else {
            printf("Scalene\n");
        }
    } else {
        printf("Not a valid triangle\n");
    }
    
    return 0;
}
```

---

## Exercise 5: Simple Calculator ⭐⭐

### Problem

Create a calculator that performs basic operations using a menu.

### Sample Output

```
=== Simple Calculator ===
1. Addition
2. Subtraction
3. Multiplication
4. Division
Choose operation (1-4): 3

Enter two numbers: 5 7
Result: 5 × 7 = 35
```

---

### Solution

```c
#include <stdio.h>

int main() {
    int choice;
    float num1, num2, result;
    
    printf("=== Simple Calculator ===\n");
    printf("1. Addition\n");
    printf("2. Subtraction\n");
    printf("3. Multiplication\n");
    printf("4. Division\n");
    printf("Choose operation (1-4): ");
    scanf("%d", &choice);
    
    printf("Enter two numbers: ");
    scanf("%f %f", &num1, &num2);
    
    switch (choice) {
        case 1:
            result = num1 + num2;
            printf("Result: %.2f + %.2f = %.2f\n", num1, num2, result);
            break;
        case 2:
            result = num1 - num2;
            printf("Result: %.2f - %.2f = %.2f\n", num1, num2, result);
            break;
        case 3:
            result = num1 * num2;
            printf("Result: %.2f × %.2f = %.2f\n", num1, num2, result);
            break;
        case 4:
            if (num2 != 0) {
                result = num1 / num2;
                printf("Result: %.2f ÷ %.2f = %.2f\n", num1, num2, result);
            } else {
                printf("Error: Division by zero!\n");
            }
            break;
        default:
            printf("Invalid choice!\n");
    }
    
    return 0;
}
```

---

## Exercise 6: BMI with Categories ⭐⭐

### Problem

Calculate BMI and display the category.

**BMI Categories:**
- Underweight: BMI < 18.5
- Normal: 18.5 ≤ BMI < 25
- Overweight: 25 ≤ BMI < 30
- Obese: BMI ≥ 30

### Sample Output

```
Enter weight (kg): 70
Enter height (m): 1.75

Your BMI: 22.86
Category: Normal weight
Status: Healthy range
```

---

### Solution

```c
#include <stdio.h>

int main() {
    float weight, height, bmi;
    
    printf("Enter weight (kg): ");
    scanf("%f", &weight);
    
    printf("Enter height (m): ");
    scanf("%f", &height);
    
    bmi = weight / (height * height);
    
    printf("\nYour BMI: %.2f\n", bmi);
    printf("Category: ");
    
    if (bmi < 18.5) {
        printf("Underweight\n");
        printf("Status: Below healthy range\n");
    } else if (bmi < 25) {
        printf("Normal weight\n");
        printf("Status: Healthy range\n");
    } else if (bmi < 30) {
        printf("Overweight\n");
        printf("Status: Above healthy range\n");
    } else {
        printf("Obese\n");
        printf("Status: Consult healthcare provider\n");
    }
    
    return 0;
}
```

---

## Exercise 7: Quadratic Equation Solver ⭐⭐⭐

### Problem

Solve ax² + bx + c = 0 for all cases:
- Two real roots (discriminant > 0)
- One real root (discriminant = 0)
- Complex roots (discriminant < 0)

**Formula:** x = [-b ± √(b²-4ac)] / 2a

### Sample Output

```
Enter coefficients (a b c): 1 -5 6
Two real roots:
x1 = 3.00
x2 = 2.00

Enter coefficients (a b c): 1 -2 1
One real root:
x = 1.00

Enter coefficients (a b c): 1 0 1
Complex roots:
Real part: 0.00
Imaginary part: ±1.00
```

---

### Solution

```c
#include <stdio.h>
#include <math.h>

int main() {
    double a, b, c, discriminant, root1, root2, realPart, imagPart;
    
    printf("Enter coefficients (a b c): ");
    scanf("%lf %lf %lf", &a, &b, &c);
    
    // Calculate discriminant
    discriminant = b * b - 4 * a * c;
    
    if (discriminant > 0) {
        // Two real roots
        root1 = (-b + sqrt(discriminant)) / (2 * a);
        root2 = (-b - sqrt(discriminant)) / (2 * a);
        printf("Two real roots:\n");
        printf("x1 = %.2f\n", root1);
        printf("x2 = %.2f\n", root2);
    } else if (discriminant == 0) {
        // One real root
        root1 = -b / (2 * a);
        printf("One real root:\n");
        printf("x = %.2f\n", root1);
    } else {
        // Complex roots
        realPart = -b / (2 * a);
        imagPart = sqrt(-discriminant) / (2 * a);
        printf("Complex roots:\n");
        printf("Real part: %.2f\n", realPart);
        printf("Imaginary part: ±%.2f\n", imagPart);
    }
    
    return 0;
}
```

---

## Exercise 8: Day of Week ⭐

### Problem

Given a number (1-7), display the corresponding day of the week.

### Sample Output

```
Enter day number (1-7): 3
Wednesday

Enter day number (1-7): 8
Invalid day number!
```

---

### Solution

```c
#include <stdio.h>

int main() {
    int day;
    
    printf("Enter day number (1-7): ");
    scanf("%d", &day);
    
    switch (day) {
        case 1:
            printf("Monday\n");
            break;
        case 2:
            printf("Tuesday\n");
            break;
        case 3:
            printf("Wednesday\n");
            break;
        case 4:
            printf("Thursday\n");
            break;
        case 5:
            printf("Friday\n");
            break;
        case 6:
            printf("Saturday\n");
            break;
        case 7:
            printf("Sunday\n");
            break;
        default:
            printf("Invalid day number!\n");
    }
    
    return 0;
}
```

---

## Exercise 9: Electricity Bill with Tiers ⭐⭐⭐

### Problem

Calculate electricity bill using SONELGAZ's tiered pricing:
- 0-125 KWH: 1.78 DA/KWH
- 126-250 KWH: 4.18 DA/KWH
- 251-1000 KWH: 4.81 DA/KWH
- Above 1000 KWH: 5.48 DA/KWH

### Sample Output

```
Enter consumption (KWH): 300

=== Electricity Bill ===
First 125 KWH: 222.50 DA
Next 125 KWH: 522.50 DA
Next 50 KWH: 240.50 DA
Total: 985.50 DA
```

---

### Solution

```c
#include <stdio.h>

int main() {
    float consumption, bill = 0, remaining;
    
    printf("Enter consumption (KWH): ");
    scanf("%f", &consumption);
    
    printf("\n=== Electricity Bill ===\n");
    
    remaining = consumption;
    
    // First tier: 0-125 KWH at 1.78 DA
    if (remaining > 0) {
        float tier1 = (remaining > 125) ? 125 : remaining;
        bill += tier1 * 1.78;
        printf("First %.0f KWH: %.2f DA\n", tier1, tier1 * 1.78);
        remaining -= tier1;
    }
    
    // Second tier: 126-250 KWH at 4.18 DA
    if (remaining > 0) {
        float tier2 = (remaining > 125) ? 125 : remaining;
        bill += tier2 * 4.18;
        printf("Next %.0f KWH: %.2f DA\n", tier2, tier2 * 4.18);
        remaining -= tier2;
    }
    
    // Third tier: 251-1000 KWH at 4.81 DA
    if (remaining > 0) {
        float tier3 = (remaining > 750) ? 750 : remaining;
        bill += tier3 * 4.81;
        printf("Next %.0f KWH: %.2f DA\n", tier3, tier3 * 4.81);
        remaining -= tier3;
    }
    
    // Fourth tier: Above 1000 KWH at 5.48 DA
    if (remaining > 0) {
        bill += remaining * 5.48;
        printf("Next %.0f KWH: %.2f DA\n", remaining, remaining * 5.48);
    }
    
    printf("\nTotal: %.2f DA\n", bill);
    
    return 0;
}
```

---

## Exercise 10: Character Type Checker ⭐⭐

### Problem

Determine if a character is:
- Uppercase letter (A-Z)
- Lowercase letter (a-z)
- Digit (0-9)
- Special character

### Sample Output

```
Enter a character: A
Uppercase letter

Enter a character: 7
Digit

Enter a character: @
Special character
```

---

### Solution

```c
#include <stdio.h>

int main() {
    char ch;
    
    printf("Enter a character: ");
    scanf(" %c", &ch);  // Space before %c to skip whitespace
    
    if (ch >= 'A' && ch <= 'Z') {
        printf("Uppercase letter\n");
    } else if (ch >= 'a' && ch <= 'z') {
        printf("Lowercase letter\n");
    } else if (ch >= '0' && ch <= '9') {
        printf("Digit\n");
    } else {
        printf("Special character\n");
    }
    
    return 0;
}
```

---

## Exercise 11: Max of Three Numbers ⭐

### Problem

Find the maximum of three numbers.

### Sample Output

```
Enter three numbers: 5 12 8
Maximum: 12
```

---

### Solution

```c
#include <stdio.h>

int main() {
    int a, b, c, max;
    
    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);
    
    // Method 1: Nested if
    if (a >= b && a >= c) {
        max = a;
    } else if (b >= c) {
        max = b;
    } else {
        max = c;
    }
    
    printf("Maximum: %d\n", max);
    
    return 0;
}
```

---

## Exercise 12: Vowel or Consonant ⭐

### Problem

Check if a letter is a vowel or consonant.

### Sample Output

```
Enter a letter: e
e is a vowel

Enter a letter: k
k is a consonant
```

---

### Solution

```c
#include <stdio.h>

int main() {
    char ch;
    
    printf("Enter a letter: ");
    scanf(" %c", &ch);
    
    // Convert to lowercase for easier checking
    if (ch >= 'A' && ch <= 'Z') {
        ch = ch + 32;  // Convert to lowercase
    }
    
    if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
        printf("%c is a vowel\n", ch);
    } else if (ch >= 'a' && ch <= 'z') {
        printf("%c is a consonant\n", ch);
    } else {
        printf("Not a letter!\n");
    }
    
    return 0;
}
```

---

## 🎯 Exercise Summary

| Exercise | Difficulty | Concepts |
|----------|-----------|----------|
| 1. Even/Odd | ⭐ | Basic if-else, modulus |
| 2. Grade Calculator | ⭐⭐ | if-else chain, ordering |
| 3. Leap Year | ⭐⭐ | Logical operators (&&, \|\|) |
| 4. Triangle Validator | ⭐⭐ | Nested if, multiple conditions |
| 5. Simple Calculator | ⭐⭐ | switch statement, division by zero |
| 6. BMI Categories | ⭐⭐ | if-else chain, ranges |
| 7. Quadratic Solver | ⭐⭐⭐ | Complex conditions, math.h |
| 8. Day of Week | ⭐ | switch statement basics |
| 9. Electricity Tiers | ⭐⭐⭐ | Complex if-else, real-world logic |
| 10. Character Type | ⭐⭐ | Character ranges, ASCII |
| 11. Max of Three | ⭐ | Multiple comparisons |
| 12. Vowel/Consonant | ⭐ | Logical OR, case handling |

---

## 📝 Testing Tips

### Test Edge Cases

For each exercise, test:
- **Boundary values** (exactly at limits)
- **Normal values** (typical cases)
- **Invalid input** (out of range)

**Example for Grade Calculator:**
- Test: 90, 89, 80, 79, 70, 69, 60, 59
- Test: 100, 0, -5, 150

### Use printf for Debugging

```c
// Add this to see what your program is thinking
printf("DEBUG: score = %d\n", score);
printf("DEBUG: condition result = %d\n", score >= 90);
```

---

## 🚀 Challenge Problems

After completing all exercises, try these:

### Challenge 1: Complete Date Validator
Validate a date (day, month, year) considering:
- Days in each month
- Leap years
- Invalid dates like Feb 30

### Challenge 2: Simple Tax Calculator
Calculate income tax with multiple brackets:
- 0-30,000: 0%
- 30,001-120,000: 10%
- 120,001-360,000: 20%
- Above 360,000: 35%

### Challenge 3: Rock-Paper-Scissors Game
- User picks (1=Rock, 2=Paper, 3=Scissors)
- Computer picks randomly
- Determine winner

---

## ✅ Submission Checklist

Before submitting:

- [ ] All programs compile without errors
- [ ] Tested with at least 3 different inputs per program
- [ ] Code is properly indented
- [ ] Variables have meaningful names
- [ ] All if-else chains are ordered correctly
- [ ] All switch statements have `break`
- [ ] Division by zero is handled where applicable

---

> **Prepared and maintained by Maria Djadi**  
> Department of Computer Science, USTHB  
> ✉️ [maria.djadi@usthb.edu.dz](mailto:maria.djadi@usthb.edu.dz)

---

**End of Practice Exercises**