# Ex.No. 6 – AI-Assisted Programming and Debugging

## Date: 02-09-2026

## Register No.: 212224110047

## Aim

To write and implement programs using AI-assisted programming tools, identify and debug errors, optimize the generated code, analyse its complexity, generate unit tests, and compare manual programming with AI-assisted programming.


## AI Tools Required

- ChatGPT
- Google Gemini
- GitHub Copilot
- Python
- Any suitable IDE or code editor



# 1. Experiment Overview

AI-assisted programming uses Artificial Intelligence tools to support software development activities such as:

- Code generation
- Bug identification
- Debugging
- Code optimization
- Complexity analysis
- Unit-test generation
- Code explanation
- Documentation

In this experiment, multiple AI tools are used to generate solutions for the same programming problem. The generated programs are then compared based on correctness, code quality, readability, efficiency, maintainability, and performance.

The experiment also compares **manual coding** with **AI-assisted coding**.


# 2. Selected Application

## Application: Student Result Management System

The selected application is a simple **Student Result Management System**.

The system accepts student marks, calculates the total and average, determines the grade, and displays the result.

### Functional Requirements

1. Accept student name.
2. Accept marks for multiple subjects.
3. Calculate total marks.
4. Calculate average marks.
5. Determine grade.
6. Display the result.
7. Validate marks entered by the user.


# 3. Persona Pattern

The following persona prompt was used with the AI tools:

> **"Act as an experienced software engineer and Python developer. Develop clean, efficient, readable and maintainable code for a Student Result Management System. Follow good programming practices, include input validation, meaningful variable names and appropriate error handling. Explain the code and provide test cases."**

The same requirement was provided to multiple AI tools to compare their generated solutions.


# 4. Python Code Generated Using AI

```python
def calculate_result(name, marks):
    if not marks:
        raise ValueError("Marks list cannot be empty.")

    for mark in marks:
        if mark < 0 or mark > 100:
            raise ValueError("Marks must be between 0 and 100.")

    total = sum(marks)
    average = total / len(marks)

    if average >= 90:
        grade = "A+"
    elif average >= 80:
        grade = "A"
    elif average >= 70:
        grade = "B"
    elif average >= 60:
        grade = "C"
    elif average >= 50:
        grade = "D"
    else:
        grade = "F"

    return {
        "name": name,
        "total": total,
        "average": average,
        "grade": grade
    }


name = input("Enter student name: ")

marks = []
subjects = int(input("Enter number of subjects: "))

for i in range(subjects):
    mark = float(input(f"Enter marks for subject {i + 1}: "))
    marks.append(mark)

try:
    result = calculate_result(name, marks)

    print("\n--- Student Result ---")
    print("Name:", result["name"])
    print("Total:", result["total"])
    print("Average:", result["average"])
    print("Grade:", result["grade"])

except ValueError as error:
    print("Error:", error)
```

---

# 5. C Code Generated Using AI

```c
#include <stdio.h>

int main() {
    int n;
    float mark, total = 0, average;

    printf("Enter number of subjects: ");
    scanf("%d", &n);

    if (n <= 0) {
        printf("Invalid number of subjects.\n");
        return 1;
    }

    for (int i = 0; i < n; i++) {
        printf("Enter marks for subject %d: ", i + 1);
        scanf("%f", &mark);

        if (mark < 0 || mark > 100) {
            printf("Invalid marks.\n");
            return 1;
        }

        total += mark;
    }

    average = total / n;

    printf("\nTotal = %.2f\n", total);
    printf("Average = %.2f\n", average);

    if (average >= 90)
        printf("Grade = A+\n");
    else if (average >= 80)
        printf("Grade = A\n");
    else if (average >= 70)
        printf("Grade = B\n");
    else if (average >= 60)
        printf("Grade = C\n");
    else if (average >= 50)
        printf("Grade = D\n");
    else
        printf("Grade = F\n");

    return 0;
}
```


# 6. Java Code Generated Using AI

