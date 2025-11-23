#include <stdio.h>

struct Employee {
    int id;
    char name[50];
    float salary;
};

int main() {
    struct Employee emp[20], temp;
    int n, i, j;

    printf("Enter number of employees: ");
    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        printf("\nEnter details of employee %d\n", i + 1);

        printf("Enter employee ID: ");
        scanf("%d", &emp[i].id);

        printf("Enter employee Name: ");
        scanf(" %[^\n]", emp[i].name);

        printf("Enter employee Salary: ");
        scanf("%f", &emp[i].salary);
    }

    // Sort by salary in descending order
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (emp[j].salary < emp[j + 1].salary) {
                temp = emp[j];
                emp[j] = emp[j + 1];
                emp[j + 1] = temp;
            }
        }
    }

    printf("\nEmployees sorted by salary (Descending Order):\n");
    printf("--------------------------------------------------------\n");
    printf("%-5s %-20s %-10s\n", "ID", "Name", "Salary");
    printf("--------------------------------------------------------\n");

    for (i = 0; i < n; i++) {
        printf("%-5d %-20s %-10.2f\n", emp[i].id, emp[i].name, emp[i].salary);
    }

    return 0;
}
