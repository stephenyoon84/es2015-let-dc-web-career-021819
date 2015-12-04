# Using The Let Keyword

## Overview

In this lesson, you will get to know ES2015's let keyword.

## Objectives

1. Understand how to declare variables using the let keyword.
2. Understand the scoping differences between let and var.
3. Understand how let hoists differently than var.

<!-- iframe of video lecture goes here -->

## Function Scope vs Block Scope

The let keyword is an alternative to using the var keyword to declare variables. "let" behaves more in line with other programming languages like C or Java that use block scope. To understand block scope let us first describe blocks.

### What are blocks?

A "block" is a way to group several statements of code together. We describe the starting and ending points of a block using curly braces `{}`. In JavaScript this can be seen below in the following examples: such as if/else statements,  
```javascript
if (fish !== 'extinct') {
  // this also defines a block.
}
```  
loops,  
```javascript
while (stillPlaying) {
  // this as well defines a block.
}
```  
or a generic blocks defined by just braces alone.  
```javascript
{
  // all code here is also a generic block.
}
```  
Again, the important character to distingush these blocks are the curly braces `{}`. The braces themselves form a scope gate.

To appreciate how the let keyword differs let's first take a look at how the var keyword scopes variables.

### Lexical (Function) Scope

In JavaScript using the var keyword, variables are lexically scoped to the function they are within. This means that variables that are declared within the function declaration are only accessible inside of that function and are not accessable outside of that function. For example:  
```javascript
function birthday(age) {
  age++;
  if (age > 18) {
    var response = "Hope your saving for retirement...";
  } else {
    var response = "Happy Bithday kid!";
  }
  return response;
}
console.log(response); // Uncaught referenceError: response is not defined.
```  
In this example the variable response is only accessible inside the function birthday. When we try to console log its value we recieve an error that response is undefined. This is do to the var keywords scope which is limited within the function.


## Resources

- [MDN - JavaScript - Let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [MDN - JavaScript - Block](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block)

<a href='https://learn.co/lessons/es2015-let' data-visibility='hidden'>View this lesson on Learn.co</a>