```java
import java.util.Scanner;

public class StudentResult {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter student name: ");
        String name = scanner.nextLine();

        System.out.print("Enter number of subjects: ");
        int subjects = scanner.nextInt();

        if (subjects <= 0) {
            System.out.println("Invalid number of subjects.");
            return;
        }

        double total = 0;

        for (int i = 1; i <= subjects; i++) {
            System.out.print("Enter marks for subject " + i + ": ");
            double mark = scanner.nextDouble();

            if (mark < 0 || mark > 100) {
                System.out.println("Invalid marks.");
                return;
            }

            total += mark;
        }

        double average = total / subjects;
        String grade;

        if (average >= 90)
            grade = "A+";
        else if (average >= 80)
            grade = "A";
        else if (average >= 70)
            grade = "B";
        else if (average >= 60)
            grade = "C";
        else if (average >= 50)
            grade = "D";
        else
            grade = "F";

        System.out.println("\n--- Student Result ---");
        System.out.println("Name: " + name);
        System.out.println("Total: " + total);
        System.out.println("Average: " + average);
        System.out.println("Grade: " + grade);

        scanner.close();
    }
}
```

# 7. AI-Based Bug Identification

A deliberately incorrect version of the Python code was provided to the AI tools:

```python
def calculate_average(marks):
    total = 0

    for mark in marks:
        total += mark

    average = total / len(marks)

    if average > 90:
        grade = "A+"
    elif average > 80:
        grade = "A"
    elif average > 70:
        grade = "B"
    else:
        grade = "C"

    return average, grade
```

### Identified Problems

The AI tools identified the following issues:

1. Empty lists can cause a `ZeroDivisionError`.
2. Boundary conditions such as exactly 90, 80 and 70 are not handled as expected.
3. Marks are not validated.
4. Marks greater than 100 or less than 0 are accepted.
5. The grading system is incomplete.
6. The function does not provide meaningful error handling.


# 8. Debugged Code

```python
def calculate_average(marks):
    if not marks:
        raise ValueError("Marks list cannot be empty.")

    if any(mark < 0 or mark > 100 for mark in marks):
        raise ValueError("Marks must be between 0 and 100.")

    total = sum(marks)
    average = total / len(marks)

    if average >= 90:
        grade = "A+"
    elif average >= 80:
        grade = "A"
    elif average >= 70:
        grade = "B"
    elif average >= 60:
        grade = "C"
    elif average >= 50:
        grade = "D"
    else:
        grade = "F"

    return average, grade
```

---

# 9. Code Optimization

The original implementation manually calculated the total:

```python
total = 0

for mark in marks:
    total += mark
```

The optimized implementation uses Python's built-in `sum()` function:

```python
total = sum(marks)
```

This makes the program:

- Shorter
- Easier to read
- Easier to maintain
- Less repetitive

The validation can also be simplified using:

```python
if any(mark < 0 or mark > 100 for mark in marks):
    raise ValueError("Marks must be between 0 and 100.")
```


# 10. Complexity Analysis

For `n` subjects:

### Time Complexity

The marks are traversed to calculate the total.

```text
Time Complexity = O(n)
```

### Space Complexity

The list of marks requires storage proportional to the number of subjects.

```text
Space Complexity = O(n)
```

If the marks are processed one at a time without storing the entire list, auxiliary space can be reduced to:

```text
O(1)
```

# 11. Unit Test Generation

The following unit tests can be generated using AI assistance:

```python
import unittest

def calculate_average(marks):
    if not marks:
        raise ValueError("Marks list cannot be empty.")

    if any(mark < 0 or mark > 100 for mark in marks):
        raise ValueError("Marks must be between 0 and 100.")

    total = sum(marks)
    average = total / len(marks)

    if average >= 90:
        grade = "A+"
    elif average >= 80:
        grade = "A"
    elif average >= 70:
        grade = "B"
    elif average >= 60:
        grade = "C"
    elif average >= 50:
        grade = "D"
    else:
        grade = "F"

    return average, grade


class TestStudentResult(unittest.TestCase):

    def test_a_plus_grade(self):
        average, grade = calculate_average([95, 92, 96])
        self.assertEqual(grade, "A+")

    def test_a_grade(self):
        average, grade = calculate_average([85, 82, 86])
        self.assertEqual(grade, "A")

    def test_b_grade(self):
        average, grade = calculate_average([75, 72, 76])
        self.assertEqual(grade, "B")

    def test_invalid_marks(self):
        with self.assertRaises(ValueError):
            calculate_average([105, 80, 90])

    def test_empty_marks(self):
        with self.assertRaises(ValueError):
            calculate_average([])


if __name__ == "__main__":
    unittest.main()
```


