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