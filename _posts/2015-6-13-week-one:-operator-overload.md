---
layout: post
title: week1
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

2. You cannot invent your own operator symbol. For example, suppose you really like the look of ",,," and decide it would make a good operator for your type. This is not allowed. In C++, you are limited to use only the existing symbols.

3. You cannot change the presidence of the operator (order of operations). "*" and "/" have a higher presidence than "+" and "-". This means that any operation involving these operators will happen before an operation with lower presidence. Since this happens at the parsing stage of compilation, it cannot be changed.

4. You cannot change the associativity of an operator. X - Y - Z happens left to right. That means Y is subtracted from X before Z. In the case of X = Y = Z, the opposite happens. Y is assigned to Z before X is assigned.

5. You cannot change the arity of an operator. This refers to the number of arguments it takes. There are uniary, binary, ternary and multi argument operators, such as "(-)", "+", "()? () : ()" and method calls. You cannot decide to make one addition happen with three numbers.

While these restrictions might be inconvenient for some programmers, the ability to overload operators in C++ is a powerful tool that can be used for many practical applications.
