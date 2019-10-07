# CSCE 115 Notes

### Programming, Compiling & Running
 * Source file is a *plain text* file containing code in a high-level language
 * Source files have to be complied into an exectuable Programming
   - *source -> assembly -> machine code*

### Demonstration
1. Edit a source file, *hello.c*
2. Assemble file: *gcc -S hello.c*
3. Compile file: *gcc -c hello.c*
  - produces an object file: *hello.o*
  - view file: *hexdum -C hello.c*
4. You need to also link any external libraries
5. Everything at once: *gcc hello.c*

### Program Basics
* DRY - don't repeat yourself
* %lf - long float
* scanf - scanning in
* %f - placeholders for the variables
* Comments are human readable messages
* single line comments begin with: *//* anything beyond the *//* is not read by the computer
* Multi line comments begin with _/*_ and end with _*/_
* "Doc-Style" comments (headers of programs)
* Comments are designed to tell the why and how not the "what"
* code should be self-documenting! The code itself tells the "what"
* Pre
*



//declare an integer variable and set it equal to 10:
int x = 10;
int y; //dont know whta is stored in y
//0xDEADBEEF - value that has not been set

// later on you can always reset a variable's value:
x = 20;

//declare and set a double variable:
double pi = 3.14;



//declare a character variable:
char firstInitial = 'K' // backslash \ can be used for other such as \' or \\ (prints a \)
// cant have more than one charcter in charcter

* A variable's *name* (*identifiers*) must follow several rules
  * It may consist of letters, a-z, A-Z, 0-9, _
  * it may NOT begin with a number
* Style: USe proper names
  * Variables should be named after the things that they represent
  * Don't use not descriptive variable names; 'x', "foo", "bar", "myVariable", "myVariable02"
  * Good examples: "numberOfStudents", "annualPercentageRate"
  * In general you should aviod abbreviations, acronyms, short version
  * Follow consistent styling: "lowerCamelCasing" or "lower_underscore_casing"


### Operators

- Arithmetic: '+', '-', '*', '/'
- Consider the following: "a + b * c" is not the same as "(a + b) * c"
- PEMDAS
- example: $\frac { -b \pm \sqrt (b*2 - 4ac)} {2a}$



```c
double x = sqrt(-10); // results in Nan;

int y - 10 / 0 // Results in INT
```


* An integer division operator: '%'
  * It resuts in the *remainders* of a division
  * examples:
    * "10 % 3" results in 1 (a remainder of 1)
    * "11 % 3" results in 2
    * "11 % 2" results in 0

### Pit Fall: Truncation

```c
int a = 10;
int b = 20
double c = a / b; //results zero
```

* when you have two integers in your arithmetic operation, the result is always an integers
* IF you have an integer divided by an integer, the result is an integer: the fractional part is thrown away or "truncated"
* You can solve this by "temporarily" making one or both of the variables into a compatible 'dobule' type by *type casting*

```c
int a = 10;
int b - 20;
double c = (double) a / b;  // result 0.5
```

* Math Library
  * Has a bunch of mathematical function: 'sin(), cos(), tan(), sqrt()'
  * It also has a bunch of nice constants, 'M_PI', 'M_E'
  * you an use it by using '#include <math.h>'
  * On cse you *may* need to manually link it in:s
  'gcc -lm myProgram.c'
  * What other functions are in the math library?
    * google it
    * RTM: Tead the Manual
      man: sqrt()

### Basic I/O

* I = input, O = output
* Consider *interactive input*: where you prompt the user to enter a value then read from mathematical
* interactive input is achieved by usin gth 'scanf' (scan formmatted)
  * You provide a placeholder:
    * int : %d
    * double : %lf
    * char : %c
  * In general, read one value at a time
  * Never forget your ampersand on the variable: '&' otherwise you'll get wierd Results

* You can print to the standard output(screen) using 'printf'
  * Same format: you provide a format and any number of variables
    * int : %d
    * double : %f
    * char : %c
  * YOu can print multiple values in one statement using placeholders, but the numbers and types should match
  * You can also have more fine-grained control on what is printed

