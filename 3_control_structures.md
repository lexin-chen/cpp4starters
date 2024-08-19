# Control Structures

## Conditionals

### Simple if

In Python, it is like this

```python
if condition:
    statement1
    statement2
```

In C++ this same patten is simply 

```cpp
if (condition) {
    statement1
    statement2
    ...
}
```

Once again you can see that in C++ the curly braces define a block rather than indentation. In C++ the parenthesis around the condition are required because `if` is technically a function that evaluates to `true` or `false`.

### if else

how it looks in Python

```python
if condition:
    statement1
else:
    statement1
```

in C++

```cpp
if (condition) {
    statement1
    statement2
    ...
}
else {
    statement1
    statement2
    ...
}
```

### if elif else

```cpp
//Shows how to put conditional statements together,
//specfically putting "else if" after an "if" statement.
#include <iostream>
using namespace std;

int main() {

    int grade = 85;

    if (grade < 60) {
        cout<<'F'<<endl;
    }
    else if (grade < 70) {
        cout<<'D'<<endl;
    }
    else if (grade < 80) {
        cout<<'C'<<endl;
    }
    else if (grade < 90) {
        cout<<'B'<<endl;
    }
    else  cout<<'A'<<endl;

    return 0;
}
```

### switch

`switch` statement that acts something like the elif statement of Python under certain conditions but not that powerful. 

## While Loops

Most important control structures: iteration and selection. 

C++ has the standard `while` and `for` constructs. 

One example of the while loop

```cpp
int counter = 1;
while (counter <= 5) {          /*Use of an interactive method until the
                                 the loop ends   */
    cout << "Hello, world" << endl;
    counter = counter + 1;
}
```

And this will print Hello, while loop remains to be true if counter is less than or equal to 5. Once reach, it will break. 

The `while` statement is general and can be used in many different algorithms. 

```cpp
while ((counter <= 10) && (!done)) {
...
}
```

logical operators
| words | operator |
|-------|----------|
| and | `&&` |
| or | `\|\|` |
| not equal to  | `!=` |
| not | `!` |
| greater than | `>` |
| less than | `<` |
| greater than or equal to | `>=` |
| less than or equal to  | `<=` |

## For Loops

`while` types are good but `for` loops is also pretty useful and it is useful when you know the number of time a loops should be executed for. 

```cpp
# include <iostream>
using namespace std;

int main(){
    for (int i = 0; i < 10; i++;){
	      cout << i << "Hello World" << endl;
    }
}
```

for (start; stop; increment)

now it will run it 10 times.

find the power from 1-10

```cpp
#include <iostream>
using namespace std;

int main(){
    for (int i = 0; i < 12; i++){
        cout << i * i << endl;
    }
    return 0;
}
```