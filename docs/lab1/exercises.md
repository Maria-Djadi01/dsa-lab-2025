# 🧪 Lab 1: Practice Exercises

## 📚 Exercise Overview

These exercises are designed to reinforce the fundamental concepts covered in Lab 1:

- Variable declarations and initialization
- Arithmetic operations
- Mathematical functions
- Type casting
- Input/output operations
- Formula implementation

---

## Exercise 1: Circle Calculator ⭐

### Problem Statement

Ask the user to enter the radius of a circle. Compute and display both the **area** and **circumference**.

**Formulas:**

- Area = π × r²
- Circumference = 2 × π × r

**Use:** π = 3.14159265359

### Sample Input/Output

```text
Enter the radius of the circle: 5

=== Circle Properties ===
Radius: 5.00
Area: 78.54
Circumference: 31.42
```

### Requirements

- Use `#define` or `const` for PI
- Display results with 2 decimal places
- Handle decimal radius values

### Hints

1. Include `math.h` for the `pow()` function (or use `r * r`)
2. Use `%f` format specifier for float/double
3. Use `%.2f` to display 2 decimal places

---

<details><summary>Solution</summary>

```c
#include <stdio.h>
#include <math.h>

int main() {
    const double PI = 3.14159265359;
    double radius, area, circumference;
    
    // Input
    printf("Enter the radius of the circle: ");
    scanf("%lf", &radius);
    
    // Calculations
    area = PI * radius * radius;  // Or: PI * pow(radius, 2)
    circumference = 2 * PI * radius;
    
    // Output
    printf("\n=== Circle Properties ===\n");
    printf("Radius: %.2f\n", radius);
    printf("Area: %.2f\n", area);
    printf("Circumference: %.2f\n", circumference);
    
    return 0;
}
```

</details>

---

## Exercise 2: Currency Converter ⭐⭐

### Problem Statement

Ask for an amount in **Algerian Dinar (DZD)** and convert it to USD, EUR, and GBP using fixed exchange rates.

**Exchange Rates:**

- 1 USD = 134 DZD
- 1 EUR = 145 DZD
- 1 GBP = 165 DZD

### Sample Input/Output


```
Enter amount in DZD: 10000

=== Currency Conversion ===
10000.00 DZD =
  74.63 USD
  68.97 EUR
  60.61 GBP
```

### Requirements

- Use constants for exchange rates
- Display all currencies with 2 decimal places
- Handle large amounts correctly

### Hints

1. To convert DZD to USD: `usd = dzd / rate_usd`
2. Division gives you the foreign currency amount
3. Use `const double` for exchange rates

---

<details><summary>Solution</summary>

```c
#include <stdio.h>

// Define exchange rates (1 unit = X DZD)
const double USD_RATE = 134.0;
const double EUR_RATE = 145.0;
const double GBP_RATE = 165.0;

int main() {
    double dzd, usd, eur, gbp;
    
    // Input
    printf("Enter amount in DZD: ");
    scanf("%lf", &dzd);
    
    // Conversions
    usd = dzd / USD_RATE;
    eur = dzd / EUR_RATE;
    gbp = dzd / GBP_RATE;
    
    // Output
    printf("\n=== Currency Conversion ===\n");
    printf("%.2f DZD =\n", dzd);
    printf("  %.2f USD\n", usd);
    printf("  %.2f EUR\n", eur);
    printf("  %.2f GBP\n", gbp);
    
    return 0;
}
```

</details>

---

## Exercise 3: BMI Calculator ⭐

### Problem Statement

Ask the user to input their **height** (in meters) and **weight** (in kilograms), then compute and display their BMI.

**Formula:**

```text
BMI = weight / (height × height)
```

**BMI Categories:**

- Underweight: BMI < 18.5
- Normal weight: 18.5 ≤ BMI < 25
- Overweight: 25 ≤ BMI < 30
- Obese: BMI ≥ 30

