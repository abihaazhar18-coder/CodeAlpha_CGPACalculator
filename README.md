#include "stdafx.h"
#include <iostream>
#include <iomanip>
#include <string>

using namespace std;

struct Course
{
    string name;
    string grade;
    int creditHours;
    double gradePoint;
};

double getGradePoint(string grade)
{
    if (grade == "A+" || grade == "A")
        return 4.0;
    else if (grade == "A-")
        return 3.7;
    else if (grade == "B+")
        return 3.3;
    else if (grade == "B")
        return 3.0;
    else if (grade == "B-")
        return 2.7;
    else if (grade == "C+")
        return 2.3;
    else if (grade == "C")
        return 2.0;
    else if (grade == "C-")
        return 1.7;
    else if (grade == "D")
        return 1.0;
    else
        return 0.0;
}

int main()
{
    int n;

    cout << "==============================" << endl;
    cout << "      CGPA CALCULATOR" << endl;
    cout << "==============================" << endl;

    cout << "\nEnter Number of Courses: ";
    cin >> n;

    Course* courses = new Course[n];

    double totalCredits = 0;
    double totalGradePoints = 0;

    for (int i = 0; i < n; i++)
    {
        cout << "\nCourse " << i + 1 << endl;

        cout << "Course Name: ";
        cin.ignore();
        getline(cin, courses[i].name);

        cout << "Grade (A+, A, A-, B+, B, B-, C+, C, C-, D, F): ";
        cin >> courses[i].grade;

        cout << "Credit Hours: ";
        cin >> courses[i].creditHours;

        courses[i].gradePoint = getGradePoint(courses[i].grade);

        totalCredits += courses[i].creditHours;
        totalGradePoints += courses[i].gradePoint * courses[i].creditHours;
    }

    double cgpa = totalGradePoints / totalCredits;

    cout << "\n===============================================";
    cout << "\n              COURSE DETAILS";
    cout << "\n===============================================\n";

    cout << left << setw(20) << "Course"
         << setw(10) << "Grade"
         << setw(10) << "Credits"
         << setw(12) << "Point"
         << endl;

    cout << "-------------------------------------------------\n";

    for (int i = 0; i < n; i++)
    {
        cout << left << setw(20) << courses[i].name
             << setw(10) << courses[i].grade
             << setw(10) << courses[i].creditHours
             << setw(12) << courses[i].gradePoint
             << endl;
    }

    cout << "\nTotal Credit Hours : " << totalCredits << endl;
    cout << "Total Grade Points : " << totalGradePoints << endl;

    cout << fixed << setprecision(2);
    cout << "\nFinal CGPA : " << cgpa << endl;

    cout << "\nThank You!" << endl;
	delete[] courses;
	system ("pause");
    return 0;
}

