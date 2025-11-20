# 📊 Lab 4: Homework Assignment - Student Grade Management System

## Problem: Student Grade Management System

Create a program that manages student information and calculates statistics for a class.

---

## Requirements

Your program must handle:

### Part 1: Student Data (Arrays)

- Store data for up to 50 students
- Each student has:
  - ID (integer)
  - 3 exam scores (integers, 0-100)

### Part 2: Operations

1. **Input student data**
2. **Calculate for each student:**
   - Average score
   - Grade (A, B, C, D, F)
3. **Calculate class statistics:**
   - Class average
   - Highest and lowest scores
   - Number of students per grade
4. **Search student by ID**
5. **Sort students by average** (descending)
6. **Display formatted report**

---

## Grade Scale

| Average | Grade |
|---------|-------|
| 90-100 | A |
| 80-89 | B |
| 70-79 | C |
| 60-69 | D |
| 0-59 | F |

---

## Example Output

```bash
=== Student Grade Management System ===

Enter number of students (1-50): 3

--- Enter Student Data ---

Student 1:
  ID: 101
  Exam 1 score: 85
  Exam 2 score: 90
  Exam 3 score: 88

Student 2:
  ID: 102
  Exam 1 score: 75
  Exam 2 score: 78
  Exam 3 score: 80

Student 3:
  ID: 103
  Exam 1 score: 95
  Exam 2 score: 92
  Exam 3 score: 98

=== Individual Student Reports ===

ID: 101 | Scores: 85 90 88 | Average: 87.67 | Grade: B
ID: 102 | Scores: 75 78 80 | Average: 77.67 | Grade: C
ID: 103 | Scores: 95 92 98 | Average: 95.00 | Grade: A

=== Class Statistics ===
Class Average: 86.78
Highest Score: 98 (Student ID: 103)
Lowest Score: 75 (Student ID: 102)

Grade Distribution:
  A: 1 student(s)
  B: 1 student(s)
  C: 1 student(s)
  D: 0 student(s)
  F: 0 student(s)

=== Sorted by Average (Descending) ===
1. ID: 103 | Average: 95.00 | Grade: A
2. ID: 101 | Average: 87.67 | Grade: B
3. ID: 102 | Average: 77.67 | Grade: C

--- Search Student ---
Enter student ID to search: 102
Found: ID 102 | Average: 77.67 | Grade: C
```

---

## Data Structures

```c
// Store student data in parallel arrays
int ids[50];              // Student IDs
int exam1[50];            // Exam 1 scores
int exam2[50];            // Exam 2 scores
int exam3[50];            // Exam 3 scores
float averages[50];       // Calculated averages
char grades[50];          // Letter grades (A, B, C, D, F)
```

---

## Requirements Checklist

- [ ] Input validation (scores 0-100, 1-50 students)
- [ ] Calculate averages correctly (use float!)
- [ ] Assign grades correctly
- [ ] Calculate class statistics
- [ ] Sort maintains all student data together
- [ ] Search works correctly
- [ ] Formatted output (aligned, readable)
- [ ] Handle "not found" case in search

---

## Submission

1. Accept GitHub Classroom assignment: [link](https://classroom.github.com/a/Zhlsn3sU)
2. Clone repository
3. Write code in `grade_system.c`
4. Test with all test cases
5. Commit and push:

   ```bash
   git add grade_system.c
   git commit -m "Complete grade management system"
   git push
   ```

**Start early and test thoroughly! Good luck!**