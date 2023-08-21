---
title: "Lambthon - Lambda Calculus Interpreter"
author: "Samuel Kriikkula"
---

Lambthon is a small python script I made a while back.
It's a lambda calculus interpreter.

[Lambthon Lives Here](https://gitlab.com/xamn/lambthon)

## Syntax
`^x.` is a function that takes *x* as input. The return value comes after `.`

Currying is supported. This is similar to Haskell (if you happen to know Haskell).

`^x.^y.` is a function that takes two parameters, however it's also a function `^x.` that returns another function `^y.`

## The most simple function
The defined *a* function returns it's first parameter.
```
a = ^x.x
```

This returns the *a* function itself.
```
a a
```

This returns 1.
```
a 1
```

## Math
Addition
```
add = ^x.^y.x+y
```

Subtraction
```
sub ^x.^y.x-y
```

Square
```
sqr = ^x.x*x
```

## Logic
True and false both take two parameters.

True returns it's first parameter.
False returns it's second parameter.
```
true  = ^x.^y.x
false = ^x.^y.y
```

The logical operators are defined as follows:
```
notf = ^x.x false true
andf = ^x.^y.x y false
orf = ^x.^y.x true y
xor = ^x.^y.x (notf y) y
xnor = ^x.^y.x y (notf y)
```