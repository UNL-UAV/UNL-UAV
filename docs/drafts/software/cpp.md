# C++
The whole project will be based around C++. C++ is a fast language, but it's also very complicated. By using this tutorial you will have the basics of C++ down. This whole tutorial is based heavily upon some java experiances. Contact a software team lead if you have trouble understanding a concept.

## Learn C++ via videos
This whole documentation is just a dumbed down version of what c++ entails. There is more resources and more concepts behind everything. I recommend that if you get stuck on something checkout the C++ videos by [TheCherno](youtube.com/TheChernoProject). As the guy make pretty good in-depth explination on each concept. You can checkout their C++ playlist [here](https://www.youtube.com/playlist?list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb).

## Compiler
C++ is a compiled language meaning that there is a program that sits in front of your source code. That program take in file and output an executable. On GNU/Linux we it would be most likely be g++. There are other programs like catkin, make, premake. Whose job is to generate project files and structure your projects. With ROS we will be using catkin, which is a dirivative of make.

## Pre-Proccessing
In C++ they have an feature called pre-procesing. That will execute before compile-time. These woule be our common `#include` or `#pragma once`.

`#include` basically copy and paste a file into the current file. We will be using this a lot because in source files we need to refrence our header file for our code and other header files. We can say this is our `import` statment in java. 

`#pragma once` is called an header guard. This basically prevent copying your declairation twice. It will solve some of the errors with C++. In the old days we would have to do somthing like 

```c++
#ifndef _CLASS
#define _CLASS

/** YOUR H File HERE */

#endif
```

## Headers
Headers are one of the file types you find in C++. They contain the declaration of your code. In short it says there exists a function/class/method. That has these parmeters. These files are typically ends with a .h or .hpp.

## Source Files
Source files are files that contain the body of the function. These are typically in .c or .cpp files.

## Data types
We have all the common data types from java

- bool - Boolean
- char - Character
- int - Integer
- float - Floating point
- double - Double Percision Floating Point
- void - valueless

We have modifiers that change the data type.

- signed - positive and negative values
- unsigned - only positive values
- short - reduced size
- long - increased size;

Here is a table with _most_ of the primitive data types

| Data Type                    | Width                    | Range                    |
|------------------------------|--------------------------|--------------------------|
| char                         | 1 byte                   | -127-127 or 0-255        |
| unsigned char                | 1 byte                   | 0-255                    |
| signed char                  | 1 byte                   | -127-127                 |
| int                          | 4 bytes                  | -2147483648 - 2147483647 |
| unsigned int                 | 4 bytes                  | 0 to 4294967295          |
| singed int                   | 4 bytes                  | -2147483648 - 2147483647 |
| short int                    | 2 bytes                  | -32768 - 32767           |
| unsigned short int           | 2 bytes                  | 0 to 65535               |
| signed short int             | 2 bytes                  | -32768 - 32767           |
| long int                     | 8 bytes                  | -2147483648 - 2147483647 |
| signed long int              | 8 bytes                  | same as long int         |
| unsigned long int            | 8 bytes                  | 0 - 4294967295           |
| long long int                | 8 bytes                  | -(2^63) - (2^63)-1       |
| unsigned long long int       | 8 bytes                  | 0 - 18446744073709551615 |
| float                        | 4 bytes                  |                          |
| double                       | 8 bytes                  |                          |
| long double                  | 12 bytes                 |                          |

We can use the `sizeof()` operator to get the size in bytes. For example `sizeof(int)` would output 4. While `sizeof(varible)` will output the size of the varible.

## Pointers
One of the most important data type in C++ is pointers. Pointers can be very complicated, but all you need to know is that `a pointer is just a varible that holds a memory address`. That's it. To get a pointer type we can use the memory address operator `&`. Then to decode that memory address we can use the derefrence operator `*`. See Example (Pointers-1)

We can also declare arrays as a pointer to the first object. See Example (Pointers-2). One of the pitfalls of having a pointer as an array type is that you don't know the size of the array. You may run in to a segmentation fault. That's why we pass though the size of the array. Take a look at the main function in Example (Pointers-2)

Pointers-1
```c++
#include "pch.hpp"
int main(){
	int i = 3287;
	int* pI = &i; // Pointer to I. This contain the memory address of I

	std::cout << *(pI) << std::endl // Dereference the pointer and print out the value at I.
}
```

Pointers-2
```c++
#include "pch.hpp"
int main(char* argv, int argc){
	int array[] = {3,2,8,7,9};
	int* pArray = array;

	const char* str = "Hello World"; // A string is just a const char pointer. Other also known as a character array.
}
```

## References
Like pointers, references are alias to the actual varibles. We use it when we want to modify the original data (to prevent copying). See Example (References-1). A reference must be instaciated.

References-1
```c++
#include "pch.hpp"
void modifyString(std::string str){
	str + " bar";
}

void modifyStringRef(std::string& str){
	str+" bar"
}

int main(){
	std::string var = "foo";
	modifyString(var);
	std::cout << var << std::endl; // will just print out "foo"

	modifyStringRef(var);
	std::cout << var << std::endl; // will print out "foo bar"
}
```

## Scopes
In general, the scope is defined as the extent up to which something can be worked with. In programming also the scope of a variable is defined as the extent of the program code within which the variable can we accessed or declared or worked with.

### Stack
e allocation happens on contiguous blocks of memory. We call it stack memory allocation because the allocation happens in function call stack. The size of memory to be allocated is known to compiler and whenever a function is called, its variables get memory allocated on the stack. And whenever the function call is over, the memory for the variables is deallocated. This all happens using some predefined routines in compiler. Programmer does not have to worry about memory allocation and deallocation of stack variables. The stack has very little space (Appox 1MB).

### Heap
The memory is allocated during execution of instructions written by programmers. Note that the name heap has nothing to do with heap data structure. It is called heap because it is a pile of memory space available to programmers to allocated and de-allocate. If a programmer does not handle this memory well, memory leak can happen in the program.

## Objects
C++ is a Object Orientated Language. It's layed out like Java, but it have the ability to be turned functional programming (C/Python).

To instanciate a class you can use the following format to start on the stack:

```c++
Foo f();
// or
Foo f;
```

To instaciate a class on the heap you can use the following format.

```c++
Foo* f = new Foo();
// Processing
delete f; // Every time we call new we call delete. Otherwise we get a memory leak. Memory leak is bad.
```

### Class
A class is an object that has visiblity. The main components of a class is it's member varibles, member functions, constructors, destructor.

#### Constructor
Constructors is a function that get executed to set up the object once instanciated.

#### Member Varibles
These are varibles that is owned by the class.

#### Member functions
These are functions that is owned by the class. They define the behaviour of the class.

#### Destructor
This is a function that will get called when a class need to be destroyed.

Here is an example on laying out your class in a header file.

Foo.hpp:
```c++
#pragma once
#include <string>

class Foo{
private:
	int _i1;
	std::string _bar;

	static int _COUNT;
public:
	Foo(); // Constructor
	void foo();
	void bar();
	inline int getI1() const { return _i1;};
	inline std::string& getBar() {return _bar;};
	~Foo(); // Destructor
private:
};
```

Foo.cpp
```c++
#include "Foo.hpp"

static int Foo::_COUNT = 0;

Foo::Foo(){
	// Implement Constructor
}

void Foo::foo(){
	// Implement Foo
}

void Foo::bar(){
	// Implement bar
}

Foo::~Foo(){
	// Implment Destructor
}
```

### Structs
Another type of object is called a struct. A struct is just a class with no visibility at all(all public)

```c++
struct config{
	std::string name;
	float fov;
	//...
}
```

## Inheratence
TODO

## Other
