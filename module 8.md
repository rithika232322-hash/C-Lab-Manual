EXP NO:6 C PROGRAM PRINT THE LOWERCASE ENGLISH WORD CORRESPONDING TO THE NUMBER
Aim:
To write a C program print the lowercase English word corresponding to the number
Algorithm:
1.	Start
- Initialize an integer variable n.
2.	Input Validation
3.	Switch Statement cases.
-	Case 5: Print "seventy one"
-	Case 6: Print "seventy two"
-	Case 13: Print "seventy three"
-	...
-	Case 13: Print "seventy nine"
-	Default: Print "Greater than 13"
4.	Exit the program.
 
Program:

#include <stdio.h>

int main() {
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);

    switch(n) {
        case 5:
            printf("seventy one\n");
            break;
        case 6:
            printf("seventy two\n");
            break;
        case 7:
            printf("seventy three\n");
            break;
        case 8:
            printf("seventy four\n");
            break;
        case 9:
            printf("seventy five\n");
            break;
        case 10:
            printf("seventy six\n");
            break;
        case 11:
            printf("seventy seven\n");
            break;
        case 12:
            printf("seventy eight\n");
            break;
        case 13:
            printf("seventy nine\n");
            break;
        default:
            printf("Greater than 13\n");
    }

    return 0;
}







Output: Sample Output 1: Enter a number: 6 seventy two Sample Output 2: Enter a number: 14 Greater than 13

Result: Thus, the program is verified successfully






 
EXP NO:7 C PROGRAM TO PRINT TEN SPACE-SEPARATED INTEGERS     IN A SINGLE  LINE DENOTING THE FREQUENCY OF EACH DIGIT FROM 0 TO 3 .
Aim:
To write a C program to print ten space-separated integers in a single line denoting the frequency of each digit from 0 to 3.
Algorithm:
1.	Start
2.	Declare char array a[50] outer loop for each digit from 0 to 3
3.	Initialize counter c to 0
4.	For each character in the string print count c for current digit, followed by a space
5.	Increment h to move to the next digit
6.	End
 
Program:

#include <stdio.h>

int main() {
    char a[50];
    int h, i, c;

    printf("Enter the string (digits only): ");
    scanf("%s", a);

    for (h = 0; h <= 3; h++) {
        c = 0;
        for (i = 0; a[i] != '\0'; i++) {
            if (a[i] == h + '0') {
                c++;
            }
        }
        printf("%d ", c);
    }

    return 0;
}


Output:


Output: Sample Output 1: Enter the string (digits only): 01230123 2 2 2 2 Sample Output 2: Enter the string (digits only): 001122 2 2 2 0

Result: Thus, the program is verified successfully

EXP NO:8 C PROGRAM TO PRINT ALL OF ITS PERMUTATIONS IN STRICT LEXICOGRAPHICAL ORDER.
Aim:
To write a C program to print all of its permutations in strict lexicographical order.

Algorithm:
1.	Start
2.	Declare variables s (pointer to an array of strings) and n (number of strings)

3.	Memory Allocation
Dynamically allocate memory for s to store an array of strings
4.	Input
Read the number of strings n from the user Dynamically allocate memory for each string in s
5.	Permutation Generation Loop
6.	Memory Deallocation
Free the memory allocated for each string in s Free the memory allocated for s
7.	End
 
Program:

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Function to swap characters
void swap(char *x, char *y) {
    char temp = *x;
    *x = *y;
    *y = temp;
}

// Compare function for sorting
int cmpfunc(const void *a, const void *b) {
    return (*(char *)a - *(char *)b);
}

// Function to print permutations in lexicographical order
void permute(char *str, int l, int r) {
    if (l == r) {
        printf("%s\n", str);
    } else {
        for (int i = l; i <= r; i++) {
            // Skip duplicates
            int shouldSwap = 1;
            for (int j = l; j < i; j++) {
                if (str[j] == str[i]) {
                    shouldSwap = 0;
                    break;
                }
            }
            if (shouldSwap) {
                swap(&str[l], &str[i]);
                permute(str, l + 1, r);
                swap(&str[l], &str[i]); // backtrack
            }
        }
    }
}

