# JavaScript

## Important Concepts

* `Hoisting` is JavaScript's default behavior of moving declarations to the top.
* All `Function Declarations` are hoisted.
* A `Function Expression` is an anonymous function that is saved into a variable. They do not get hoisted.
* In a `Regular function`, the `this` keyword is bind to the `window object` instead of the scope of where the function is located.
* In an `Arrow Functions`, the `this` keyword is automatically bind to where the function or class is located.
* Declare all your variables as a `const` unless the use of `let` is required.
* `let` variables are block scoped.`var` variables are function scoped.
* `let` variables are not added to the global object. `var` variables are added to the global object as properties.
* `let` variables can not be redeclared. It will give you an error. `var` keyword allows you to redeclare a variable without any issue.
* Avoid using `var` to declare variables. `var` variables get 'hoisted', which can lead to unexpected results.
* Always use strict equality operator `===`. The abstract equality operator `==` only compares value, not type.
* Both `null` and `undefined` represent empty values. When a variable is declared, but not assign a value, JS will automatically set `undefined` as a placeholder.
* If you do `typeOf` `undefined` the value will be `undefined`, whereas the value of `null` will be an object.



## Array Helpers
* `forEach()`
* `map()`
* `filter()`
* `find()`
* `reduce()`
* `every()`
* `some()`

## JavaScript Most Used Features
* `Template Literals`: Allows for embedded expressions in a string.
```js
const color = "red";
console.log( `Hello, my favorite color is ${color}!!` );
// Result: Hello, my favorite color is red!!
```
* `Spread Operator`: It takes in an array or object and expands it into individual elements. This operator makes copying and merging arrays a lot simpler.
```js
const fruits = [ "apple", "banana", "kiwi" ];
const basket = [ ...fruits, "orange", "strawberries"];
// Result: [ "apple", "banana", "kiwi", "orange", "strawberries" ]
```
* `Rest Operator`: allows a function to accept an indefinite number of arguments as an array.
```js
function average( ...theArgs ) {
    const total = theArgs.reduce( (previous, current) => {
        return previous + current;
    });
    return total / theArgs.length;
}
console.log(average(1,2,3,4,5));
// Result: 3
```
* `Default function parameters`: allows named parameters to be initialized with default values if no value or undefined is passed
```js
function tipCalculator( billAmount, tip = 10 ) {
    return ( tip * billAmount ) / 100;
}
console.log( tipCalculator( 40 ) );
// Result: 4
console.log( tipCalculator( 60, 15 ) );
// Result: 9
```
* `Destructuring`: makes it possible to unpack values from arrays, or properties from objects, into distinct variables.
```js
let motorcycle = {
    type: "Yamaha",
    model: "R6",
    color: "Blue",
    name: "Rosalinda"
}
let { name } = motorcycle;
console.log(name);
// Result: Rosalinda
```


## Helpful
