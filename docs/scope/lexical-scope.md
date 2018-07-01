# Lexical Scope

The word "lexical" refers to the fact that lexical scoping uses the location where a variable is declared within the source code to determine where that variable is available. Nested functions have access to variables declared in their outer scope.

![Lexical Scope](/assets/images/lexical-scope.png)
Source: https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20%26%20closures/ch2.md

- In lexical scope (1), we have `foo`
- In lexical scope (2), we have `a, b, bar`
- In lexical scope (3), we have `c`

Inner scope can access to variables of outer scope.