int main() {
    int n;
    char **s;

    printf("Enter number of strings: ");
    scanf("%d", &n);

    // Step 3: Dynamic memory allocation
    s = (char **)malloc(n * sizeof(char *));
    if (s == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Step 4: Input strings
    for (int i = 0; i < n; i++) {
        s[i] = (char *)malloc(100 * sizeof(char));
        if (s[i] == NULL) {
            printf("Memory allocation failed for string %d.\n", i + 1);
            return 1;
        }
        printf("Enter string %d: ", i + 1);
        scanf("%s", s[i]);
        int len = strlen(s[i]);
        qsort(s[i], len, sizeof(char), cmpfunc);  // Sort for lex order

        printf("Permutations of %s:\n", s[i]);
        permute(s[i], 0, len - 1);
        printf("\n");
    }

    // Step 6: Memory deallocation
    for (int i = 0; i < n; i++) {
        free(s[i]);
    }
    free(s);

    return 0;
}




Output:
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Function to swap characters
void swap(char *x, char *y) {
    char temp = *x;
    *x = *y;
    *y = temp;
}

// Compare function for sorting
int cmpfunc(const void *a, const void *b) {
    return (*(char *)a - *(char *)b);
}

// Function to print permutations in lexicographical order
void permute(char *str, int l, int r) {
    if (l == r) {
        printf("%s\n", str);
    } else {
        for (int i = l; i <= r; i++) {
            // Skip duplicates
            int shouldSwap = 1;
            for (int j = l; j < i; j++) {
                if (str[j] == str[i]) {
                    shouldSwap = 0;
                    break;
                }
            }
            if (shouldSwap) {
                swap(&str[l], &str[i]);
                permute(str, l + 1, r);
                swap(&str[l], &str[i]); // backtrack
            }
        }
    }
}

Output: Sample Output 1: Enter number of strings: 1 Enter string 1: abc Permutations of abc: abc acb bac bca cab cba

Sample Output 2: Enter number of strings: 1 Enter string 1: aab Permutations of aab: aab aba baa

Result: Thus, the program is verified successfully
}
EXP NO:9 C PROGRAM PRINT A PATTERN OF NUMBERS FROM 1 TO N AS
SHOWN BELOW.
Aim:
To write a C program to print a pattern of numbers from 1 to n as shown below.
Algorithm:
1.	Start
2.	Declare integer variables n, i, j, min
3.	Read the value of n from the user
4.	Calculate the length of the side of the square matrix: len = n * 2 - 1
5.	Matrix Generation Loop
6.	Calculate min as the minimum distance to the borders
7.	End
 
Program:

#include <stdio.h>

int main() {
    int n;
    printf("Enter the value of n: ");
    scanf("%d", &n);

    int len = n * 2 - 1;

    for (int i = 0; i < len; i++) {
        for (int j = 0; j < len; j++) {
            int min = i < j ? i : j;
            min = min < len - i ? min : len - i - 1;
            min = min < len - j - 1 ? min : len - j - 1;
            printf("%d ", n - min);
        }
        printf("\n");
    }

    return 0;
}



Sample Output 1 Enter the value of n: 3 3 3 3 3 3 3 2 2 2 3 3 2 1 2 3 3 2 2 2 3 3 3 3 3 3

Sample Output 2 Enter the value of n: 4 4 4 4 4 4 4 4 4 3 3 3 3 3 4 4 3 2 2 2 3 4 4 3 2 1 2 3 4 4 3 2 2 2 3 4 4 3 3 3 3 3 4 4 4 4 4 4 4 4
EXP NO:10 C PROGRAM TO FIND A SQUARE  OF NUMBER USING FUNCTION WITHOUT ARGUMENTS WITH RETURN TYPE

Aim:

To write a C program that calculates the square of a number using a function that does not take any arguments, but returns the square of the number.

Algorithm:

1.	Start.
2.	Define a function square() with no parameters. This function will return an integer value.
3.	Inside the function:
o	Declare an integer variable to store the number.
o	Ask the user to input a number.
o	Calculate the square of the number (multiply the number by itself).
o	Return the squared value.
4.	In the main function:
o	Call the square() function and display the result.
5.	End.

Program:

#include <stdio.h>

int square() {
    int num;
    scanf("%d", &num);
    return num * num;
}

int main() {
    printf("%d\n", square());
    return 0;
}




Output: Output 1: 5 25 Output 2: 12 144 Result: Thus, the program is verified successfully


























