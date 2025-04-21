# Collection Data Types

## Collections

in addition to numeric, Boolean, and char types. There are also built-in collection types. 

A **collection** data type is a grouping of some number of other data items and needs to be operated upon together. 

arrays, vectors, strings, sets, hash tables are useful C++ collection types. 

## Arrays

An array is a data structure with an ordered collection of data elements, of identical type in which each element can be identified by array index. 

C++ array is stored in contiguous memory. C++ array can be allocated in two different ways. 

1. statically allocated means fixed at compile-time and cannot change
2. dynamically allocated means pointers in allocation process so size can change at run time. 
- In modern C++, statically allocated array is only used when speed is essential or hardware constraints exist. Usually, a vector is typically used when more flexibility is required.
- This is the ancestor of Python list.
- quite similar but C++ store variables directly and each element must be of identical data type
- start at 0
- Ordered set of memory so you can manipulate as one
- also direct access to each element

### Why use an array?

- speed is essential
- fixed space available
- Array elements are stored in memory locations in contiguous memory locations.

```cpp
double darray[4];
int iarray[10];
char arr2[3000];
```

**statically allocated C++ array need to have type and size at compile type.**

```cpp
int arr[] = {1, 2, 3, 4}; //This is size 4
char arr2[] = {'a', 'b', 'c'}; // size 3
string arr3[] = {"this", "is", "an", "array"}; // This is size 4. 
```

Beware that these are not the same

```cpp
double darray[] = {1.2};   // must use index to access value
double darray = 1.2; // cannot use index to access value.
```

### Be cautious with arrays

The speed and low level control in array is powerful.. and dangerous. 

As a Python programmer, using a C++ array help you understand trade-off of protections python offers. 

```cpp
//outputs all elements in the array
#include <iostream>
using namespace std;

int main(){
    int myarray[] = {2, 4, 6, 8};
    for (int i = 0; i < 4; i++){
        cout << myarray[i] << endl;
    }
    return 0;
}
```

Python has protection but protection takes time and C++ is all about speed. 

Python will not let you go beyond the end of a list. 

C++ not only let you do this and you can change value beyond end of the array with catastrophic results. 

For example:

```cpp
#include <iostream>
using namespace std;

// demonstrates what happens when iterating
// outside of an array in C++,
//also outputs the location of the value in memory
int main(){
    int myarray[] = {2, 4, 6, 8};
    for (int i = 0; i< = 8; i++){
        cout << myarray[i] << endl;
        cout << "id: " << &myarray[i] << endl;
    }
    return 0;
}
```

Output

```
2
id: 0x7ffc0906a860
4
id: 0x7ffc0906a864
6
id: 0x7ffc0906a868
8
id: 0x7ffc0906a86c
0
id: 0x7ffc0906a870
0
id: 0x7ffc0906a874
2033860096
id: 0x7ffc0906a878
-2030686375
id: 0x7ffc0906a87c
1
id: 0x7ffc0906a880
```

it comes at a cost of no error checking.

You should use an array when you have a need for speed or you have hardware constraints. Otherwise, consider the other collection data type, the vector. 

What happened? Went out of bounds

What is the correct way to declare an array in C++?

`int myarray[5]`

## Vectors

Vectors are much more similar to Python lists than arrays are. 

use the `< >` to indicate the data type of the elements.

```cpp
#include <vector>
```

Vector commands

- `myvector[i]` access value of element at index i
- `myvector[i] = value` assign value to element at index i.
- `myvect.push_back(item)` Append to the end of the vector.
- `myvect.pop_back()` Deletes last item (from far end) of the vector.
- `myvect.insert(i, item)` inserts an item at index i
- `myvect.size()` returns the actual size used by elements
- `myvect.capacity()` return size of allocated storage capacity.
- `myvect.reserve(amount)` request a change in capacity to amount.

### Iterating through Vectors

For vector it is simply, 

- `.length()` function to get length of container.

However for array, to get length, 

- you need to first do `sizeof()` - size in memory of the array and divide it by size of first element also using this function.

Python Example - get square of 0 to 49

```python
def main():
sqs = []
    for i in range(50):
        sqs.append(i ** 2)
```

C++ example

```cpp
// function that uses vector to sq
// every number from 0 to 49
#include <iostream>
#include <vector>
using namespace std;

int main(){
		vector<int> intvector;
		intvector.reserve(50);
		
		for (int i = 0; i < 50; i++){
				intvector.push_back(i * i);
				cout << intvector[i] << endl;
		}
		return 0;
}
```

In example above, `intvector.reserve(50)` is optional. 

However, better to do this because it will save time. Because if undefine it will guess and if it gets larger than the guess then it needs to move to large capacity and therefore will require more time copying. 

Vector can change size

What good is the `reserve` method in a vector?

Using it will save time if you know the max size needed.

## Strings

strings is a collections of zero or more characters, letters, numbers, other symbols”

Two types of strings in C++. C++ string or just string from `<string>` is similar to Python string class. 

```cpp
char cppchar = 'a'; // char single quotes
string cppstring = "Hello World!"; // double quote
```

Strings are sequences

- `astring[i]` access value of character at index i
- `astring[i] = value` change value of character at index i
- `string1 + astring2` concatenate strings
- `astring.append(string)` Appends a string to the end of the string.
- `astring.push_back(char)` Appends a character to the end of the string.
- `astring.pop_back()` Deletes the last character from end of the string.
- `astring.insert(i, string)` inserts a string at a specific index
- `astring.erase(i, j)` erases an element from one index to another
- `astring.find(item)` returns the index of the first occurrence of the item.
- `astring.size()` returns the size of the string.

