---
layout: post
title: Pointers and References
---

When I started learning C++, the only other programming language I knew was Java. Since Java handles objects exlusively on the heap, the idea of building an object on the stack was very new to me. As a result, this was my first exposure to the concept of pointers. Although Java does use pointers to reference objects, it's all handled automatically and was easy to miss as a new programmer.

While pointers allow programmers to write powerful code, I can understand how their usage might seem confusing to novice programmers. I can remember struggling to understand the difference between the "*" and "&" operators. As it turns out, there are four stories to tell with these operators:

### * next to a type

```c++
int  a;
int* b;
```

When * appears next to a type, it creates a pointer of that type. Pointers can be used to access specific locations in memory.

### & next to a name

```c++
int  a = 6;

int* b = &a;

cout << a << endl; // prints 6
cout << b << endl; // prints the address, ex. 0x08E074BF
```

Using the operator like this returns a pointer to 'a'. This is essential for creating a pointer.

### * next to a name

```c++
int  a = 6;

int* b = &a;
*b = 7;

cout <<  a << endl; // prints 7
cout << *b << endl; // prints 7
```

When * appears next to a name, it follows the pointer and returns the data pointed to. This can be used to read or write to the value pointed to by the pointer. This is called "dereferencing" the pointer. This will only work for pointer types. In this example, the thing pointed to by 'b' becomes 7. Since 'b' is pointing to the memory location of 'a' it will become 7. 

### & next to a type

```c++
int  a = 6;

int& b = a;

b = 7;

cout << a << endl; // prints 7
cout << b << endl; // prints 7
```

This operator placement creates a "reference" to an existing value. Once a reference is created, there is nothing that can be said about one value that would not affect the other. For example, changing the value of 'a' will always change the value of 'b,' and vice versa. Performing any operation with a will be the same if that operation were performed with 'b.' You can think of it as another name for that variable.

#### Personal thoughts
Coming from a language like Java where all pointers are managed for you, I have grown to love manually managing pointers. The concept of C++ references is new to me, but they feel very natural. I have written some small amounts of Java code after studying C++ and I've found that the inability to manage pointers manually inhibits my ability to easy write powerful code. Ultimately I am a huge fan of pointers and references and I encourage others not to fear them.