'''c
later tonight get these'
'''
# Chapter 3
### Conditionals


* Normally, programs have dwquential control follow
* However, more complex problems require *decisions*
* Conditionals are are how we can make some code execute uder some condition(s) and/or other, different code to execute under other conditions
* ```IF``` statements, if else statments, if-else-if statements

### Basic Syntax
```c

if(<condition>) {
  //if the condition evaluate to true, then the code inside this *block* will execute, otherwise it will NOT execute

}

if(<condition>) {
  // if this condition is true then this block gets executed

} else {
  // if this condition is false then this block gets exectued
}
```

* an if-else statement is *mutally exclusive*; exactly one of the blocks is going to be exectued (never both and never neither)
* You can also create more complex stateents using an `if-else-if` statement

```c
if(<conditionA>) {
//if condition a is gets executed

}else if (<conditionB>) {
  //if the condition b is true this block gets executed
} else {
  //otherwise, neither this block is executed
}
```

* Order is importatn: The _first_ condidion that evaluates to true, will cause its block to exectue: thus it excludes all the other blocks
* ALl conditions are *mutually exclusive*
* In gerneral you can define as many conditions as you want, with as many `else-if` statements as you want
* In general the `else` blcok is always optional
* Cruft: dead or useless or unused code in your code base, don't have left curt
* example:
```c
get this
```

# Conditions: Numberical Comparisions

* You can compare two values (either variable values or *literal* values is hare coded numbers)
* `<` (strictly less than)
* `<=` (less than or equal too)
* `>` (strictly greater than)
* `>=` (greater than or equal to)
* NOT: `=<` or `=>` (Neither is supported in c)
* `==` (equals)
* `!=` (inequality comparison)
* All of these operatots operate on two *operands* (left and right side)
* Each side can be a literal valude, variable or an expression
* grok: to immediately and intuitively understand something

```c
on github

```

## Pitfall

* you cannot use numerical comparison operators for strings
* Becuase the numerical comparison operators are comparing (memory addresses) and not the contents of the strings

## General Negation Operator

* Any statements can be negated (true becomes false, false becomes true) using the single negation operator:
* Example: `a !=b` and `!(a=b)` are the same things
* Example: `!(a < b)` could be better written as `a >= b` (second is preferralbe)
* In general you can negate any statements

## Boolean "variables"

* C actually does not support the keywords "true" nor "false"
* Instead, C uses numberical values for true/false
* In C, zero is false
* any non-zero value (1, 10, 3.14, -4.5) are all treated as true
* When you assigne a "true" value, yes, use 1, but you cannot assume that true is always 1
* Therefore if yu want a "boolean variable" (true or false falues) use `int` or

## Complex Logical Expressions

* You can combine one ore more logical expressions using logical "connectives"
* The logical AND operator is true if both of its operands is truncated
  - Syntax: `&&`
  - Example: `isStudent && isFreshman` is true if and only if the person is a student and is a freshman
* The logical OR operator which is true if at least ONE of its operands is ture
  - Syntax: `||`
  - Example: `isStudent || isFreshman` is true if one of the conditions is true


## Comparisons with Characters

* You can also make a comparison using the numberical  operator on SINGLE Characters
* This is becuase single characters are NUMBERS: ASCII

```c
```

### PitFall
Get code and notes

### Pitfall 2s


### Short Circuiting

* Consider the following logical statement: `a && b`
  - Suppose that `a` evaluates to false, does it matter what the value of `b` is?
  - No the first being false makes the entire expression false
  - Conssequently: C (and the vast majority of programing languages) will *not* evaluate `b`, its evaluate is "skipped" or "short-circuited"
  - It was originally done to save time and effieciency on CPU cycles
  - Still used in laguages becuase it is *familiar*
  - It has become a common programming *idiom*
* Consider the following logicl statement: `a || b`
  - Suppose that `a` evaluates to true, does it matter what the value of `b` is?
  - If the first is true, then the entire expression is true regardless of the value of `b`

### Linters

