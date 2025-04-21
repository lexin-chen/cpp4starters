# Struct

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
		struct {
				string brand;
				string model;
				int year;
		} myCar1, myCar2;
		
		myCar1.brand = "BMW";
		myCar1.model = "X5";
		myCar1.year = 1999;
		
		myCar2.brand = "Ford";
		myCar2.model = "Mustang";
		myCar2.year = 1969;
		
	  cout << myCar1.brand << " " << myCar1.model << " " << myCar1.year << "\n";
	  cout << myCar2.brand << " " << myCar2.model << " " << myCar2.year << "\n";
		
		
		return 0;
}

```

It can be access by the `.`

`myCar1.brand`

Struct is an object that can be used to group data together. It is a user-defined data type that allows you to combine data of different types into a single unit. Structs are commonly used to represent complex data structures in C++.
Structs are defined using the `struct` keyword, followed by the name of the struct and a set of curly braces that contain the data members. Each data member is defined with a type and a name, just like a variable. Structs can also have member functions, which are functions that operate on the data members of the struct.
Structs can be used to create complex data structures, such as linked lists, trees, and graphs. They are also commonly used in C++ to represent objects in object-oriented programming.
Structs can be used to create classes, which are a more advanced form of structs that allow for encapsulation and inheritance.
Structs are a powerful tool in C++ that allow you to create complex data structures and represent objects in your code. They are an essential part of the C++ language and are widely used in many applications.