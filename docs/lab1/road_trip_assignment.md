# Road Trip Budget Calculator — Assignment + Solution

## Assignment (Exercise)

Create a program that calculates fuel consumption, costs, and trip details for a journey. This exercise reinforces Lab 1 concepts: variables, arithmetic, I/O, and simple math library usage.

Inputs (ask the user for these 5 values):

1. Distance to travel (km)
2. Vehicle fuel consumption (L/100km)
3. Fuel price per liter (DA)
4. Average speed (km/h)
5. Number of passengers

Required outputs (compute & display):

- Total fuel needed (liters)
- Total fuel cost (DA)
- Cost per passenger (DA)
- Trip duration (hours and minutes, formatted H:MM)
- Cost per kilometer (DA/km)
- Number of fuel stops (assume tank capacity = 50 L)
- CO₂ emissions (kg) (use 2.31 kg CO₂ per liter)

Formatting rules:

- Show monetary and measured values with 2 decimal places
- Show minutes as two digits (e.g., 4:05)
- If stops calculation results in a negative number, show 0

---

## Solution (C)

<details><summary>Click to show the C solution</summary>

```c
#include <stdio.h>
#include <math.h>

int main(void) {
    // Constants
    const double TANK_CAPACITY = 50.0;     // liters
    const double CO2_PER_LITER = 2.31;     // kg CO2 per liter

    // Inputs
    double distance_km;       // total trip distance in kilometers
    double consumption_l_per_100km; // liters per 100 km
    double price_per_liter;   // currency per liter
    double avg_speed_kmh;     // average speed in km/h
    int passengers;           // number of passengers

    // Read user input
    printf("Enter distance to travel (km): ");
    if (scanf("%lf", &distance_km) != 1) return 1;

    printf("Enter vehicle fuel consumption (L/100km): ");
    if (scanf("%lf", &consumption_l_per_100km) != 1) return 1;

    printf("Enter fuel price per liter (DA): ");
    if (scanf("%lf", &price_per_liter) != 1) return 1;

    printf("Enter average speed (km/h): ");
    if (scanf("%lf", &avg_speed_kmh) != 1) return 1;

    printf("Enter number of passengers: ");
    if (scanf("%d", &passengers) != 1) return 1;

    // Basic defensive checks
    if (distance_km < 0) distance_km = 0;
    if (consumption_l_per_100km < 0) consumption_l_per_100km = 0;
    if (price_per_liter < 0) price_per_liter = 0;
    if (avg_speed_kmh <= 0) avg_speed_kmh = 1; // avoid division by zero
    if (passengers <= 0) passengers = 1; // avoid division by zero

    // Calculations
    double total_fuel_l = (distance_km / 100.0) * consumption_l_per_100km;
    double total_cost = total_fuel_l * price_per_liter;
    double cost_per_passenger = total_cost / (double)passengers;
    double cost_per_km = (distance_km > 0.0) ? (total_cost / distance_km) : 0.0;

    // Time: compute total seconds to avoid rounding issues for minutes
    double total_hours = distance_km / avg_speed_kmh; // e.g., 4.0909...
    long total_seconds = (long) round(total_hours * 3600.0);
    int hours = (int)(total_seconds / 3600);
    int minutes = (int)((total_seconds % 3600) / 60);

    // Fuel stops
    int stops = (int)ceil(total_fuel_l / TANK_CAPACITY) - 1; // subtract 1: start with full tank
    if (stops < 0) stops = 0;

    // CO2 emissions
    double co2_kg = total_fuel_l * CO2_PER_LITER;

    // Output
    printf("\n=== Trip Calculation ===\n");
    printf("Distance: %.0f km\n", distance_km);
    printf("Estimated Duration: %dh %02dmin\n\n", hours, minutes);

    printf("Fuel Consumption:\n");
    printf("  Total Fuel Needed: %.2f L\n", total_fuel_l);
    printf("  Total Cost: %.2f DA\n", total_cost);
    printf("  Cost per km: %.2f DA/km\n", cost_per_km);
    printf("  Cost per passenger: %.2f DA\n\n", cost_per_passenger);

    printf("Fuel Stops Required: %d stop(s)\n", stops);
    printf("(Tank capacity: %.0f L)\n\n", TANK_CAPACITY);

    printf("Environmental Impact:\n");
    printf("  CO2 Emissions: %.2f kg\n", co2_kg);

    return 0;
}
```

</details>

---
