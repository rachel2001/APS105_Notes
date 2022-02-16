<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [APS105](#aps105)
  - [Jan.26](#jan26)
  - [Jan.28](#jan28)
  - [Feb.7 2021](#feb7-2021)
    - [Pointer](#pointer)
  - [Feb.8](#feb8)
      - [Test Goldbach Conjecture](#test-goldbach-conjecture)
  - [Feb.14](#feb14)

<!-- /code_chunk_output -->

# APS105

## Jan.26

Example 1: Decision

Travel advisory
The purpose of this program is to help make a decision to issue an emergency advisory by the World Health Organization
by consulting three experts, and seeing what their average confidence is.

The input is the level of confidence expressed by three experts in fractions between 0 and 1.

The output of the program is a Go/No Go decision based on the
average of the three confidence levels. If the average is greater
than or equal to 70% it is a go.

```ruby
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

## Jan.28

Example 1:

This program demonstrates how a boolean variable, 'done', can be used to exit
the loop. Do not use 'break' for better coding style, readability, and
robustness.
```ruby
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

## Feb.7 2021

### Pointer

Example 1:

```ruby
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

```ruby
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

```ruby
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

## Feb.8

Functions: Scope of variables

```ruby
int func(int x, int y){
    int i = 1;
    for(int i = 0;;i++){

    }
}   // i remains 1
printf("%d,i);
```

Global Varables

```ruby
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

#### Test Goldbach Conjecture

```ruby
int main(void){
    do{
        printf("Enter a number:");
        scanf("%d",&number);
    }while(number %2 !=0 || number <= 2)

}
```

Bitwise Operator

```ruby

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

## Feb.14

```ruby
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

```
void read(int *marks, const int size){
    for(int *p = marks; i < size; p++, i++){
        scanf("%d",&p);
    }
}
```
