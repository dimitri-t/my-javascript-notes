# A few notes on how JavaScript works under the hood

> _Everything in JS happens inside the execution context_

## **Execution Context**

**Memory Component** (variable environment) - place where all variables and functions are stored as key value pairs

**Code component** (thread of execution) - where code is executed ONE line at a time

_“JS is a synchronous single-threaded language”_

**JS Call Stack** - at the bottom we have the global execution context. When a function is invoked, a new execution context is created and placed on top of the stack until it returns.

## **Undefined vs not defined**

If the variable name which is being accessed doesn't exist in memory space then it would be not defined, and if exists in memory space but hasn't been assigned any value till now, then it would be undefined

## **Hoisting**

In the memory creation phase, var is set to undefined and functions are set to the code inside them. That is why functions can be called as if they were on the top of the file. let and const are in the “temporal dead zone” until we set them, they are stored in a different memory than the global execution context. We can’t use them here initialisation. level of strictness ... var<<let<<const. var //no temporal dead zone, can redeclare and re-initialise, stored in GES. let //use TDZ, can't re-declare, can re-initialise, stored in separate memory. const //use TDZ, can't re-declare, can't re-initialise, stored in separate memory. syntax error is similar to compile error. while type and reference error falls under run time error. syntax error ... violation of JS syntax type error ... while trying to re-initialise const variable reference error ... while trying to access variable which is not there in global memory.

## **Closure**

Function bundled with its lexical environment is known as a closure. Whenever function is returned, even if its vanished in execution context but still it remembers the reference it was pointing to. Its not just that function alone it returns but the entire closure and that's where it becomes interesting

## **Scope Chain**

“Scope in JS is directly related to Lexical environment”

Scope - where you can access a specific variable inside the code

Lexical environment - wherever an execution context is created a lexical environment is also created. It’s whatever is in the local memory plus the lexical environment of it’s parent.

## **Block scope**

let & const are block scoped

A block is defined by {}

## **Closures**

Closure means that **an inner function always has access to the vars and parameters of its outer function**, even after the outer function has returned. You have learned that we can create nested functions in JavaScript. ... This is called Closure. A function can return another function in JavaScript.

## **setTimeout**

It takes the callback function, stores it somewhere and when the timer expires it adds it to the call stack

# **Functions**

## **Function statement**

```javascript
function a ( ) {
  ...
}
```

## **Function Expression**

```javascript
var a = function ( ) {
  ...
}
```

The major difference between a function statement and a function expression is **hoisting**

## **Anonymous functions**

They are used when the functions are used as values.

## **Named function expression**

```javascript
var a = function b ( ) {
  ...
}
```

Instead of assigning an anonymous function to a, we assign it a function with a name

## **Parameters vs Arguments**

```javascript
function a (param1, param2) {
  ...
}

a(arg1, arg2);
```

## **First Class Functions**

The ability to use functions as values and to be passed in as arguments to other functions and can be returned by functions

## **First C lass citizens**

same thing as first class functions

## **Higher Order Functions**

A function which takes another function as an argument or returns a function is a Higher Order Function.

## **Callback Functions**

_“Callback Functions give us access to asynchronous things in JS”_

A Callback Function is one that is passed into another function. It is called ‘Callback’ because it is passed in as an argument to another function and we don’t know when it will be called in the program.

Example: the setTimeout function. It takes in a callback function and a time in ms to call that function after that time has passed.

## **Asynchronous JS & Event-Loop**

JS uses the call-stack to execute whatever comes inside it. It gets executed instantly. JS waits for nothing here.

## **Asynchronous JS**

The browser or Node for example, will use the micro-task or callback queue to execute code after a certain delay. The browser/node will keep track of the callback function to execute after the delay is over. It will then push the function to the appropriate queue.

## **Web APIs (come as part of the browser)**

- setTimeout()
- DOM APIs
- fetch()
- localStorage
- console
- location

## **Callback queue**

After the timer gets expired, the callback function is put inside the Callback Queue, and the Event Loop checks if the Call Stack is empty and if empty, pushes the callback function from Callback Queue to Call Stack and the callback function gets removed from the Callback Queue. Then the Call Stack creates an Execution Context and executes it.

## **Micro-task queue**

Microtask Queue has **higher priority**. All the callback functions coming through **_[Promises](https://www.geeksforgeeks.org/javascript-promises/)_** and **_[Mutation Observer](https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver)_** will go inside the Microtask Queue. For example, in the case of **[.fetch()](https://www.geeksforgeeks.org/javascript-fetch-method/)**, the callback function gets to the Microtask Queue. Promise handling always has higher priority so the JavaScript engine executes all the tasks from Microtask Queue and then moves to the Callback Queue

## **Starvation of functions**

When the callback queue callback functions never get the chance to be executed, because the micro-task queue is continuously full.
