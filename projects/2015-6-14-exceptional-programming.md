---
layout: post
title: Exceptional Programming
---

What happens when a program encounters a problem? If something goes wrong, how can it be detected before the error propagates deeper into the system to a point beyond recovery? What’s the best way for a program to communicate a problem?

Error checking can happen in a number of different ways. The simplest solution that one might imagine could involve checking for a bad return value.

```python
def f(arg) :
	if arg :
		return -1
	return 0

return_value = f(1)
if return_value == -1 :
	print("something wrong")
else :
	print("normal")
```

While this would work at a simple level, it's not entirely ideal. We're also assuming that -1 is an invalid return value. What if the function could return any number? Maybe it doesn't even return a number! Using -1 as a means of communication is not a long term solution. But what if we used a global variable?

```python
def f(arg) :
	global x
	if arg :
		x = -1
	return 0

x = 0
return_value = f(1)
if x == -1 :
	print("something wrong")
else :
	print("normal")
```

This is better, but still has disadvantages. For example, a more complicated program might encounter more than one error. If global variables are used to communicate issues, more than one global variable would be needed to communicate all possible issues.

An even bigger issue at hand is the fact that if a caller forgets to check for the problem, the error will be allowed to continue through the program until a point so distant that identifying the initial issue will be much more difficult. This is what makes the use of "exceptions" very valuable.

```python
def f(arg) :
    if arg :
        raise NameError("bad")
    return 0

try :
	return_value = f(1)
	print("normal")
except :
	print("something wrong")
```

 An exception tells the program that something has gone wrong, and forces it to handle it on the spot or else terminate. This mechanism prevents errors from going unnoticed and propagating through the system. The exception object itself will also contain information about what went wrong. The "try" block tells the program to expect an exception. The "except" clause tells the program what to do in the event of an exception. Some programming languages (like C++) allow the programmer to leave out the try/catch block. In that situation, the program will return to the caller's caller looking for a try/catch block. If the program reaches the root thread of execution without finding a way to handle the exception, it will terminate.

Ultimately, the use of exceptions allows a programmer to write far more sophisticated, EXCEPTIONal code.
