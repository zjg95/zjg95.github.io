---
layout: post
title: The Pythonic Way
---

For some reason, I've always had kind of a negative attitude towards Python. I used to feel like it wasn't a real programming language and that it wasn't good for much more than printing random numbers, or simple math problems. But after the past week of Downing's class my attitude has begun to change.

Since I am in both of Downing's classes, I had to do the first programming assignment (Collatz) in both C++ and Python. Since it was the first assignment, it was very easy to feel the differences between the two languages. 

The most obvious difference to me is the lack of brackets in methods, conditionals and loops. I've found it to be a little more convenient this way, but at the same time it has been really difficult to shake the habit of writing them, which is annoying because they upset the Python interpretter. The fact that there is no need for a "main" method also feels very unnatural to me.

### Hello World!

I've found that just about everything is easier in Python. Take the example of the classic Hello World program. In C++ it looks like this:

#### C++
```c++
#include <iostream>

int main(){
	std::cout << "Hello World!" << std::endl;
}
```

Although smaller than Java, C++ doesn't hold a candle to python:

#### Python
```python
print("Hello World!")
```

The difference is clear. The hello world program is undeniably easier in Python. This is originally one of the reasons I thought it wasn't a "real" programming language. But Collatz proved to me that Python is capable of much more than hello world. The Pythonic collatz did everything the C++ collatz could do (although a bit slower). Downing proved that Python is powerful through the Root Mean Square example in class. 

#### C++
```c++
#include <math.h>
template <typename T>
double rmse (T a, T p) {
    int i = 0;
    int v = 0;
    while (i != size(a)) {
        v += pow((double)(a[i] - p[i]), 2.0);
        ++i;
    }
    return sqrt((double)(v / size(a)));
}
```
#### Python
```python
from numpy import subtract, mean, square
def rmse (a, p) :
    return sqrt(mean(square(subtract(a, p))))
```

### Personal Thoughts
The difference is incredible. It's so much easier to write the code in Python. I also appreciate the fact that Python is typeless, which makes all code generic. Obviously there is a difference in speed between C++ and Python, so you wouldn't want to write a program that runs all the time in Python. But I can absolutely appreciate the value of writing short simple programs in Python. The code is incredibly easy to write and read.

In the end, I'm really starting to see the differences between programming languages, and the value of using one over the other, depending on the goal.