# JavaScript Fundamentals - Part2

### 32 Activating Strict Mode

1. More secure mode, Strict mode forbids us to do certain things 
2. it will actually ==create visible errors== for us in certain situations in which without strict mode. JS simply fail silently without letting us know that we did a mistake.

‘use strict’;    MUST in the beginning of whole codes

```javascript
'use strict'; // more secure code
let hasDriversLicense = false;
const passTest = true;

if (passTest) hasDriversLicense = true;
if (hasDriversLicense) console.log('I can drive');

//const interface = 'Audio';
//const private = 534;
//const if=234; reserve words cannot be delared variable names
```

### 33 Functions

==Not all function need to return something==

==And not all functions need to accept parameters==

```javascript
function logger() {
    console.log('My name is Jonas');
}
logger();// becasue () is empty, we dont specify any arguments
logger();
logger();
```

If function without parameters and return, no useful, we only use where where is a block of code, that we want to reuse over and over again. 

Once again, the first code doesn’t return anything, all it does its to log something to the console, but that has nothing to do with returning a value. This only for printing to developer console but doesn’t return a value.  So we doesn’t need to save the result function to any variable. We don’t capture that undefined value.

==Return==: now we can use the return keyword and with this, we can return any value from the function. In this, let’s actually return the juice that we produced. So this value that we then return  can be used anywhere later in our code.

The juice will become  the result of executing this functions. 

```javascript
function fruitProcessor(apples, oranges) {
    console.log(apples, oranges);// Can be canceled
    const juice = `Juice with ${apples} apples and ${oranges} oranges.`;
    return juice;
}
fruitProcessor(5, 0);
//console.log(apples, organes) shows two values of the functions parameters. When the function running, then we use these two values to build this juice string. Then we return that string value from the function. So the REAL result of the function is the return value. 
//If you want to use the return result, you need to store it in a variable.
// we need capture the result from the function, we can set a vriable or we can directly use console.log
const appleJuice = fruitProcessor(5, 0);
console.log(appleJuice);
console.log(fruitProcessor(5, 0));

const appleOrangeJuice = fruitProcessor(2, 4);
console.log(appleOrangeJuice);
```

```javascript
const num = Number ('23'); //convert string to number, building function
```

### 34 Function Declarations Vs. Expressions
