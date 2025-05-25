# Ex-1 IMPLEMENTATION-OF-SYMBOL-TABLE
# Register Number :Tarunika D
# Date : 10.04.2025
# AIM :
## To write a C program to implement a symbol table.
# ALGORITHM
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol and memory address are inserted into the symbol table.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and the symbol table has been checked for the corresponding variable, the variable along with its address is displayed as a result.
8.	Stop the program. 
# PROGRAM
```
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *add[26]; // For 26 possible variables a-z
    char b[MAX_EXPRESSION_SIZE], d[26], c, srch;

    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; // Null terminate the string
    n = i;

    printf("\nGiven Expression: %s\n", b);

    printf("\nSymbol Table\n");
    printf("Symbol\tAddress\t\tType\n");

    for (j = 0; j < n; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) {
            int alreadyExists = 0;

            // Check for duplicates
            for (int k = 0; k < x; k++) {
                if (d[k] == c) {
                    alreadyExists = 1;
                    break;
                }
            }

            if (!alreadyExists) {
                void *p = malloc(sizeof(char));
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }

    // Clean input buffer
    while ((getchar()) != '\n');

    printf("\nEnter the symbol to be searched: ");
    srch = getchar();

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c @ Address %p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }

    if (!flag)
        printf("Symbol Not Found\n");

    // Free memory
    for (i = 0; i < x; i++) {
        free(add[i]);
    }

    return 0;
}
```

# OUTPUT
![image](https://github.com/user-attachments/assets/8f51a1a3-7888-4595-82f9-6ae5d599e2a1)

![image](https://github.com/user-attachments/assets/de678693-95b3-4ed4-953a-84211b643c18)


# RESULT
### The program to implement a symbol table is executed and the output is verified.
