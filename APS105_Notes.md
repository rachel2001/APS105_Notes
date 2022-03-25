<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [APS105](#aps105)
  - [Jan.26](#jan26)
  - [Jan.28](#jan28)
  - [Feb.7](#feb7)
    - [Pointer](#pointer)
  - [Feb.8](#feb8)
        - [Test Goldbach Conjecture](#test-goldbach-conjecture)
        - [Bitwise Operator](#bitwise-operator)
  - [Feb.14](#feb14)
  - [Feb.16](#feb16)
      - [Dynamic Memory Allocation](#dynamic-memory-allocation)
  - [Feb.18](#feb18)
  - [Feb.28](#feb28)
    - [2D Arrays](#2d-arrays)
      - [Declaring](#declaring)
      - [Call Stack](#call-stack)
  - [Mar.2](#mar2)
  - [Mar.4](#mar4)
    - [Strings](#strings)
  - [Mar.6](#mar6)
  - [Mar.9](#mar9)
    - [strlen](#strlen)
    - [strcpy](#strcpy)
  - [Mar.11](#mar11)
    - [String Functions](#string-functions)
      - [strcpy vs. strncpy](#strcpy-vs-strncpy)
    - [Design Our Own String Copy Function!](#design-our-own-string-copy-function)
    - [strcat vs. strncat](#strcat-vs-strncat)
    - [strcmp vs. strncmp](#strcmp-vs-strncmp)
  - [Convert string to numbers: atoi vs. atof](#convert-string-to-numbers-atoi-vs-atof)
    - [strchr](#strchr)
  - [2022/03/14 String Continued](#20220314-string-continued)
    - [strstr](#strstr)
    - [self Implementation](#self-implementation)
    - [Array of Strings](#array-of-strings)
    - [Command-line Parameters](#command-line-parameters)
  - [Conversation With Leo](#conversation-with-leo)
  - [Mar.16 Recursion](#mar16-recursion)
    - [Cutting the cake](#cutting-the-cake)
    - [Example 1](#example-1)
    - [factorial](#factorial)
    - [printRow](#printrow)
    - [printTriangle](#printtriangle)

<!-- /code_chunk_output -->

---

# APS105

---

## Jan.26

Example 1: Decision

Travel advisory
The purpose of this program is to help make a decision to issue an emergency advisory by the World Health Organization
by consulting three experts, and seeing what their average confidence is.

The input is the level of confidence expressed by three experts in fractions between 0 and 1.

The output of the program is a Go/No Go decision based on the
average of the three confidence levels. If the average is greater
than or equal to 70% it is a go.

```c
#include <math.h>
#include <stdio.h>

int main(void) {
  const double thresholdForAlert = 0.70;

  double confidence1, confidence2, confidence3;

  printf("Enter the confidence levels of three experts: ");
  scanf("%lf%lf%lf", &confidence1, &confidence2, &confidence3);

  // First version: if (confidence1 > 1 || confidence2 > 1 || confidence3 > 1) {
  if ((confidence1 < 0 || confidence1 > 1) ||
      (confidence2 < 0 || confidence2 > 1) ||
      (confidence3 < 0 || confidence3 > 1)) {
    printf("Invalid input. Stopping...\n");
    return 0;
  }

  double average = (confidence1 + confidence2 + confidence3) / 3;
  printf("The average confidence value is: %lf\n", average);
  printf("%lf\n", average - thresholdForAlert);

  if (average > thresholdForAlert) {
    printf("It's time to issue the emergency advisory!\n");
  } else {
    printf("An emergency advisory is not recommended at this time.\n");
  }

  return 0;
}
```

---

## Jan.28

Example 1:

This program demonstrates how a boolean variable, 'done', can be used to exit
the loop. Do not use 'break' for better coding style, readability, and
robustness.

```c
#include <stdbool.h>
#include <stdio.h>

int main(void) {
  bool done = false;

  for (int i = 1; i <= 10 && !done; i++) {
    printf("i = %d\n", i);

    if (i * i >= 25) {
      printf("We are done.\n");
      done = true;
    }
  }

  // Here's another potential way to exit the loop. But it requires copying and
  // pasting code (from i * i >= 25 to i * i <= 25) and is fragile: changes in
  // one copy may not be made correctly in another copy. So this is not a good
  // design at all.
  for (int i = 1; i <= 10 && i * i <= 25; i++) {
    printf("i = %d\n", i);

    if (i * i >= 25) {
      printf("We are done.\n");
    }
  }

  return 0;
}
```

---

## Feb.7

### Pointer

Example 1:

```c
#include<stdio.h>
int main(){
int *p;     //1. Declaring
p = &x;     //2. Initializing
*p = 7;  // -> x = 7
x = *p +1;
printf("%d", x)
}
```

Example 2:

```c
void swap(int * x, int * y)

int main(void){
    int x, y
    x = 5
    y = 7
    swap( & x, & y)
}
void swap(int * x, int * y){
    int temp = *x
    * x = *y
    * y = temp
}

void * p{
    int * p = &x;
    if(p == NULL){
        printf("%d", p)
    }else
        *p = 1
}
```

NULL: null pointer is a constant

```c
#include<stdio.h>
int *largerLoc(int *x, int *y){
    if(*x >= *y){
        return x;
    }else{
        return y;
    }
}
int main(void){
    int x, y;
    x = 5;
    y = 7;
    int i = *largerLoc(&x,&y);
    printf("%d", *largerLoc(&x,&y)+1);

}
```

---

## Feb.8

Functions: Scope of variables

```c
int func(int x, int y){
    int i = 1;
    for(int i = 0;;i++){

    }
}   // i remains 1
printf("%d,i);
```

Global Varables

```c
external int global;
int main(void){
    global = 2;
}
```

Call stack
|
global vars
constant
|
code

##### Test Goldbach Conjecture

```c
int main(void){
    do{
        printf("Enter a number:");
        scanf("%d",&number);
    }while(number %2 !=0 || number <= 2)

}
```

##### Bitwise Operator

```c

// C Program to demonstrate use of bitwise operators
#include <stdio.h>
int main()
{
    // a = 5(00000101), b = 9(00001001)
    unsigned char a = 5, b = 9;

    // The result is 00000001
    printf("a = %d, b = %d\n", a, b);
    printf("a&b = %d\n", a & b);

    // The result is 00001101
    printf("a|b = %d\n", a | b);

    // The result is 00001100
    printf("a^b = %d\n", a ^ b);

    // The result is 11111010
    printf("~a = %d\n", a = ~a);

    // The result is 00010010
    printf("b<<1 = %d\n", b << 1);

    // The result is 00000100
    printf("b>>1 = %d\n", b >> 1);

    return 0;

}
```

---

## Feb.14

```c
int marks[] = {1,2,3,4,5};
void read(int marks[], const int size){
    for(int i = 0; i < size; i++){
        scanf("%d",&marks[i]);
    }
}
int main(void){
    const int size = 5;
    int marks[size];
    marks = &x;
}

write NULL is instead of writting 0
```

```c
void read(int *marks, const int size){
    for(int *p = marks; i < size; p++, i++){
        scanf("%d",&p);
    }
}
```

```c
void read(int *marks, int size)
{
    for (int i = 0; i < size; i++)
        scanf("%d", marks+i);
}
int main()
{
    int a[] = {1, 2, 3, 4}, *ptr = a;
    read(a, sizeof(a)/sizeof(int));
    for (int i = 0; i < 4; i++)
        printf("%d ", a[i]);
    return 0;
}
```

---

## Feb.16

```c
int main(void){
  int marks[] = {1,2,3,4,5};
  swap(marks,1,2);

}

void swap(int *marks, int i, int j){
  int temp = *(marks+i);
  *(marks+i) = *(marks+j);
  *(marks+j) = temp;
}

```

#### Dynamic Memory Allocation

```c
#include<stdlib.h>
int size = 10;
scanf("%d",&size);
int marks[size];
```

using pointer

```c
int *marks = (int *)malloc(size * sizeof(int));
*(marks+i) = 100;
scanf("%d",&marks[i]);
free(marks);
void *malloc(size_t size); //size_t: unsigned int

```

Memory Leak

```c
void read(int *marks, int size){
  int *marks = (int *)malloc(...);
  return marks;

}
```

---

## Feb.18

Exam time: 100 minutes

-   5 short questions:

    -   One line coding question
    -   Error-finding: compile-time error
    -   Output
    -   Evaluating Expressions

-   6 long answer questions:
    -   Easy (aim for full marks)
    -   Challenging (1~2)

digit (0~9)
Number (any length)
prompt user to enter valid input

---

## Feb.28

**_Written by Wen_** [check out his GitHub Profile](https://github.com/WenOu9)

### 2D Arrays

#### Declaring

```c
const int numRows = 2;
const int numCols = 3;

int marks[numRows][numCols];

// declare when initializing
int marks[2][3] = {
    {100, 90, 80};
    {90, 80, 70}
};

// declare with for loop
for (int i = 0; i < 2; i++) {
    for (int j = 0; j < 3; j++) {
        marks[i][j] = 0; // row and column would be better variable names
    }
}
```

#### Call Stack

    marks
    ([1][2]
     [1][1]
     [1][0]
     [0][2] // + 8
     [0][1] // + 4 // int is 4 bytes
     [0][0] // this is the location of the address of marks)
     main()

`Address of marks[i][j] = Address of marks[0][0] + sizeof( int )( i * numCols + j );`

```c
int sum(int marks[][3], int numRows, int numCols) { // include the "3" for the second array is important
    for () {
        for () {
            sum += marks[i][j]; // syntatic sugar for *(*(marks+i)+j)
        }
    }
}

int main(void) {
    int marks[2][3];
    printf("%d\n", sum(marks, 2, 3));
}
```

`*marks == *&marks[0]`
For 2D arrays, we can also dereference marks[0]:
`*marks[0] == *&marks[0][0]`

---

## Mar.2

```c
int marks[2][3];
sum(marks, 2, 3);
int sum(int marks[][3], int rows, int cols)
marks === marks[0];
*marks === *&marks[0]; // both are addresses
```

| row   |
| ----- |
| int\* |
| int\* |
| int\* |

first row:
| int | int | int | int |
| --- | --- | --- | --- |

```c
int **marks = (int**) malloc(rows * sizeof(int*));
for (int i = 0; i < rows; i++) {
    marks[i] = (int*) malloc(cols * sizeof(int));
    // marks[i] == *(marks + i)
}

for (int i = 0; i < rows; i++) {
    free(marks[i]);
}
free(marks);
```

---

## Mar.4

### Strings

string cells

| 'H' | 'E' | 'L' | 'L' | 'O' | '\0' |
| --- | --- | --- | --- | --- | ---- |

Declaration & Playing Around

```c
char s[] = {'h', 'i', '\0'};

char s[] = "Hello";
char *t = "Hello";
t = "hello";
char *t = (char*) malloc(6 * sizeof(char));
char *temp = t;
t = "the quick brown fox jumps over a lazy dog";
free(temp);
```

|                 MAX                 |
| :---------------------------------: |
|        Call Stack Shrink ⬇️         |
|            ............             |
| Heap (majority of memory) Grows ⬆️  |
|       Global Vars + Constants       |
| Including Strings, which is a const |
|                Code                 |

## Mar.6

## Mar.9

### strlen

```c
char *s = "sample";
printf("%s", s);

// print substring from s[0] to s[2]
printf("%s", s + 2);

// print s[0] + 2
printf("%c", *s + 2);
```

Strlen: return length of the string

```c
#include <string.h>
unsigned int strlen(const char *s);
printf("%u", strlen(s));
```

Implement our own stringLength!

```c
int stringLength(const char *s)
{
    int i = 0;
    // s[i] hits '\0' and jumps out of the loop
    // since '\0' == unsigned int 0
    while (s[i]) i++;
    return i;
}
```

| Stack | relative address |
| :---: | :--------------: |
| '\0'  |     6 <-- t      |
|  'e'  |        5         |
|  'l'  |        4         |
|  'p'  |        3         |
|  'm'  |        2         |
|  'a'  |        1         |
|  's'  |     0 <-- s      |

pointer arithmetic ver.

```c

int stringLength(const char *s)
{
    const char *t = s;
    while (*t) t++;
    return t - s;
}
```

Dynamic memory ver.
```
int stringLength(const char *s)
{
    char *s = malloc(6*sizeof(char));
    // check if memory allocation is successful
    if (s != NULL)
    {
        // do the work
    }
}
```

### strcpy

```c
// definition
char *strcpy(char *dest, const char *src)
{
    int i = 0;
    while (src[i]) dest[i] = src[i++];

    // add '\0' to the end of the string
    dest[i] = '\0';
    return dest;
}

// pointer arithmetic ver.
char *strcpy(char *dest, const char *src)
{
    char *t = dest;
    /*
    while (*dest) *dest++ = src++;
    *dest = '\0';
    */

    while ((*dest = *src) != '\0)
        dest++, src++;

    // nerd ver., don't use!
    // while (*dest++ = *src++)
    return t;
}

```

## Mar.11 

### String Functions

#### strcpy vs. strncpy

```c
// not safe!
// char *strcpy(char *dest, const char *src);

// safe
// char *strncpy(char *dest, const char *src, size_t n);

int main()
{
    char s[6];
    // copy the '\0' character here
    strncpy(s, "Hello", 6);
    return 0;
}
```

```c
int main()
{
    char s[] = "Hello World";
    // does not copy the '\0' character
    strncpy(s, "Hello", 5);
    return 0;
}
```

### Design Our Own String Copy Function!

```c
char *stringSafeCopy(char *dest, const char *src, int n)
{
    for (int i = 0; i < n && (dest[i] = src[i]) != '\0'; i++)
    {;}
    return dest;
}
```

### strcat vs. strncat

```c
// char *strcat(char *dest, const char *src);
int main()
{
    char s1[13] = "Hello";
    char *t = "World!";

    // would print "HelloWorld!"
    puts(strcat(s1, t));

    // the string is "HelloWorld\0"
    puts(strncat(s1, t, 6));
    return 0;
}
```

### strcmp vs. strncmp

```c
// int strcmp(const char *p, const char *q);
int main()
{
    // strcmp("abc", "bcd") < 0
    // strcmp("sam", "same") < 0
    // strcmp("114514", "114514") == 0
    // strncmp("sam", "same", 3) == 0
}
```

## Convert string to numbers: atoi vs. atof

```c
// int atoi(const char *s);
int main()
{
    printf("%d", atoi("314"));
    printf("%.2lf", atof("3.14"));
}
```

### strchr

```c
// return the first occurrence of char c in string s
// strchr(const char *s, char c);
char *s = "Hello";
char *p = strchr(s, 'e');
printf("%s\n%d", p, p-s);

// print out all of the occurrences
p = s;
while (p != NULL)
{
    p = strchr(p+1, 'e');
}
```

## 2022/03/14 String Continued

### strstr

```c
// char *strstr(const char *s1, const char *s2);
// returns an address to first occurrence of s2 in s1
char *s1 = "Hello again, my name is...", *s2 = "again";
strstr(s1, s2);
```

### self Implementation

```c
// use strncmp!
char *strstr(const char *s1, const char *s2)
{
    char *p = s1;
    int n1 = strlen(s1), n2 = strlen(s2);
    while (*p != '\0' && strncmp(p, s2, n2) && n-(p-s1) >= n2)
    {
        p++;
    }
    if (*p == '\0') return NULL;
    return p;
}
```

### Array of Strings

```c
// not commonly used
// we can write into  this character array
char months[][10] = {"January", "February", /* ... */ "September", /* ... */ "December"};

// Alternative version
char *months[12];
months[0] = "January"; // note that we cannot write into it
```

### Command-line Parameters

```c
// argc stands for argument count
// argv stands for argument vector
int main(int argc, char *argv[])
{
    if (argc != 3)
    {
        printf("Usage: ls .....\n");
        // this terminates the whole program
        exit(0);

        // this only terminates the function
        return 0;

        // for more information about the difference between return 0 and exit(0) check out the link below
    }
}
```

[Difference Between return 0 and exit(0)](https://stackoverflow.com/questions/3463551/what-is-the-difference-between-exit-and-return)

```c
int main(int argc, char *argv[])
{
    for (int i = 0; i < argc; i++)
    {
        printf("%s ", argv[i]);
        // wrong version
        // printf("%s ", *argv+i);
    }
    return 0;
}
```

## Conversation With Leo

Use `macro`
[#if, #elif, #else, and #endif directives ](https://docs.microsoft.com/en-us/cpp/preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp?view=msvc-170)

```c
#if condition
// code
#elif condition
// code
#else
// code
#endif

// condition must be satisfied
assert(/* condition */);
```

## Mar.16 Recursion

### Cutting the cake

```c
cutCake(chunk)
{
    // base case
    if (chunk < loog)
        return;
    else {
        // cut into two halves
        cutCake(chunk/2);
    }
}
```

### Example 1

f(n) = {
2 \* f(n-1) + 1, n > 0
3, n = 0
}

```c
int f(int n)
{
    if (n == 0) return 3;
    return 2 * f(n-1) + 1;
}
```

### factorial

```c
int factorial(int n)
{
    if (n < 0)
    {
        printf("you fucked up");
        return 114514;
    }
    else if (n == 0 || n == 1) return 1;
    else return n * f(n-1);
}
```

### printRow

```c
void printRow(int n)
{
    if (n <= 0)
    {
        printf("\n");
        return;
    }
    else
    {
        printf("*");
        printRow(n-1);
    }
}
```

### printTriangle

```c
void printTriangle(int n)
{
    if (n > 0) {
        printTriangle(n-1);
        printRow(n);
    }
}
```

x^n
```c
double power(double x, int n){
    if(x==0){
        if(n == 0){
            printf("error");
            reurn 0.0;
        }else{
            return 0.0;
        }
    }
}

```