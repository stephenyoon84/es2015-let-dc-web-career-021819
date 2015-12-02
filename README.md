# Using The Let Keyword

## Overview

In this lesson, we'll get to know ES2015's let keyword. We'll see that let carries with it a different scope for declaring variables than the var keyword.

## Objectives

1. Understand how to declare variables using the let keyword.
2. Understand the scoping differences between let and var.
3. Appreciate how let prevents variable hoisting issues. 

## Function Scope vs Block Scope

The let keyword is an alternative to using the var keyword to declare variables . "let" behaves more in line with other programming languages like C or Java that use block scope. To understand block scope let us first describe blocks.

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
Again, the important character to distingush these blocks are the curly braces `{}`.

To appreciate how the let keyword differs let's first take a look at how the var keyword scopes variables.

### Functional Scope

In JavaScript using the var keyword gives you functional scope, meaning that variables that are declared within the curly braces of the function declaration are only can be accessible inside of that function. For example  
```javascript

var realAge = 35;

function getAge() {
  
  return StartingAge += 1;
}
```

...

## Resources

- [MDN - JavaScript - Let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [MDN - JavaScript - Block](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block)

<a href='https://learn.co/lessons/es2015-let' data-visibility='hidden'>View this lesson on Learn.co</a>
