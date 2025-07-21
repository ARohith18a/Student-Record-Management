#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int i = 0;

struct studentInfo
{
    char firstName[20];
    char lastName[20];
    int rollNumber;
    float CGPA;
    int courseId[10];
} st[500];

// Function prototypes
void addStudent();
void findByRollNumber();
void findByName();
void findRegisteredStudent();
void totalCount();
void deleteStudent();
void updateStudent();

// Main function
int main()
{
    // Example usage (you can build a menu here later)
    addStudent();
    totalCount();
    return 0;
}

// Function implementations go below
void addStudent()
{
    printf("Add the Student's Details\n\n");
    printf("Enter the first name of the student: ");
    scanf("%s", st[i].firstName);
    printf("Enter the last name of the student: ");
    scanf("%s", st[i].lastName);
    printf("Enter the roll number of the student: ");
    scanf("%d", &st[i].rollNumber);
    printf("Enter the CGPA of the student: ");
    scanf("%f", &st[i].CGPA);
    printf("Enter the course IDs of the student (5 courses): ");
    for (int j = 0; j < 5; j++)
    {
        scanf("%d", &st[i].courseId[j]);
    }
    i++;
}

void findByRollNumber()
{
    int temp;
    printf("Enter the roll number of the student: ");
    scanf("%d", &temp);
    int found = 0;
    for (int j = 0; j < i; j++)
    {
        if (temp == st[j].rollNumber)
        {
            printf("The student's details are:\n");
            printf("First name: %s\n", st[j].firstName);
            printf("Last name: %s\n", st[j].lastName);
            printf("CGPA: %.2f\n", st[j].CGPA);
            printf("Course IDs: ");
            for (int k = 0; k < 5; k++)
            {
                printf("%d ", st[j].courseId[k]);
            }
            printf("\n");
            found = 1;
            break;
        }
    }
    if (!found)
    {
        printf("Student with roll number %d not found.\n", temp);
    }
}

void findByName()
{
    char tempName[20];
    printf("Enter the first name of the student: ");
    scanf("%s", tempName);
    int found = 0;
    for (int j = 0; j < i; j++)
    {
        if (strcmp(tempName, st[j].firstName) == 0)
        {
            printf("The student's details are:\n");
            printf("First name: %s\n", st[j].firstName);
            printf("Last name: %s\n", st[j].lastName);
            printf("Roll Number: %d\n", st[j].rollNumber);
            printf("CGPA: %.2f\n", st[j].CGPA);
            printf("Course IDs: ");
            for (int k = 0; k < 5; k++)
            {
                printf("%d ", st[j].courseId[k]);
            }
            printf("\n-------------------\n");
            found = 1;
        }
    }
    if (!found)
    {
        printf("No student found with first name %s.\n", tempName);
    }
}

void findRegisteredStudent()
{
    int temp;
    printf("Enter the course ID: ");
    scanf("%d", &temp);
    int found = 0;
    for (int j = 0; j < i; j++)
    {
        for (int d = 0; d < 5; d++)
        {
            if (temp == st[j].courseId[d])
            {
                printf("Student details:\n");
                printf("First name: %s\n", st[j].firstName);
                printf("Last name: %s\n", st[j].lastName);
                printf("Roll Number: %d\n", st[j].rollNumber);
                printf("CGPA: %.2f\n", st[j].CGPA);
                printf("Course IDs: ");
                for (int k = 0; k < 5; k++)
                {
                    printf("%d ", st[j].courseId[k]);
                }
                printf("\n-------------------\n");
                found = 1;
                break;
            }
        }
    }
    if (!found)
    {
        printf("No students found enrolled in course ID %d.\n", temp);
    }
}

void totalCount()
{
    printf("The total number of students currently in the system is %d\n", i);
}

void deleteStudent()
{
    int temp;
    printf("Enter the roll number of the student: ");
    scanf("%d", &temp);
    int found = 0;
    for (int j = 0; j < i; j++)
    {
        if (temp == st[j].rollNumber)
        {
            for (int k = j; k < i - 1; k++)
            {
                st[k] = st[k + 1];
            }
            i--;
            found = 1;
            printf("Student with roll number %d deleted successfully.\n", temp);
            break;
        }
    }
    if (!found)
    {
        printf("Student with roll number %d not found.\n", temp);
    }
}

void updateStudent()
{
    int temp;
    printf("Enter the roll number of the student to update: ");
    scanf("%d", &temp);
    int found = 0;
    for (int j = 0; j < i; j++)
    {
        if (temp == st[j].rollNumber)
        {
            printf("1. First Name\n2. Last Name\n3. Roll Number\n4. CGPA\n5. Courses\n");
            int choice;
            scanf("%d", &choice);
            switch (choice)
            {
            case 1:
                printf("Enter the updated first name : ");
                scanf("%s", st[j].firstName);
                break;
            case 2:
                printf("Enter the updated last name : ");
                scanf("%s", st[j].lastName);
                break;
            case 3:
                printf("Enter the updated roll number : ");
                scanf("%d", &st[j].rollNumber);
                break;
            case 4:
                printf("Enter the updated CGPA : ");
                scanf("%f", &st[j].CGPA);
                break;
            case 5:
                printf("Enter the updated course IDs (5 courses): ");
                for (int k = 0; k < 5; k++)
                {
                    scanf("%d", &st[j].courseId[k]);
                }
                break;
            }
            found = 1;
        }
    }
    if (!found)
    {
        printf("Student with roll number %d not found.\n", temp);
    }
}
