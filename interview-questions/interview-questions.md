# JS Interview Questions

#### Q1. Difference between var and let ?

1. let was introduced in ES6
2. let has ‘block scope’. A variable defined with a let keyword will be garbage collected at the end of the block it’s defined in. var has function scope and will die in the end of the function it’s defined in, not the block
3. var gets hoisted at the top of it’s function and can be used even before defined as it is set to undefined. However, let will throw a ReferenceError as it has not been allocated memory

#### Q2. Difference between ‘==’ and ‘===’ ?

1. They both are comparison operators

2. == just compares value only

3. === compares value and type of value

4. == will convert the right value to the type of the left in order to compare

#### Q3. Difference between let and const

1. let can be re-initialised where as const cannot be

2. if u assign an object to const, it will let you change the object itself, so you could use array.push() but you could now reassign it.

#### Q4. Difference between ‘undefined’ and ‘null’

1. undefined gets assigned to a variable that has been allocated memory but not defined a value, so js sets it to a placeholder value which is undefined

2. null is just an empty value which we assign, you should not assign undefined

3. undefined is of undefined type whereas null is object type

#### Q5. What is the use of Arrow functions?

1. arrow function does not have its own this, so setting a this.variable = value; inside the arrow function, it will directly point to it’s parents this

#### Q6. What is prototypal inheritance?

1. every object has a property called prototype where you can add methods and properties to it and when you create other objects from these objects, the newly created object would automatically inherti the property of the parent, not by including in its own property, but it uses it’s parent.

#### Q7. Function declaration vs function expression

```javascript
function functionA() {
  ...
}

let functionB = function(){
  ...
}
```

functionA can be used before it is declared as it is hoisted. you can pass functionB as a variable to another function

#### Q8. What is promises and why do we use it?

1. we use them when we make an async call and we need to wait for it, and after it is done we call a callback function that we provide.
