# Intro to C++

C++ will be refered to as cpp or C++ in this document.

### Why C++?

- enormous language 
- both high level language with low level features
- an industrial strength programming language and frequently used for large codebases.

### Similarities between Python and C++

The main function in Python

```python
def main():
    print("Hello World!")
main()
```

How to put it in cpp?

```cpp
#include <iostream>

int main(){

    std::cout << "Hello World!\n";
    return 0;
}

// OR
#include <iostream>
using namespace std;

int main(){
    cout << "Hello World!\n";
    return 0;
}
```

using namespace std; is conceptually similar to import in Python. It allows you to use the standard library without having to prefix everything with std::. 

### Compilation

Big difference between C++ and Python is that Python is an **interpreted language** while cpp is a **compiled language**. You can run Python just using the Python interpreter. 

But in cpp you need two steps

1. Prepare a file that ends in `*.cpp` . 
2. That file needs to be compiled from the compiled either from command line or an integrated development environment (IDE). 

Then you can run it. 

So why is this important? What does compiling do for us?

- early detection of error
- faster program execution

Compiler turn your C++ code into language machine can understand (machine code). 

<aside>
💡 Compiler generally transforms code written in a high-level language into a low-level language in order to create an executable program

</aside>

<aside>
💡 Interpreter directly executes statements in a scripting language without requiring them to have been assembled into machine language.

</aside>

### Using headers and libraries

Introduced using a `#`. They tell preprocessing which file, header or library to make available to the compiler. 

The `#include ...` is kind of like `import ...` 

`import` directly accesses code in another file and `#include` copies classes and function from another file. 

Python 

```python
import classname
```

in cpp

```cpp
#include <libraryname>
#include "filename"
```

You need the `<>` to include libraries like `#include <iostream>` `#include <string`. `"` is for headers and files not provided by the implementation.  

### Main function

Unlike Python. Every C++ program **MUST** have a `main` function like `int main()`.

This needs to be called implicitly instead explicitly. In Python, you need to call for main but this is implicit in cpp. 

The `int main` indicates that the return type is an integer. The final line of `main` is `return 0`. 0 would mean a successful run.

Functions are grouped together in `{}` brackets. It is basically the Python equiv. of tabbing. Tabbing in C++ indicates a block of code. but tab and whitespaces mostly have no meaning. `;` is used to conclude statements. 

For example:

```cpp
#include <iostream>
using namespace std; int main(){cout << "Hello World!\n"; return 0;}
```
Runs just fine.

### Comments in C++

In Python, it is a `#` but in C++ it is `//` two slashes and multi line comment `/*` and ends with `*/`

Kinda like the docstring but without not for documentation.  

However, the symbol groups `/**` and `*/` are often used to indicate documentation blocks at the beginning of a class, program, or function, since the second asterisk `*` is simply treated as part of the multi-line comment.

### Standard Output

We have to interact with user to get data to get some results. `<iostream>` can get info from standard input and output. The input and output is handled by `steam`.

A stream is a channel that data flows from source to destination. `cout` is character ouput is like `print` in Python. It will print to standard output device. Following `cout` is followed by the `<<`, which is the “output operator”. It can also be used to concatenante output like “+” in Python.  
The word 'endl' in C++, a programming language, stands for **end of line**

```cpp
#include <iostream>
using namespace std;

int main(){
    cout << "Ever heard of rubber duck debugging?" << endl;
    cout << "                __     " << endl;
    cout << "              <(o )___-" << endl;
    cout << "               ( .__> /" << endl;
    cout << "                `----' " << endl;
}
```

### Standard Input

The command `cin` is similar to `cout` except it is an character input. Input stream direct data from a source, a keyboard or a file. 

```cpp
#include <iostream>
using namespace std;

int main() {

    // Declare a variable to store the user's input
    float num;

    // User prompt
    cout << "Give me a number:" << endl;

    // Store user input in the variable
    cin >> num;

    // Output the user's input to the console
    cout << "This is your number doubled: " << num * 2 << endl;

    return 0;
}
```

### Type Declaration

all variable in cpp must be declared before use and they cannot change type — **static typing**. `float num` tells compiler to set sufficient space for a floating point number and to name this memory location `num` and whatever the user types will be stores in `num`. 

<aside>
💡 Summary

1. Everything in C++ must be declared as a specific type of object or variable, including declaring the return type for each function.
2. Every C++ program must have a function which begins as `int main()`, and ends with the statement `return 0;` when successfully completed.
3. C++ statements are ended by a semi-colon.
4. White space is mostly meaningless in C++, but all C++ code blocks must be surrounded by curly brackets {}, rather than using indentation to delineate blocks as is done in Python.
</aside>

Compiler creates an executable program by transforming code written in a high-level programming language into a low-level programming language. 

Machine code is a computer program written in instructions that can be directly executed by a computer’s CPU.