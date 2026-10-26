# binary search
#include <iostream>
#include <cstdlib>   // for realloc()
using namespace std;
struct Student
{
    int id;
    char name[50];
    float cgpa;
};
int main()
{
    Student *s = NULL;
    int n;
    cout << "Enter number of students: ";
    cin >> n;
    // Allocate memory for n students
    s = (Student *)realloc(s, n * sizeof(Student));
    // Input student details
    for (int i = 0; i < n; i++)
    {
        cout << "\nEnter Student ID: ";
        cin >> s[i].id;
        cout << "Enter Name: ";
        cin >> s[i].name;
        cout << "Enter CGPA: ";
        cin >> s[i].cgpa;
    }
    // Sort by ID (required for Binary Search)
    for (int i = 0; i < n - 1; i++)
    {
        for (int j = i + 1; j < n; j++)
        {
            if (s[i].id > s[j].id)
            {
                Student temp = s[i];
                s[i] = s[j];
                s[j] = temp;
            }
        }
    }
    // Binary Search
    int searchId;
    cout << "\nEnter Student ID to Search: ";
    cin >> searchId;
    int low = 0, high = n - 1, mid;
    bool found = false;
    while (low <= high)
    {
        mid = (low + high) / 2;
        if (s[mid].id == searchId)
        {
            cout << "\nStudent Found!" << endl;
            cout << "ID: " << s[mid].id << endl;
            cout << "Name: " << s[mid].name << endl;
            cout << "CGPA: " << s[mid].cgpa << endl;
            found = true;
            break;
        }
        else if (searchId < s[mid].id)
        {
            high = mid - 1;
        }
        else
        {
            low = mid + 1;
        }
    }
    if (!found)
    {
        cout << "\nStudent Not Found!" << endl;
         }
    free(s);
    return 0;
    }


#Linear search
#include <iostream>
#include <string>
using namespace std;
struct Student
{
    int id;
    string name;
    float cgpa;
};
int main()
{
    int n, searchId;
    cout << "Enter number of students: ";
    cin >> n;
    // Dynamic memory allocation
    Student *s = new Student[n];
    // Input student details
    for (int i = 0; i < n; i++)
    {
        cout << "\nEnter details of Student " << i + 1 << endl;
        cout << "Enter ID: ";
        cin >> s[i].id;
        cin.ignore();
        cout << "Enter Name: ";
        getline(cin, s[i].name);
        cout << "Enter CGPA: ";
        cin >> s[i].cgpa;
    }
    // Search by ID
    cout << "\nEnter Student ID to search: ";
    cin >> searchId;
    bool found = false;
    // Linear Search
    for (int i = 0; i < n; i++)
    {
        if (s[i].id == searchId)
        {
            cout << "\nStudent Found!" << endl;
            cout << "ID   : " << s[i].id << endl;
            cout << "Name : " << s[i].name << endl;
            cout << "CGPA : " << s[i].cgpa << endl;
            found = true;
            break;
        }
    }
    if (!found)
    {
        cout << "\nStudent Not Found!" << endl;
    }
    // Free allocated memory
    delete[] s;
    return 0;
    }



  #sorting
  #include <iostream>
#include <string>
using namespace std;
struct Student
{
    int id;
    string name;
    float cgpa;
};
int main()
{
    int n;
    cout << "Enter number of students: ";
    cin >> n;
    // Dynamic memory allocation
    Student *s = new Student[n];
    // Input student details
    for (int i = 0; i < n; i++)
    {
        cout << "\nStudent " << i + 1 << endl;
        cout << "Enter ID: ";
        cin >> s[i].id;
        cout << "Enter Name: ";
        cin >> s[i].name;
        cout << "Enter CGPA: ";
        cin >> s[i].cgpa;
    }
    int choice;
    cout << "\n1. Sort by Name (Alphabetical)";
    cout << "\n2. Sort by CGPA (Descending)";
    cout << "\nEnter your choice: ";
    cin >> choice;
    // Bubble Sort
    for (int i = 0; i < n - 1; i++)
    {
        for (int j = 0; j < n - i - 1; j++)
        {
            bool swapNeeded = false;
            if (choice == 1)
            {
                if (s[j].name > s[j + 1].name)
                    swapNeeded = true;
            }
            else if (choice == 2)
            {
                if (s[j].cgpa < s[j + 1].cgpa)
                    swapNeeded = true;
            }
            if (swapNeeded)
            {
                Student temp = s[j];
                s[j] = s[j + 1];
                s[j + 1] = temp;
            }
        }
    }
    // Display sorted records
    cout << "\nSorted Student Records:\n";
    cout << "\nID\tName\tCGPA\n";
    for (int i = 0; i < n; i++)
    {
        cout << s[i].id << "\t"
             << s[i].name << "\t"
             << s[i].cgpa << endl;
    }
    delete[] s; // Free memory
    return 0;
    }


    
    }
    free(s);
    return 0