Python equivalent example of below C++ example

```python
def main():
		mystring1 = "Hello"
		mystring2 = "World"
		mystring3 = mystring1 + " " + mystring2
		print(mystring3)
		
		print(mystring2, end=" ")
		print("begins at", end=" ")
		print(str(mystring3.find(mystring2)))
		
	main()
```

C++ example. 

```cpp
#include <iostream>
#include <string>
using namespace std;

int main(){
		string mystring1 = "Hello";
		string mystring2 = "World!";
		string mystring3 = mystring1 + " " + mystring2;
		cout << mystring3 << endl;
		cout << mystring2 << "begins at ";
		cout << mystring3.find(mystring2) << endl; 
		return 0;
}
```

## Hash tables

just like Python dictionaries. 

A hash table is a collection of pairs of key and value. 

Also known as *map* because the hash function “maps” the key to the value. 

Hash function returns the location of associate value as the output. It makes look up fast. 

In Python, the dictionary data type represents the implementation of the hash table. 

```cpp
#include <unordered_map>
```

Python equivalent: dictionaries

```cpp
def main():
		spnumbers = {"one": "uno", "two": "dos"}
		
		spnumbers["four"] = "cuatro"
		spnumbers["three"] = "tres"
		
		print("one is", end=" ")
		print(spnumbers["one"])
		print(len(spnumbers))
		
main()
```

C++: hash tables 

```cpp
#include <iostream>
#include <unordered_map>
using namespace std;

int main() {
		unordered_map<string, string> spnumbers;
		spnumbers = { {"one", "uno"}, {"two", "dos"} };
		spnumbers["three"] = "tres";
		spnumbers["four"] = "cuatro"
		cout << "one is ";
		cout << spnumbers["one"] << endl;
		cout << spnumbers.size() << endl;
}
```

It is important to note that hash tables are organized by the location given by hash function not in particular order by keys. 

It is this point that make look up fast. 

That’s why it is odd to iterate hash table in C++ and Python. 

```python
def main():
		spnumbers = {"one":"uno","two":"dos","three":"tres","four":"cuatro","five":"cinco" }
		
		for key in spnumbers:
				print(key)
				print(spnumbers[key])

main()
```

C++

```cpp
#include <iostream>
#include <unordered_map>
#include <string>
using namespace std;

int main(){
		unordered_map<string, string> spnumbers;
		spnumbers = {
				{"one", "uno"},
				{"two", "dos"},
				{"three", "tres"},
				{"four", "cuatro"},
				{"five", "cinco"}
				};
		for (auto i = spnumbers.begin(); 
				i != spnumbers.end(); i++){
				cout << i->first << ":";
				cout << i->second << endl;
		}
}
```

`auto` is used to automatically detect the data type when variable is declared. 

This is ONLY when declaring complex variables. 

Hash tables have both methods and operators. 

- `mymap[k]` return the value associated with `k` or else error.
- `mymap.count(key)` return `true` if key is in `mymap`. `false` otherwise. (is it there?)
- `mymap.erase(key)` removes the entry from `mymap`.
- `mymap.begin()` an iterator to first element in `mymap`.
- `mymap.end()` iterator to past-the-end element of `mymap`

## Unordered Sets

- An **unordered set** is an unordered collection of zero or more unique C++ data values of a particular type.
- Unordered_sets allows for fast retrieval of individual element based on their value.
- The value of an element is also the key
- Keys are immutable.
- cannot be modified once in the container.
- Can be inserted and removed.
- no duplicate
- initialized using comma-delimited values in `{ }`

```cpp
set<int> mySet = {3, 6, 4, 78, 10}
```

Very similar to the math setting. 

`set_union()` return new set with all elements from both sets

`set_intersection()` return new set with elements in both sets. 

`set_difference()` return new set with all items from first but not in second. 

`aset.insert(item)` adds item to the set

`aset.erase(item)` removes item from the set

`aset.clear()` removes all elements from the set

Function to check if a char is in the unordered set.

```cpp
#include <iostream>
#include <unordered_set>
using namespace std;

void checker(unordered_set<char> set, char letter){
		if(set.find(letter) == set.end()){
				cout << "letter " << letter << " is not in the set." << endl;
		}
		else{
				cout << "letter " << letter << " is in the set." << endl;
		}
}

int main(){
		unordered_set<char> charSet = {'d', 'c', 'b', 'a'};
		char letter = 'e';
		checker(charSet, letter);
		charSet.insert('e');
		checker(charSet, letter);
		return 0;
}
```

The find method compare each item in the set with the given param until there is a match. 

`set.find(letter) == set.end()` if `find` cannot find `letter` before reaching to end of the set. Then `letter` not in set. 

1. A statically allocated C++ array is an ordered collection of one or more C++ data values of identical type stored in contiguous memory.
    1. example `{"What", "am", "I", "am"}`
2. A vector is a dynamically allocated array with many useful methods. It is more similar to the Python list than the array.
3. C++ strings are a sequential collection of zero or more characters. They are very similar to Python strings.
4. A hash table is used to store keys-value pairs. It applies a related hash function to the key in order to compute the location of the associated value. Look-up is typically very fast.
    1. example `{{"What", "am I"}}`
5. A set is an unordered collection of **unique values.**
    1. example `{"What", "am", "I"}`