* Code may be syntacitcally correct ( it will compile) but still may have errors
* Lint are pieces of coe that may look suspicious and may lead to errors but are not syntax errors
* Linters are *Static analysis* tools that look for such *potential* errors in you rcode and report them (usually as warning)
* Static analysis: a grogram that analyzes the *source code* of another program pre-compilation
* `gcc` can be used as a rudimentary Linter using the flag `-Wall`
* its best practice to always compile with this flag, *take care of all your computer warnings*

# Loops

* To stop a program from the command line type "ctrl + c"
* Be careful from infinite loops
* Make sure to put in curly brackets to *bound* the code to a loop
* It is best to include curly brackets even if you don't need them


## Other Issues
### Nested loops

* Often you many nee to have more than one iteration
* You may neet to have a loop within a loop

```c
for(int i=0; i<10; i++){
  for(int j=0; j<10; j++){
    printf("i = %d, j =%d \n", i, j);
  }
}
```

### For Loop vs While loops

* Fact: any for loop can be rewritten as a while loop and vice versa
* In General you use a for loop when you know how many (even a varaible number of) interations you are going to execute
* In General  you use a while loop when you don't know how many iterations you are going to execute


```c
int x = 1234;

//Best Answer don't forget the math library
int numberOfDigits = (int) log10(x) + 1;

printf("Digits - %d", numberOfDigits);

//Another Answer without math library

int x = 1234;

int numberOfDigits = 0;
if (x = 0) {
  printf("Digits - 1");
}
while(x!=0) {
  x /= 10;
  numberOfDigits++;
}
  printf("Digits - %d", numberOfDigits);
```

* A for loop's iteration is *always* done at the end of the loop iteration
* You cannot scope (declare) an index variable that is limited to a while loop

### FizzBuzz Program
```c
int main(void) {

 for(int i=1; i<=100; i++){

   if (i % 3 == 0 && i % 5 == 0){
     printf("FizzBuzz\n");

   } else if(i % 3 == 0){
     printf("Fizz\n");

   } else if (i % 5 == 0) {
     printf("Buzz\n");

   } else {
     printf("%d\n", i);
   }
 }
}
```

### Savings Program
```c
#include <stdio.h>

int main(void) {

  double currentBalance = 1000.00;
  double apr = 0.05;
  double monthlyDeposit = 100.00;
  int numYears = 10;
  int numMonths = numYears / 12;


  for(int i=1; i<=numMonths; i++){
    double monthlyInterest = currentBalance * (apr / 12);
    double oldBalance = currentBalance;
    currentBalance += (monthlyInterest + monthlyDeposit);
    printf("%d $%.2f $%.2f $%.2f", i, oldBalance, monthlyInterest, currentBalance);
  }

return 0;
}
```

# Functions

* A *function* is a reusable unit fo code that may take *input(s)* and *may* produce an *output*
* Similar to math functions:
  - $$f(x), f(x, y), f()$$
* Already familiar with several functions: `sin(), round(), printf(), scanf(), main()`, ect.
* Functions facilitate *code reuse*: you don't copy-paste, don't reinvent the wheel.
* Procedural Abstaraction: functions allow you to ignore implementation details of how a certain block of code works, you con *just use it*
* Functions *encapsulate* functionality into reusable *abstract* units of code
* Standard libraries and external libraries provide useful functions that have a lot of testing, debugging and optimization behind them, don't throw these resources away!
* Feeds into an overall problem solving strategy: is there a function that does this task for me already? Or, failing that, is there a function that can help me parially solve this task?

## Functions in C

* as with variable, functions have to be "declared" before you can use them
* In c you "declare" a function by creating a *prototype*
* A prototype is a declaration that defines a functions *signature*
  - The name of the function (identifier)
  - the list of its inputs called "parameters" or "arguments"
  - The type of variable that the function outputs or `return`s
* Example:

```c
/**
 * this function rounds teh given amout to the
 * nearest hundredth (the nearest cent)
 *
 */
double roundToCents(double ammount);

```

* prototypes end with a semicolon
* Documentation is usually written *above* a prototype
* DRY: Don't repeat yourself, documentation should only be located in one place, an dhte most appropriate place in C is with the prototype
* Later on in teh program you actually define what the function does
* Example: You repeat the function signature and provide a function *body*

