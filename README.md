# CPP-Assignment
2nd Year C++ Course Final Assignment. Object Oriented Programming
This is a simple Student Records Management System written in C++ using Object-Oriented Programming (OOP) principles. It allows input, storage, and processing of basic student information such as name, roll number, birthdate, gender, grades, and more. 

FUll code:
---------

---

### Your entire code formatted for GitHub README:

```markdown
```cpp
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

// Structure to store date of birth
struct DateOfBirth
{
    int day;
    int month;
    int year;
};

// Class representing individual students
class Student
{
public:
    string name;
    int rollNumber;
    DateOfBirth birthDate;
    string gender;
    vector<int> grades;

    // Input student information
    void inputStudentInfo()
    {
        cout << "Enter student name: ";
        getline(cin, name);
        cout << "Enter student roll number: ";
        cin >> rollNumber;
        cout << "Enter student birthdate (Day Month Year): ";
        cin >> birthDate.day >> birthDate.month >> birthDate.year;
        cin.ignore(); // Ignore newline left in buffer
        cout << "Enter student gender(M/F/O): ";
        getline(cin, gender);
    }

    // Display student information
    void displayStudentInfo() const
    {
        cout << "Name: " << name << endl;
        cout << "Roll Number: " << rollNumber << endl;
        cout << "Birthdate: " << birthDate.day << "/" << birthDate.month << "/" << birthDate.year << endl;
        cout << "Age based on birthdate: " << calculateAge() << endl;
        cout << "Gender: " << gender << endl;
    }

    // Input grades for courses
    void inputGrades()
    {
        int numCourses;
        cout << "Enter number of courses: ";
        cin >> numCourses;

        for (int i = 0; i < numCourses; i++)
        {
            int grade;
            cout << "Enter grade for course #" << i + 1 << ": ";
            cin >> grade;
            grades.push_back(grade);
        }
    }

    // Display GPA (Grade Point Average)
    void displayGPA() const
    {
        double total = 0;

        for (int i = 0; i < grades.size(); i++)
        {
            total += grades[i];
        }

        double gpa = grades.empty() ? 0 : total / grades.size();
        cout << "GPA: " << gpa << endl;
    }

    // Check if the student is of legal age (above 18)
    bool isLegalAge() const
    {
        return calculateAge() >= 18;
    }

private:
    // Calculate age based on birthdate and current year
    int calculateAge() const
    {
        int currentYear = 2023; // Current year for example
        return currentYear - birthDate.year;
    }
};

// Categorize students by gender
void categorizeStudents(const vector<Student>& students)
{
    for (size_t i = 0; i < students.size(); i++)
    {
        const Student& student = students[i];
        if (student.gender == "Male")
        {
            cout << student.name << " is categorized as Male." << endl;
        }
        else if (student.gender == "Female")
        {
            cout << student.name << " is categorized as Female." << endl;
        }
        else
        {
            cout << student.name << " is categorized as Other." << endl;
        }
    }
}

// Compare function for sorting students by name
bool compareByName(const Student& a, const Student& b)
{
    return a.name < b.name;
}

// Compare function for sorting students by roll number
bool compareByRollNumber(const Student& a, const Student& b)
{
    return a.rollNumber < b.rollNumber;
}

// Sort students by name
void sortStudentsByName(vector<Student>& students)
{
    sort(students.begin(), students.end(), compareByName);
}

// Sort students by roll number
void sortStudentsByRollNumber(vector<Student>& students)
{
    sort(students.begin(), students.end(), compareByRollNumber);
}

// Search for a student by roll number and display details
void searchStudentByRollNumber(const vector<Student>& students, int rollNumber)
{
    for (size_t i = 0; i < students.size(); i++)
    {
        const Student& student = students[i];
        if (student.rollNumber == rollNumber)
        {
            student.displayStudentInfo();
            return; // Exit the loop since the student is found
        }
    }
    cout << "Student with roll number " << rollNumber << " not found." << endl;
}

int main()
{
    vector<Student> students;

    int numStudents;
    cout << "Enter the number of students to register: ";
    cin >> numStudents;
    cin.ignore(); // Ignore newline left in buffer

    // Register students
    for (int i = 0; i < numStudents; i++)
    {
        Student s;
        cout << "Enter details for student #" << i + 1 << ":" << endl;
        s.inputStudentInfo();
        students.push_back(s);
    }

    // Display student information
    for (size_t i = 0; i < students.size(); i++)
    {
        cout << "Student #" << i + 1 << " details:" << endl;
        students[i].displayStudentInfo();
    }

    // Input grades
    for (size_t i = 0; i < students.size(); i++)
    {
        students[i].inputGrades();
    }

    // Display GPA
    for (size_t i = 0; i < students.size(); i++)
    {
        students[i].displayGPA();
    }

    // Determine whether a student is of legal age
    for (size_t i = 0; i < students.size(); i++)
    {
        if (students[i].isLegalAge())
        {
            cout << students[i].name << " is of legal age." << endl;
        }
        else
        {
            cout << students[i].name << " is not of legal age." << endl;
        }
    }

    // Categorize students by gender
    categorizeStudents(students);

    // Sort by name or roll number
    sortStudentsByName(students);
    sortStudentsByRollNumber(students);

    // Search for a student by roll number
    int rollNumberToSearch;
    cout << "Enter roll number to search: ";
    cin >> rollNumberToSearch;
    searchStudentByRollNumber(students, rollNumberToSearch);

    return 0;
}
arch);

    return 0;
}
