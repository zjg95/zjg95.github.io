---
layout: post
title: Assignment vs Initialization
---

Downing has blown my mind yet again. When discussing programming, I have always tended to describe setting a value as "assigning" the value to a variable. Whether it was an initial declaration, or 100 lines later, the value was "assigned." I haven't ever thought twice about using that word to describe the action. As it turns out, I've been wrong for a long time; there's actually a difference between "assignment" and "initialization."

```c++
class T {
	...	
};

int main(){
	T x;   // initialization
	x = 2; // assignment
}
```

#### Assignment
Assignment refers to changing the value of an already existing variable. At the low level, this means that you are changing the underlying data of the particular data type. You cannot assign a value to a variable that has not been initialized. This invokes the assignment operator of the class.

In the example given above, T x already exists. We are simply changing its value from 3 to 2.

#### Initialization
This refers to building data for a structure that does not exist yet. The data structure's type is given in front of the expression to trigger the initialization. This invokes the constructor of the class.

In the example above, we delcare that x is of type T. This reserves space for the T.

### The Difference

Assignment cannot happen before initialization. You must have existing underlying data before you can make any changes.

In a language like C++ where objects can be built on the stack, declaring the existence of an object without additional arguments invokes the default constructor of that type. This will provide initial values for the data, allowing you to make changes.

```c++
#include <iostream>

class T {
	T(){
		// default constructor
		std::cout << "initialization" << std::endl;
	}
	T(int i){
		// int constructor
		std::cout << "initialization" << std::endl;
	}
	T(const T& rhs){
		// copy constructor
		std::cout << "initialization" << std::endl;
	}
	T& operator=(const T& rhs){
		// assignment operator
		std::cout << "assignment"     << std::endl;
	}
};

int main(){
	T x;     // prints initialization
	x = 2;   // prints assignment

	T y = 3; // prints initialization
}
```

As shown above, it is possible to provide an initial value to a variable. However, since this invokes that object's constructor it is still not assignment; this is initialization.

### Closing Thoughts

I found Downing's analysis of this subject to be very interesting. Aside from being "politically correct" about the phrasing, it's very cool to have a better understanding of the processes happening under the covers.
