# Student Data Processing using Python and YAML

## Introduction
This project demonstrates how to use Python to process student data stored in a YAML file. The script loads student information, displays all students, and filters students based on a minimum GPA requirement.

## Files Included
1. **students.yaml** - Contains student data.
2. **app.py** - Python script to process student data.
3. **output.png** - Screenshot of the program's output.

## YAML Data Structure (students.yaml)
The student data is stored in YAML format as follows:
```yaml
students:
  - name: John Doe
    age: 20
    major: Computer Science
    gpa: 3.8
  - name: Alice Smith
    age: 22
    major: Mathematics
    gpa: 3.6
  - name: Bob Johnson
    age: 21
    major: Physics
    gpa: 3.9
```

## Python Script (app.py)
```app.py
import yaml

def load_data(file_path):
    """
    Load data from a YAML file.
    :param file_path: Path to the YAML file.
    :return: Data loaded from the YAML file.
    """
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)  # Load the data as a Python dictionary
    return data

def display_students(students):
    """
    Display information about all students.
    :param students: List of student dictionaries.
    """
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """
    Filter and display students with a GPA above the specified minimum.
    :param students: List of student dictionaries.
    :param min_gpa: Minimum GPA for filtering.
    """
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    print(f"\nStudents with GPA >= {min_gpa}:")
    
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    """Main function to load data, display students, and filter by GPA."""
    # Load the data from the YAML file
    data = load_data('students.yaml')
    students = data['students']
    
    # Display all students
    display_students(students)
    
    # Filter students by GPA
    try:
        min_gpa = float(input("\nEnter minimum GPA to filter students: "))
        filter_students_by_gpa(students, min_gpa)
    except ValueError:
        print("Invalid input! Please enter a numeric value for GPA.")

if __name__ == "__main__":
    main()
```
The script performs the following operations:
- Loads data from the YAML file.
- Displays all students.
- Filters students based on a minimum GPA input.

### Functions Explanation
1. **load_data(file_path)**
   - Reads data from a YAML file and converts it into a Python dictionary.
   - Uses `yaml.safe_load()` to safely parse the YAML content.

2. **display_students(students)**
   - Iterates through the list of students and prints their details.

3. **filter_students_by_gpa(students, min_gpa)**
   - Filters and displays students whose GPA is greater than or equal to `min_gpa`.
   - If no students match the criteria, it prints "No students found."

4. **main()**
   - Calls `load_data()` to fetch student records.
   - Calls `display_students()` to show all student records.
   - Prompts the user for a minimum GPA and calls `filter_students_by_gpa()`.
   - Handles invalid input using a `try-except` block.

## Running the Script
1. Install dependencies if not installed:
   ```sh
   pip install pyyaml
   ```
2. Run the script:
   ```sh
   python app.py
   ```

## Expected Output
```
All Students:
Name: John Doe, Age: 20, Major: Computer Science, GPA: 3.8
Name: Alice Smith, Age: 22, Major: Mathematics, GPA: 3.6
Name: Bob Johnson, Age: 21, Major: Physics, GPA: 3.9

Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: John Doe, Age: 20, Major: Computer Science, GPA: 3.8
Name: Alice Smith, Age: 22, Major: Mathematics, GPA: 3.6
Name: Bob Johnson, Age: 21, Major: Physics, GPA: 3.9
```
![image](https://github.com/user-attachments/assets/a6bca65a-1f5d-495a-b779-8dd1b6d623dc)

## Conclusion
This project showcases how to use YAML for structured data storage and Python for data processing and filtering. It can be extended to handle more complex student record management tasks.
