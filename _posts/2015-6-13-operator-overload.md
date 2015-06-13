---
layout: post
title: Overloading the operator
---

The power of C++ continues to impress me as I discover more and more. In my opinion, one of the coolest and most powerful features of the language is the ability to overload (give a new meaning to already existing) operators. What does this mean, and why is it useful? 

An operator is a symbol that has meaning for a given type. Take the primitive type int, for example. If you have two ints, you can add them together using “+” operator or subtract their values using “-” operator. These operations are fairly standard for all built-in types. But what about user types? Imagine you have a user-type named Elephant.

```c++
struct Elephant{
  int value;
}
```

Would it be legal to use the “+” operator on two Elephant types? What kind of behavior would result? Out of the box, this would not work, since the “+” operator is not defined by default on user-types. That’s where overloading comes into play.

```c++
struct Elephant{
  int value;

  // the following overloads the “+” operator
  int operator+(const Elephant& rhs){
    return value + rhs.value;
  }
}
```

By inserting the method “operator+” into the code, we have given a meaning to using the “+” operator with two Elephant types. But it doesn’t stop with just the “+” operator; we can extend this idea to any other existing operator in the language, such as “=”, “-”, “*”, “/”, “<<” and “>>”. However, there are a few rules to keep in mind when overloading an operator:

1. You cannot overload the operators for built-in types. For example, you cannot change the behavior of “+” for int or float. This also means that you cannot overload an operator that is not defined on a given built-in type. This means you cannot come along and give a meaning to “<<” on a float.