*(We'll add category display next week with conditionals!)*

### Sample Input/Output

```bash
Enter your weight (kg): 70
Enter your height (m): 1.75

=== BMI Calculator ===
Weight: 70.00 kg
Height: 1.75 m
Your BMI: 22.86
```

### Requirements

- Accept decimal values for height and weight
- Display BMI with 2 decimal places
- Handle height in meters (not centimeters)

### Hints

1. BMI formula uses height in meters
2. height × height can be written as `height * height` or `pow(height, 2)`
3. Use `double` for better precision

---

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    double weight, height, bmi;
    
    // Input
    printf("Enter your weight (kg): ");
    scanf("%lf", &weight);
    
    printf("Enter your height (m): ");
    scanf("%lf", &height);
    
    // Calculate BMI
    bmi = weight / (height * height);
    
    // Output
    printf("\n=== BMI Calculator ===\n");
    printf("Weight: %.2f kg\n", weight);
    printf("Height: %.2f m\n", height);
    printf("Your BMI: %.2f\n", bmi);
    
    // Note: We'll add category interpretation next week!
    printf("\nBMI Categories:\n");
    printf("  < 18.5: Underweight\n");
    printf("  18.5-24.9: Normal weight\n");
    printf("  25.0-29.9: Overweight\n");
    printf("  >= 30.0: Obese\n");
    
    return 0;
}
```

</details>

---

## Exercise 4: Distance Between Two Points ⭐⭐

### Problem Statement

Input two points in a 2D plane **(x₁, y₁)** and **(x₂, y₂)**, then compute the **Euclidean distance** between them.

**Formula:**

```text
distance = √[(x₂ - x₁)² + (y₂ - y₁)²]
```

### Sample Input/Output

```bash
Enter coordinates of point 1 (x1 y1): 0 0
Enter coordinates of point 2 (x2 y2): 3 4

=== Distance Calculator ===
Point 1: (0.00, 0.00)
Point 2: (3.00, 4.00)
Distance: 5.00
```

### Requirements

- Use `sqrt()` function from `math.h`
- Display coordinates and distance with 2 decimal places
- Handle negative coordinates

### Hints

1. Remember: (x₂ - x₁)² = `(x2 - x1) * (x2 - x1)` or `pow(x2 - x1, 2)`
2. Must include `math.h` for `sqrt()`
3. Compile with `-lm` flag on Linux/Mac

---

<details><summary>Solution</summary>

```c
#include <stdio.h>
#include <math.h>

int main() {
    double x1, y1, x2, y2;
    double distance;
    
    // Input first point
    printf("Enter coordinates of point 1 (x1 y1): ");
    scanf("%lf %lf", &x1, &y1);
    
    // Input second point
    printf("Enter coordinates of point 2 (x2 y2): ");
    scanf("%lf %lf", &x2, &y2);
    
    // Calculate distance
    // Method 1: Using separate calculations
    double dx = x2 - x1;  // Difference in x
    double dy = y2 - y1;  // Difference in y
    distance = sqrt(dx * dx + dy * dy);
    
    // Method 2: All in one line
    // distance = sqrt(pow(x2 - x1, 2) + pow(y2 - y1, 2));
    
    // Output
    printf("\n=== Distance Calculator ===\n");
    printf("Point 1: (%.2f, %.2f)\n", x1, y1);
    printf("Point 2: (%.2f, %.2f)\n", x2, y2);
    printf("Distance: %.2f\n", distance);
    
    return 0;
}
```

</details>

---

## Exercise 5: Time Conversion (Seconds to Clock) ⭐⭐

### Problem Statement

Ask the user to input a **duration in seconds**, then compute and display the equivalent **hours, minutes, and remaining seconds**.

**Example:** 3665 seconds = 1 hour, 1 minute, 5 seconds

### Sample Input/Output

```bash
Enter duration in seconds: 3665

=== Time Conversion ===
Total seconds: 3665
Formatted: 1:01:05
(1 hours, 1 minutes, 5 seconds)
```

### Requirements

- Use integer division and modulus operators
- Format output as H:MM:SS
- Handle large values (e.g., 86400 seconds = 1 day)

### Hints

1. Hours = seconds / 3600
2. Remaining after hours = seconds % 3600
3. Minutes = remaining / 60
4. Seconds = remaining % 60

---

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int totalSeconds, hours, minutes, seconds, remaining;
    
    // Input
    printf("Enter duration in seconds: ");
    scanf("%d", &totalSeconds);
    
    // Calculations
    hours = totalSeconds / 3600;              // 3600 seconds = 1 hour
    remaining = totalSeconds % 3600;          // Leftover after extracting hours
    
    minutes = remaining / 60;                 // 60 seconds = 1 minute
    seconds = remaining % 60;                 // Leftover seconds
    
    // Output
    printf("\n=== Time Conversion ===\n");
    printf("Total seconds: %d\n", totalSeconds);
    printf("Formatted: %d:%02d:%02d\n", hours, minutes, seconds);
    printf("(%d hours, %d minutes, %d seconds)\n", hours, minutes, seconds);
    
    return 0;
}
```

</details>

---

## Exercise 6: Elapsed Time Between Two Clock Times ⭐⭐⭐

### Problem Statement

Ask for two times: **start time** (h₁, m₁, s₁) and **end time** (h₂, m₂, s₂). Compute and display the **total elapsed time** in hours, minutes, and seconds.

**Assumption:** End time is always after start time (same day).

### Sample Input/Output