# 12. Comparison of Multiple AI Tools

| Evaluation Criteria | ChatGPT | Google Gemini | GitHub Copilot |
|---|---|---|---|
| Code Generation | Excellent | Very Good | Excellent |
| Code Accuracy | Excellent | Very Good | Excellent |
| Bug Detection | Excellent | Very Good | Very Good |
| Code Explanation | Excellent | Excellent | Good |
| Optimization | Excellent | Very Good | Excellent |
| Unit Test Generation | Excellent | Very Good | Excellent |
| Readability | Excellent | Very Good | Very Good |
| Ease of Use | Excellent | Excellent | Excellent |
| Overall Performance | Excellent | Very Good | Excellent |


# 13. Manual Coding vs AI-Assisted Coding

| Feature | Manual Coding | AI-Assisted Coding |
|---|---|---|
| Development Speed | Moderate | High |
| Code Generation | Requires more time | Very fast |
| Debugging | Manual | AI-assisted |
| Error Detection | Depends on programmer | Faster identification |
| Code Explanation | Programmer dependent | Automatically generated |
| Optimization | Manual analysis | AI suggestions available |
| Unit Tests | Must be written manually | Can be generated automatically |
| Learning | Strong conceptual learning | Requires verification |
| Control | High | High with human review |
| Productivity | Moderate | High |


# 14. Code Quality Analysis

The AI-generated code was evaluated based on the following criteria:

| Criterion | Evaluation |
|---|---|
| Correctness | High |
| Readability | High |
| Maintainability | High |
| Efficiency | High |
| Error Handling | Good |
| Modularity | Good |
| Documentation | Good |
| Testing | High |
| Performance | Good |
| Overall Quality | High |

AI-assisted programming reduced the time required for writing repetitive code and identifying common programming errors. However, the generated code still required human verification because AI may produce incorrect assumptions, inefficient implementations, or logic errors.


# 15. Advantages of AI-Assisted Programming

1. Faster code generation.
2. Helps identify programming errors.
3. Provides explanations for complex code.
4. Generates unit tests automatically.
5. Suggests code optimization techniques.
6. Supports multiple programming languages.
7. Improves developer productivity.
8. Helps beginners understand programming concepts.
9. Reduces repetitive coding work.
10. Assists in documentation generation.


# 16. Limitations of AI-Assisted Programming

1. AI-generated code may contain errors.
2. Generated solutions must be tested before use.
3. AI may misunderstand project requirements.
4. Security vulnerabilities may be introduced.
5. Overdependence on AI can reduce programming practice.
6. Generated code may not always be optimal.
7. Human review is required for critical applications.
8. AI may use outdated or inappropriate programming approaches.


# 17. Key Observations

- Multiple AI tools can generate working programs from the same requirement.
- Different AI tools may produce different programming approaches.
- AI is particularly useful for repetitive coding tasks.
- AI-assisted debugging can reduce development time.
- AI-generated unit tests improve test coverage.
- Human verification remains essential.
- Combining programmer knowledge with AI assistance produces better results than blindly accepting generated code.
- AI-assisted programming improves productivity while the programmer remains responsible for correctness and security.


# 18. Final Prompt Used

> **"Act as a senior software engineer and Python developer. Develop a clean, modular and efficient Student Result Management System. Generate the complete Python implementation with proper input validation and exception handling. Then inspect the code for bugs, optimize it, explain its time and space complexity, generate comprehensive unit tests, and identify possible security, reliability and maintainability issues. Finally, provide recommendations for improving the code quality."**


# Conclusion

AI-assisted programming provides significant support throughout the software-development lifecycle. In this experiment, multiple AI tools were used for code generation, debugging, optimization, complexity analysis and unit-test generation.

The comparison showed that AI-assisted programming can significantly reduce development time and improve productivity. However, AI-generated code cannot be accepted without testing and human verification.

Therefore, the most effective approach is to combine **programmer expertise with AI assistance**, where AI performs repetitive and supportive tasks while the programmer validates the logic, correctness, security and overall quality of the solution.

# Result

**The corresponding prompt was executed successfully. Python, C and Java programs were generated using AI tools. The generated code was analysed, bugs were identified and corrected, the code was optimized, complexity was evaluated, and unit tests were generated. AI-assisted programming was found to improve development speed, debugging efficiency and code productivity compared with manual coding.**
