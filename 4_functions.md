# Functions

## Defining C++ Functions

A function definition requires a name , group of parameters, return type, body. 

It may return a variable, value, or nothing (void keyword)

for example 

```cpp
#include <iostream>
using namespace std;

int timesTwo(int num) {
    return num * 2;
}

int main() {
    cout << timesTwo(5) << endl;
    return 0;
}
```

a function that does not return anything

```cpp
#include <iostream>
using namespace std;

void timesTwoVoid(int num) {
    cout << num * 2 << endl;
}

int main() {
    timesTwoVoid(5);
    return 0;
}
```

`timesTwoVoid` has a void in front of its function and is a non-fruitful function meaning it does not return a value even though it can still print something out. 

```cpp
#include <iostream>
using namespace std;

double newton(double n) {
    double oldguess = n/2;
    for (int i = 0; i < 20; i++) {
        // or 1.0/2
	      oldguess = 0.5 * (oldguess + (n/oldguess));
    } 
    return oldguess;
}

int main() {
    cout << newton(9) << endl;
    
    return 0;
}
```

So 0.5 or 1.0/2 because it needs to be recognize as a float if it is 1/2 it will be recognized as integer and you will get a 0 output. 

## Parameter Passing: by Value versus by Reference

So far, what we have done is **pass by value.**

Calling function by value involves copying the contents into memory location of the corresponding formal parameters. 

```cpp
void functionExample( int inputVar ) {
    int nextVar = inputVar * 2;
    inputVar = 4;

    cout << "nextVar = " << nextVar << " inputVar = " << inputVar;
}

void callingFunction() {
    int myVar = 10;

    functionExample( myVar );
    cout << "myVar = " << myVar;
}
```

When the function 

`callingFunction()`, it will call for `functionExample(...)`

### How about when we want a function to return more than one value?

that is pass by reference. Using this mechanism, the actual location in memory referenced by arguments are sent rather than values in that location. To let the compiler know that you intend to use pass by reference you put an `&` at the end of the type name. 

Then any changes to the values of the parameters will change the value of the arguments as well. 

If you want to change the value of a variable. pass by reference would be helpful

### When is this beneficial?

This feature is quite powerful and can be useful for

1. Efficiency 
    1. it directly operate on the original object, so it avoids the overhead of copy large or complex data. 
    2. Can be beneficial dealing with large arrays, structs, or objects. 
2. Modification of original data 
    1. functions can modify original data passed to them. 
    2. When you need a function to alter the state of its arguments. 
    3. can return multiple values from a function by passing multiple arguments by reference. 
3. “hand it over” without making a copy 
4. Interactions with pointers

```cpp
#include <iostream>
using namespace std;

void swap_values(int &variable1, int &variable2) {
    int temp;
    temp = variable1;
    variable1 = variable2;
    variable2 = temp;
}

int main(){
    int first_num, second_num;
    first_num = 7;
    second_num = 8;
    swap_values(first_num, second_num);
    cout << "1)" << first_num << "2)" << second_num;
    return 0;
}
```

Know the difference between these `func1` and `func2`

```cpp
// demonstrates the difference between pass-by-value
// and pass-by-reference functions.
#include <iostream>
using namespace std;

void func1(int var1, int var2){
    int temp;
    temp = var1;
    var1 = var2;
    var2 = temp;
}

void func2(int &var1, int &var2){
    int temp;
    temp = var1;
    var1 = var2;
    var2 = temp;
}

int main(){
    int num1 = 2;
    int num2 = 3;

    func1(num1, num2);
    cout << "results of func1:" << endl;
    cout << "num1: " << num1 << ", num2: " << num2 << endl;
    func2(num1, num2);
    cout << "results of func2:" << endl;
    cout << "num1: " << num1 << ", num2: " << num2 << endl;

    return 0;
}
```

- `func1`is passed by value
    - values passed into the function are copies of the original variable. Good for like `char` or small data types
- `func2` is passed by reference
    - values are passed into the function are direct memory references of the original variable. Good for large and complex datatypes.
    - So why does the `&` in the parameter cause the output to be different?
        - The `&` stores the memory address of the variable and in this case above, it swapped memory references, aka lockers switched.

## Arrays as Parameters in Functions

An array is a collection data type that is the ancestor of Python list. Functions can be used with **array parameters** to maintain a structured design. 

In function definition, an array parameter looks like a pass-by-value parameter because there is no `&` but the variable name is followed with set of `[]`. 

Here is an example of average hours worked over array of integers. 

```cpp
double average( int list[], int length ) {
    // It is correct syntax to omit array length on itself
    double total = 0;
    // return type double which indicates decimal is returned
    int count;
    for( count = 0; count < length; count++ ){
	      total += double(list[count]);
    };
    return (total / length);
}
```

Array parameters look like pass by value, but they are similar to pass by reference. They do not make private copies of the arrays. 

```cpp
void add_list( int first[], int second[], int total[], int length ){
    int count;
    for( count = 0; count < length; count++) {
        total[count] = firstpcount] + second[count];
};}
```

The first two array do not change values. So on the safe side, we can add the modifier `const`

```cpp
void add_lists( const int first[], const int second[], int total[], int length ) {
    //return type void which indicates that nothing is returned
    int count;
    for( count = 0; count < length; count++ ) {
        total[count] = first[count] + second[count];
};}
```

Ensures that compiler will not accept any statement that will modify elements of arrays `first` and `second`

## Function Overloading

### What is function overloading?

- to create multiple functions with identical names.
- Not a feature in Python
- In C++, two or more functions can have same name when they can be distinguish by parameters.

Overloading is a nice feature that Python does not offer so to do this require a different technique

```cpp
#include <iostream>
using namespace std;

void myfunct(int n) {
    cout << "1 parameter: " << n <<endl;
}

void myfunct(int n, int m) {
    cout << "2 parameters: " << n;
    cout << " and " << m <<endl;
}

int main() {
    myfunct(4);
    myfunct(5, 6);
    myfunct(100);
    
    return 0;
}
```

Python equivalent

```cpp
def myfunct(n, m=None):
    if m is None:
        print("1 parameter: " + str(n))
    else:
        print("2 parameters: " + str(n), end="")
        print(" and ", str(m))

def main():
    myfunct(4);
    myfunct(5, 6);
    myfunct(100);

main()
```

### Benefits of function overloading

- help kept consistency in the way functions are names in program
- Function that do similar tasks differ based on parameters rather than by name.
- Function can fulfill multiple tasks based on parameters