```bash
Enter start time (hours minutes seconds): 10 30 45
Enter end time (hours minutes seconds): 14 45 20

=== Elapsed Time Calculator ===
Start: 10:30:45
End:   14:45:20
Elapsed: 4:14:35
(4 hours, 14 minutes, 35 seconds)
```

### Requirements

- Handle cases where seconds/minutes need borrowing
- Display in H:MM:SS format
- Validate that end time > start time (for now, just assume it is)

### Hints

1. Convert both times to total seconds
2. Calculate difference in seconds
3. Convert difference back to H:M:S format
4. Reuse logic from Exercise 5!

---

<details><summary>Solution</summary>

```c
#include <stdio.h>

int main() {
    int h1, m1, s1;  // Start time
    int h2, m2, s2;  // End time
    int startSeconds, endSeconds, elapsedSeconds;
    int hours, minutes, seconds, remaining;
    
    // Input start time
    printf("Enter start time (hours minutes seconds): ");
    scanf("%d %d %d", &h1, &m1, &s1);
    
    // Input end time
    printf("Enter end time (hours minutes seconds): ");
    scanf("%d %d %d", &h2, &m2, &s2);
    
    // Convert both times to total seconds
    startSeconds = h1 * 3600 + m1 * 60 + s1;
    endSeconds = h2 * 3600 + m2 * 60 + s2;
    
    // Calculate elapsed time
    elapsedSeconds = endSeconds - startSeconds;
    
    // Convert elapsed seconds back to H:M:S
    hours = elapsedSeconds / 3600;
    remaining = elapsedSeconds % 3600;
    minutes = remaining / 60;
    seconds = remaining % 60;
    
    // Output
    printf("\n=== Elapsed Time Calculator ===\n");
    printf("Start: %02d:%02d:%02d\n", h1, m1, s1);
    printf("End:   %02d:%02d:%02d\n", h2, m2, s2);
    printf("Elapsed: %d:%02d:%02d\n", hours, minutes, seconds);
    printf("(%d hours, %d minutes, %d seconds)\n", hours, minutes, seconds);
    
    return 0;
}
```

</details>

---
## 🚗 Lab 1: Homework Assignment

### Problem: Road Trip Budget Calculator

Create a program that calculates fuel consumption, costs, and trip details for a journey.

---

### Input

Your program asks for:

1. Distance to travel (km)
2. Vehicle fuel consumption (L/100km)
3. Fuel price per liter (DA)
4. Average speed (km/h)
5. Number of passengers

---

### Calculate and Display

Your program must calculate these **7 values**:

#### 1. Total fuel needed (liters)

```bash
Total Fuel = (Distance / 100) × Fuel Consumption
```

#### 2. Total fuel cost (DA)

```bash
Total Cost = Total Fuel × Price per Liter
```

#### 3. Cost per passenger (DA)

```bash
Cost per Passenger = Total Cost / Number of Passengers
```

#### 4. Trip duration (hours and minutes)

```bash
Hours = Distance / Speed
Minutes = (Distance % Speed) * 60 / Speed
```

#### 5. Cost per kilometer (DA/km)

```bash
Cost per km = Total Cost / Distance
```

#### 6. Number of fuel stops

```bash
Assume tank capacity = 50 liters
Stops = how many times you need to refuel
Use ceil() function from math.h
```

#### 7. CO₂ emissions (kg)

```bash
CO₂ = Total Fuel × 2.31
(2.31 kg CO₂ per liter of gasoline)
```

---

### Example Output

```bash
Enter distance to travel (km): 450
Enter vehicle fuel consumption (L/100km): 7.5
Enter fuel price per liter (DA): 45.50
Enter average speed (km/h): 110
Enter number of passengers: 4

=== Trip Calculation ===
Distance: 450 km
Estimated Duration: 4h 05min

Fuel Consumption:
  Total Fuel Needed: 33.75 L
  Total Cost: 1535.63 DA
  Cost per km: 3.41 DA
  Cost per passenger: 383.91 DA

Fuel Stops Required: 0 stops
(Tank capacity: 50 L)

Environmental Impact:
  CO2 Emissions: 77.96 kg
```

---

### Requirements

- Use `#include <math.h>` for `ceil()` function
- Display numbers with 2 decimal places (`.2f`)
- Compile with: `gcc -Wall homework.c -lm -o homework`
- Name your file: `road_trip.c`

---

### Submission

1. Accept GitHub Classroom assignment: [Link](https://classroom.github.com/a/SHcYpqQN)
2. Clone your repository
3. Write your code in `road_trip.c`
4. Test with the example above
5. Commit and push:

    ```bash
    git add road_trip.c
    git commit -m "Complete road trip calculator"
    git push
    ```

---
