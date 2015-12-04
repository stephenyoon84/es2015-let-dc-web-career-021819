# Using The Let Keyword

## Overview

In this lesson, you will get to know ES2015's let keyword.

## Objectives

1. Understand how to declare variables using the let keyword.
2. Understand the scoping differences between let and var.
3. Understand how let hoists differently than var.

<!-- iframe of video lecture goes here -->

The following code below can be run in Terminal by using ...

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

### Lexical (Function) Scope and Hoisting

In JavaScript using the var keyword, variables are lexically scoped to the function they are within. This means that variables that are declared within the function declaration are only accessible inside of that function and are not accessable outside of that function. For example:  
```javascript
function advice(age) {
  if (age > 18) {
    var suggestion = "Hope your saving for retirement...";
  } else {
    var praise = "Happy birthday kid!";
  }
}

advice(19);
console.log(suggestion); //Uncaught referenceError: suggestion is not defined.
```  
In this example the variable suggestion is only accessible inside the advice function. When we try to console log its value we receive an error that suggestion is not defined. This is do to the var keywords scope which is limited within the function.

Let's update the code example to log the value of suggestion now inside the advice function:
```javascript
function advice(age) {
  if (age > 18) {
    var suggestion = "Hope your saving for retirement...";
  } else {
    var praise = "Happy birthday kid!";
  }
  console.log(suggestion); // Hope your saving for retirement...
  console.log(praise); // undefined.
}

advice(19);
```  
The console reports back "Hope your saving for retirement..." for the suggestion value and undefined for the value of the praise variable. The advice variables value is accessible (in scope) inside of the function. But wait a minute why did the the console log for the praise variable report its value as "undefined" instead of a proper error message like "Uncaught referenceError: praise is not defined." This is because JavaScript does something sneaky, it hoists variable declarations to the top of the function scope. It is essentially doing this for us behind the scenes:  
```javascript
function advice(age) {
  var suggestion, praise; // variables declared with var keyword are hoisted to top of function.
  if (age > 18) {
    suggestion = "Hope your saving for retirement...";
  } else {
    praise = "Happy birthday kid!";
  }
  console.log(suggestion); // Hope your saving for retirement...
  console.log(praise); // undefined.
}

advice(19);
```  
Here we can see that hosting is when JavaScript automatically lifts the variable declaration to the top of the function scope. `var suggestion, praise;` is declared but no value is assigned at that point. This means that when we try to log its value inside of the function before we have assigned a value, it will hold the value of undefined. It is treated as a variable that has been named but is holding no value up until the point that we set it a value inside our if/else condition. If the else condition never runs then its value remains undefined.

It would be nice to get a proper error message in these situations and have some control to prevent JavaScript from hoisting variables to the top of the function. To protect ourselves it would be ideal in this case to limit the scopr of the variables to inside the blocks of the if/else `{}` curly braces.

## Introducing Let

Here we can accomplish this using the let keyword in place of var.  
```javascript
function advice(age) {
  if (age > 18) {
    let suggestion = "Hope your saving for retirement...";
    console.log(suggestion); //Hope your saving for retirement...
  } else {
    let praise = "Happy birthday kid!";
    console.log(praise); //Happy birthday kid!
  }
  console.log(suggestion); //Uncaught referenceError: suggestion is not defined.
  console.log(praise); //Uncaught referenceError: praise is not defined.
}

advice(19);
advice(12);
```  
The previous code illustrates that the variables declared using the let keyword are scoped within the if/else block instead of the entire function as wit hte var keyword. The console logs inside the if/else blocks report the correct values where as logging the values outside of the if/else blocks throws an appropriate error message. The let keyword only hoists to the top of each block as opposed to the top of the function they are found within.

## Summary

- The let keyword allows us to scope variables inside their block.
- The let keyword only hoists variables to the top of the current block preventing unexpected undefined values like we might see when using var.
- The syntax for declaring a block scoped variable is `let x = 12;`.

## Resources

- [MDN - JavaScript - Let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [MDN - JavaScript - Block](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block)

<a href='https://learn.co/lessons/es2015-let' data-visibility='hidden'>View this lesson on Learn.co</a>