```c
double roundToCents(double amount) {
  double result = round(amount * 100) / 100;
  return result;
}
```

* Observve: not only does our function provide new functionality, but it illustrates code ruse itself: it uses the math library's `round` function!
* The result varaible is a *local variable* the *scope* of teh varile is limited to the function itself
* In general you can create as many local varaibles as you want or none at all
* In addititon, the paramerter varaible itself (in this case `amount`) is *local to the function*

## Creating a library: Modularity

* Demonstration: create another more general round function

```c
/**
 * This function rounds the fiven value to a decimal
 * place defined by the given digit
 * For examlple for
 *  value = 123.456 and digit = 2 would round to 100
 *  value = 123.456 and digit = 0 would round to 123
 *  value = 123.456 and digit = -2 would round to 123.46
 */

double roundToDigit(double value, int digit) {
  int power = pow(10, digit);
  return round(value / power) * power;
}

```

* in general prototypes (along with their documentation) are placed into *header* files, files ending in `.h`
* Function dfinition are placed in separate source files with the same base names with a `.c` extenstion
* YOu can compile (without linking) the library using the `-c` flage which produces an object file, `roundToDigit.o`
* IN general you should use `#include "userLibrary.n"` in your code using the double quotes for user-defined libraries
* To compile into an actual executable program; use `gcc roundUtil.o roundDemo.c` (ie include all object files in teh command)
* In general you want to perform, good, rigorous and *automated* testing of your functions called "unit testing"
* In general you want to


* programs have  a *program stack*: it is a LIFO = Last In First Out data structure
* The only operations allowed are: push; pop; removing from the top
* NO access to "middle" elements is allowed
* each time a funcition is called, a new *stack frame* is created and placed on top of teh program stack
* each time a function feturns (to the calling function) the top most stack frame is popped

* BY default, variable values are *passed by value* to function in c


## Pointers in C

* Every piece of data in a program or a computer is stored in *memory*
* Memory has both an *address* and *contents*
* You can acess contents by using a regular old ariable `int a = 42`
* You can access teh *address* of a memory location using a *pointer* varaible
* To declare a pointer variable you use the star operator: `*`

```c
//regular old declaration
in a = 42;
//this declares a pointer varable that can pointer
// to a memory location that contains an into
int *pointerToA;
```

* At this point, `pointerToA` does not necessarily point to anything, it could:
  - Point to an invalid memory location
  - point to a memory location that doesn't belong to you
* it is best practice to initialize a pointer ot a valid memory location or, failing that, to `NULL`
* Example:

```c
int *pointerToA = NULL;

if (pointerToa == NULL) {
  printf("Invalid pointer\n");
}
```

* How do you make a pointer point to a valid memory locaiton
* A variable's name is its "content"
* To get a varaible's memory location use the referencing operator: `&`
* Example:
```c
//this make pointerToA "point" to a
pointerToA = &a;
```

* If you have a regular variable, to get its memory adress you use the referencing operator: `&`
* If you have a ponter varaible, to access its contents (change it in to a regular old variable) : use the dereerencing operator: `*`
* You can have a pointer varaible point to any other type of varaible:

```c
int a = 42;
doulbe b = 3.5;
int *ptrToA = &a;
double *ptrToB = &b;
```

## Pitfalls

* You cannot arbitrarily assign values to a ponter:

```c
//pont to garbage or anything
int *ptrToA;
// ponts to a n invalid memory location or a memory location that does not belong to us;
ptrToA = 1234;
//The following is also wrong;
ptrToA = a;
```


* All of the above will likely result in a segmentation fault
* Even if it doesn't result in a seg fault you might be corrupting your own memeory


### summary

* Recall that `scanf("&lf", &b);` used an ampersand: why?
* Scanf is passing a variable by reference
* Functions that take pointer variable can make changes to the original variable if needed
* Referencing operator: regular variable into a pointer varaible `&`
* Dereferencing operator: pointer variable into a regular variable `*`
* Pointers allow you to free up the return value: instead of returing a result, you can set the values of a pointer or multiple pointers!
* You can write functions that "return" multiple values
