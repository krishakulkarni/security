#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 100
#define MAX_TEACHERS 50

// Structure for student
struct Student {
    int id;
    char name[50];
    int age;
    char department[50];
};

// Structure for teacher
struct Teacher {
    int id;
    char name[50];
    char subject[50];
    int experience;
};

// Function to add a student
void addStudent(struct Student students[], int *studentCount) {
    if (*studentCount >= MAX_STUDENTS) {
        printf("Student limit reached.\n");
        return;
    }

    printf("Enter student ID: ");
    scanf("%d", &students[*studentCount].id);
    printf("Enter student name: ");
    scanf(" %[^\n]%*c", students[*studentCount].name);
    printf("Enter student age: ");
    scanf("%d", &students[*studentCount].age);
    printf("Enter student department: ");
    scanf(" %[^\n]%*c", students[*studentCount].department);

    (*studentCount)++;
    printf("Student added successfully.\n");
}

// Function to add a teacher
void addTeacher(struct Teacher teachers[], int *teacherCount) {
    if (*teacherCount >= MAX_TEACHERS) {
        printf("Teacher limit reached.\n");
        return;
    }

    printf("Enter teacher ID: ");
    scanf("%d", &teachers[*teacherCount].id);
    printf("Enter teacher name: ");
    scanf(" %[^\n]%*c", teachers[*teacherCount].name);
    printf("Enter subject: ");
    scanf(" %[^\n]%*c", teachers[*teacherCount].subject);
    printf("Enter years of experience: ");
    scanf("%d", &teachers[*teacherCount].experience);

    (*teacherCount)++;
    printf("Teacher added successfully.\n");
}

// Function to display student details
void displayStudents(struct Student students[], int studentCount) {
    if (studentCount == 0) {
        printf("No students to display.\n");
        return;
    }

    printf("Student Details:\n");
    for (int i = 0; i < studentCount; i++) {
        printf("ID: %d, Name: %s, Age: %d, Department: %s\n",
               students[i].id, students[i].name, students[i].age, students[i].department);
    }
}

// Function to display teacher details
void displayTeachers(struct Teacher teachers[], int teacherCount) {
    if (teacherCount == 0) {
        printf("No teachers to display.\n");
        return;
    }

    printf("Teacher Details:\n");
    for (int i = 0; i < teacherCount; i++) {
        printf("ID: %d, Name: %s, Subject: %s, Experience: %d years\n",
               teachers[i].id, teachers[i].name, teachers[i].subject, teachers[i].experience);
    }
}

// Function to search student by ID
void searchStudent(struct Student students[], int studentCount, int id) {
    for (int i = 0; i < studentCount; i++) {
        if (students[i].id == id) {
            printf("Student found: ID: %d, Name: %s, Age: %d, Department: %s\n",
                   students[i].id, students[i].name, students[i].age, students[i].department);
            return;
        }
    }
    printf("Student with ID %d not found.\n", id);
}

// Function to search teacher by ID
void searchTeacher(struct Teacher teachers[], int teacherCount, int id) {
    for (int i = 0; i < teacherCount; i++) {
        if (teachers[i].id == id) {
            printf("Teacher found: ID: %d, Name: %s, Subject: %s, Experience: %d years\n",
                   teachers[i].id, teachers[i].name, teachers[i].subject, teachers[i].experience);
            return;
        }
    }
    printf("Teacher with ID %d not found.\n", id);
}

int main() {
    struct Student students[MAX_STUDENTS];
    struct Teacher teachers[MAX_TEACHERS];
    int studentCount = 0;
    int teacherCount = 0;
    int choice, id;

    while (1) {
        printf("\n--- Campus Management System ---\n");
        printf("1. Add Student\n");
        printf("2. Add Teacher\n");
        printf("3. Display Students\n");
        printf("4. Display Teachers\n");
        printf("5. Search Student by ID\n");
        printf("6. Search Teacher by ID\n");
        printf("7. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addStudent(students, &studentCount);
                break;
            case 2:
                addTeacher(teachers, &teacherCount);
                break;
            case 3:
                displayStudents(students, studentCount);
                break;
            case 4:
                displayTeachers(teachers, teacherCount);
                break;
            case 5:
                printf("Enter student ID to search: ");
                scanf("%d", &id);
                searchStudent(students, studentCount, id);
                break;
            case 6:
                printf("Enter teacher ID to search: ");
                scanf("%d", &id);
                searchTeacher(teachers, teacherCount, id);
                break;
            case 7:
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice! Please try again.\n");
        }
    }

    return 0;
}
