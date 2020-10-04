# JS-TIPS :sunglasses:

## **JS-TIPS** is a collections of *byte sized JavaScript tips* which I found during my journey of learning JavaScript. The complete guide is divided into multiple sections. This is more of like a reference for myself so that I can glance over what I learnt while studying JavaScript.

### Values in JavaScript

- Numbers in JavaScript are 64 bits which include all of integers (both positive and negative), decimal numbers.

- There are 6 types of values in JavaScript, ES6 adds one more called Symbols
    * Numbers
    * Booleans
    * Strings
    * Objects
    * Functions
    * Undefined

- `Infinity`, -`Infinity` and `NaN` are special type of Number values.
    ```javascript
    Infinity - Infinity // NaN
    Infinity / Infinity // NaN
    Infinity + Infinity // Infinity
    Infinity * Infinity // Infinity
    ```
- `typeof` operator gives the type of a value in string.
    ```javascript
    console.log(typeof (typeof 'str')); // 'string'
    ```
- if you code:
    ```javascript
    console.log(typeof(Object))
    ```
   It returns "function" as result. This is because Javascript is a weakly typed language and with a great degree of freedom. JavaScript functions are called "high-order" or "first-class" and can, like objects, store attributes and methods.

- There is only one value in JavaScript that is not equal to itself - **NaN**. `NaN` is the result of a nonsensical computations and as such is not equal to another nonsensical computations.

- `null` and `undefined` are the equal in value but they have different types. They both represent the absence of any value.
    ```javascript
    null == undefined ; // true
    null === undefined; // false
    typeof undefined; // 'undefined'
    typeof null; // 'object'
    ```
- When null or undefined occurs on either side of the operator, it produces true only if both sides are one of null or undefined
    ```javascript
        false == undefined; // false
        undefined == null ; // true
    ```
- We can compare a value to null when we want to check if it has real value or not. `==` or `!=` should be used to check the presece of real value. Do not use `===` as it will result in false unless the values being compared to has the type *object*.

- There are 6 falsy values in JavaScript - `false`, `0`, `null`, `undefined`, `""` (empty strings), `NaN`. Other than these 6 all are truthy values.

- The `&&` and `||` operators in JavaScript tries to convert the value on their LHS (left hand side) to a boolean value and depending upon that value conversion they further decide what to do next. Depending upon the operator and result of conversion they either return the origin left hand value or right hand value

    #### || Operator
    ```javascript
        console.log('' || 'Hridayesh') ; // Hridayesh
    ```    
        In the above code the javascript first tries to convert '' into boolean and it converts to falsy value. Threfore the 'Hridayesh' is returned as the result
    ```javascript
        console.log('' || false); // false
    ```
        In this the RHS value also converts to false and this is what returned.
    ```javascript
        console.log('Hridayesh' || 'Sharma'); // 'Hridayesh'
    ```
    #### && Operator
    In case of && operator the first value is returned if it converts to boolean false and second value is not checked. The RHS value is checked only if the first value results into true value.
    ```javascript
        console.log(true && false); // false
        console.log(true && null); // null;
        console.log(null && true); // null
    ```
     **In short in case of || operator the LHS is returned if it converts to truthy value otherwise RHS value is returned. And in case of && operator the LHS is returned if it evaluates to falsy value otherwise the RHS value is returned.**

### Miscellaneous JS things
Did you ever try sorting a numerical array in javascript?
Try in console:
```javascript
let arrayToSort = [123, 8, 2];
arrayToSort.sort()
console.log(arrayToSort)
```

You will be surprised to see the output to be [123, 2, 8], because by default JS converts every element to string and sort them. Well, that's Javascript!
To fix this, or rather I would say to tweak it, we can do something like this.

```javascript
arrayToSort.sort((a, b)=>a-b);
console.log(arrayToSort)
```

The sort function takes a comparator function as argument which you can use to emulate different types of sortings.

Did you know that, in addition to being able to store functions in variables, you can declare them in an abbreviated form, similar to ternary operators? This type of declaration is called "Arrow Function". Here is an example:
The code:
```javascript
function sum(n1,n2) {
	return n1 + n2;
}
```
Is equal to this one, with arrow function:
```
const sum = (n1,n2) => n1+n2;
```