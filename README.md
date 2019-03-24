# JS-TIPS

## **JS-TIPS** is a collections of *byte sized JavaScript tips* which I found during my journey of learning JavaScript. The complete guide is divided into multiple sections.

### Values in JavaScript

- Numbers in JavaScript are 64 bits which include all of integers (both positive and negative), decimal numbers.

- There are 6 types of values in JavaScript, ES6 adds one more called Symbols
    * Numbers
    * Booleans
    * Strings
    * Objects
    * Functions
    * Objects

- `Infinity`, -`Infinity` and `NaN` are special type of Number values.
    Infinity - Infinity // NaN
    Infinity / Infinity // NaN
    Infinity + Infinity // Infinity
    Infinity * Infinity // Infinity

- `typeof` operator gives the type of a value in string.
    console.log(typeof (typeof 'str')); // 'string'

- There is only one value in JavaScript that is not equal to itself - **NaN**. `NaN` is the result of a nonsensical computations and as such is not equal to another nonsensical computations.

- `null` and `undefined` are the equal in value but they have different types. They both represent the absence of any value.
    null == undefined ; // true
    null === undefined; // false
    typeof undefined; // 'undefined'
    typeof null; // 'object'

- When null or undefined occurs on either side of the operator, it produces true only if both sides are one of null or undefined
    false == undefined; // false
    undefined == null ; // true

- We can compare a value to null when we want to check if it has real value or not. `==` or `!=` should be used to check the presece of real value. Do not use `===` as it will result in false unless the values being compared to has the type *object*.

- There are 6 falsy values in JavaScript - `false`, `0`, `null`, `undefined`, `""` (empty strings), `NaN`. Other than these 6 all are truthy values.

- The `&&` and `||` operators in JavaScript tries to convert the value on their LHS (left hand side) to a boolean value and depending upon that value conversion they further decide what to do next. Depending upon the operator and result of conversion they either return the origin left hand value or right hand value

    #### || Operator
    console.log('' || 'Hridayesh') ; // Hridayesh
    In the above code the javascript first tries to convert '' into boolean and it converts to falsy value. Threfore the 'Hridayesh' is returned as the result

    console.log('' || false); // false
    In this the RHS value also converts to false and this is what returned.

    console.log('Hridayesh' || 'Sharma'); // 'Hridayesh'
    #### && Operator
    In case of && operator the first value is returned if it converts to boolean false and second value is not checked. The RHS value is checked only if the first value results into true value.

    console.log(true && false); // false
    console.log(true && null); // null;
    console.log(null && true); // null
    
     **In short in case of || operator the LHS is returned if it converts to truthy value otherwise RHS value is returned. And in case of && operator the LHS is returned if it evaluates to falsy value otherwise the RHS value is returned.**


