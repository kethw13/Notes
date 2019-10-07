# CSCE 115E - Computer Science 1
## Arrays
### Fall 2019

* It is really rare that you only deal with say one varaible or one piece of data
* You usually want to operate on a *collection* of pieces of data
* In C, collections of similar pieces of data can be stored in *arrays*
  - Arrays are a collection of variables of the same type
  - Arrays have a single identifier (name)
  - Elements in an array can be accessed usin gan *index*: the first eement is at index 0, the seond is at index 1, ect.
  - If there are $n$ elements in an array, the last one is at index $n-1$
  - Indexing is achieved using the square brackets

## Static Arrays

* Static arrays are arrays of a fixed size that are allocated on top of the program stack
* Syntax

```c
//create an array that can hold 10 integers:
int arr[10];

//create an array that can hold 20 double values:
double numbers[20];
```
* Observation: just like other uninitailized variables, the contents of an array have no default values
* Demonstrations
* Once you have an array, you can set individual values using an index and the normal assignemnt operator

```c
arr[0] = 42;
arr[1] = -5;
arr[2] = 3.14; //arr[2] has a value of 3

//set the last value to 102:
arr[9] = 102;

//what happens here?:
arr[10] = 5;
arr[-1] = 6;
```

* Accessing elements outside of an array is *undefined behavior*
  - MAY be a seg fault
  - MAY simply screw up (memory corruption) your own memory
  - It MAY not result in any bad consequences

### Convenience Syntax

* YOu can initialize a static array using convenient syntax:

```c
int n = 7;
int primes[] = {2, 3, 5, 7, 11, 13, 17};
```

* In general, there is no way to determine the size of an array after it has been created in C
* In C, you *must* keep track of teh size of every array, this is known as "memory manegment"
* It is *your* responsibility ot keep track of the size of every array
* Consequence: if you pass an array to a function, you also need to *pass in an integer that represents the size of the array*
* This is also known as "bookkeeping": keeping track of the size of an arry in an `int` variable
```c
int main(void){
    int n = 100;
    int arr[n];
      for(int i = 0; i<n; i++){
       arr[i] = i * 10;
      }

       for(int i = 0; i<100; i++){
        printf("%d\n", arr[i]);
      }

  return 0;
}
```

## VLAs: Varaible Length Arrays

* You can set the size of an array using a varaible:
```c
int n = 100;
int arr[n]; //of size 100
```

* But in general, you shouldn't do this
* In fact, you should not use static arrays in general unless they are very small
* You end up abusing the stack space (which is relatively small)
* Example: attempt to create a "moderaltely" large array on the stack

## Dynamic Arrays

* Alternative: use dynamic arrays
* Dynamic Arrays are arrays that are allocated on the program "heap" instead of teh program stack
* The heap is larger, but less "well organized" chunk of memory
* However the heap is *much larger*
* In general, you "ask" the operating system for some chunk of memeor on the heap (of some specified) size, and it either accommodates you or refuses
* The wasy that you "ask" for memory is to ask for a *memory allocation*
* using the function `malloc`
* `malloc` takes only one argument: the number of bytes you want to allocate
* `malloc` returns a *pointer* to the memory location as which the memory was allocated (if successful)
* `malloc` will return `NULL` if it was unsuccessful
* More details:
  - `malloc` actually returns a "generic `void` pointer"
  - actual signature: `void * malloc(size_t size);`
  - This means that there are not dozens of different `malloc` functions, there is only one that returns "a chunk" of memory
  - It is your responsibility to use this memory for whatever purpose you have: use it as an array of integer, or use it as an array of doubles
  - In general the way you do this is by type casting: you case the returned generic void pointer into the pointer type you want

```c
int *a; //pointer to an integer
double *b;//pointer to a double
void *c;//generic pointer

int *arr = (int *) malloc(...);
double *numbers = (doulbe *) malloc(...);
```
* After successful allocation, you can use an array from malloc like a static array using regular old indexing

* In general you don't hardcode the number of bytes you want to use with `malloc`
* Some systems an integer may be only 2 bytes, some may be 4, or 3, or 8, etc.
* You can use teh "macro" `sizeof` to determine how many bytes a certain type takes on that

### Memory Management

* Once you allocate a chunk of dynamic memory and are done using it, you need to clean up after yourself
* Failure to clean up after yourself may result in a *memory leak* eventually leading to a program failure when you've run out of memory
* To clean up memory you use the `free` function: simpley pass in the pointer to memory that you want to *deallocate*

```c
//free up the integer array:
free(arr);
//ree up teh numbers array:
free(numbers);
```

* Attempts to access the contents of freed memory are *undefined behavior*
* Attempts to free already freed memory ("double freeing") is also *undefined behavior*
* Freeing memory that does not belong to you is *undefined bahvior*
