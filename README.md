# Let

## Overview

In this lesson, you will get to know ES2015's let keyword.

## Objectives

1. Understand how to declare variables using the let keyword.
2. Understand the scoping differences between let and var.
3. Understand how let hoists differently than var.

## ~ 5min

<!-- iframe of video lecture goes here -->

*The code examples from this lesson can be run by pasting them into [Babel's online REPL](https://babeljs.io/repl/)*

## Function Scope vs Block Scope

The let keyword is an alternative to using the var keyword to declare variables. "let" behaves more in line with other programming languages like C or Java that use block scope. Block Scope means that variables have limited access within curly braces `{}` in the code. Function Scope (also known as lexical scope) means that variables declared within a function have limited access only inside of that function. To better understand this, let's first look at some blocks.

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

### Function Scope and Hoisting

In JavaScript when using the var keyword, variables are lexically scoped to the function they are inside of. This means that variables that are declared within the function declaration are only accessible inside of that function and are not accessable outside of that function. For example:  
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
In this example the variable suggestion is only accessible inside the advice function. When we try to console log its value we receive an error that suggestion is not defined.

Let's update the code example to log the value of suggestion now inside the advice function:
```javascript
function advice(age) {
  if (age > 18) {
    var suggestion = "Hope your saving for retirement...";
  } else {
    var praise = "Happy birthday kid!";
  }
  console.log(suggestion); // Hope your saving for retirement...
}

advice(19);
```  
The console reports back "Hope your saving for retirement..." for the suggestion value. The suggestion variables value is now accessible (in scope) inside of the function.

What would happen if we tried to access the value of praise instead:  
```javascript
function advice(age) {
  if (age > 18) {
    var suggestion = "Hope your saving for retirement...";
  } else {
    var praise = "Happy birthday kid!";
  }
  console.log(praise); // undefined.
}

advice(19);
```  
Wait a minute why did the the console log praise's value as "undefined" instead of a proper error message like "Uncaught referenceError: praise is not defined." This is because JavaScript does something sneaky, it hoists variable declarations to the top of the function scope. It is essentially doing this for us behind the scenes:  
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
Hpisting gives us `var suggestion, praise;` being declared at the top of the function, but no value is assigned at that point. This means that when we try to log its value inside of the function before we have assigned a value, it will hold the value of undefined. It is treated as a variable that has been named but is holding no value. If the else condition never runs such as in the case above then its value remains undefined.

It would be nice to get a proper error message in these situations and have some control to prevent JavaScript from hoisting variables to the top of the function. To protect ourselves it would be ideal in this case to limit the scope of the variables to inside the blocks of the if/else `{}` curly braces instead of having them scoped to the entire function.

## Introducing Let

Here we can accomplish limiting varibales to block scope by using the let keyword in place of var.  
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
The code above illustrates that the variables declared using the let keyword are scoped within the if/else block instead of the entire function. The console logs inside the if/else blocks report the correct values, where as logging the values outside of the if/else blocks throws the expected error message.

## Summary

- The syntax for using let is `let x = 12;`.
- The let keyword allows us to scope variables inside their block.
- The let keyword doesn't hoist variables to the top of the function, which gives us clear errors when we try to interact with them outside of their scope.

## Resources

- [MDN - JavaScript - Let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
- [MDN - JavaScript - Block](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/block)

<a href='https://learn.co/lessons/es2015-let' data-visibility='hidden'>View this lesson on Learn.co</a>
