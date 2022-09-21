

# JavaScript Algorithms and Data Structure

### ES6

```javascript
function checkScope() {
  "use strict";
  let i = "function scope";
  if (true) {
    let i = "block scope";
    console.log("Block scope i is: ", i);
  }
  console.log("Function scope i is: ", i);
  return i;
}
```

~~Question1:~~ “use strict”is put in the beginning of the code.

Done! React is very strict, if you type “use strict”, your code is very strict. Cannot appear x=5; ==Must== be let x=5; 

Question2: nmp install live-server package, no different between nvm and node.js

```javascript
const s = [5, 7, 2];
function editInPlace() {
  // Only change code below this line
  s.unshift(s.pop());
  console.log(s);

  // Using s = [2, 5, 7] would be invalid

  // Only change code above this line
}
editInPlace();
```

Up solution is Better than 👇

```javascript
const s = [5, 7, 2];
function editInPlace() {
  "use strict";
  s[0] = 2;
  s[1] = 5;
  s[2] = 7;
}
editInPlace();
```

### try catch finally

- `try...catch`
- `try...finally`
- `try...catch...finally`

You can create "Conditional `catch`-blocks" by combining `try...catch` blocks with `if...else if...else` structures, like this:

```javascript
try {
  myroutine(); // may throw three types of exceptions
} catch (e) {
  if (e instanceof TypeError) {
    // statements to handle TypeError exceptions
  } else if (e instanceof RangeError) {
    // statements to handle RangeError exceptions
  } else if (e instanceof EvalError) {
    // statements to handle EvalError exceptions
  } else {
    // statements to handle any unspecified exceptions
    logMyErrors(e); // pass exception object to error handler
  }
}
```

A common use case for this is to only catch (and silence) a small subset of expected errors, and then re-throw the error in other cases:

```javascript
try {
  myRoutine();
} catch (e) {
  if (e instanceof RangeError) {
    // statements to handle this very common expected error
  } else {
    throw e;  // re-throw the error unchanged
  }
}
```

###  Array.reduce()

```javascript
const array1 = [1, 2, 3, 4];

// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);

console.log(sumWithInitial);
// expected output: 10

```

###  (...args)

```javascript
const sum = (...args) => {
  return args.reduce((a, b) => a + b, 0);
  // const args = [x, y, z];
  // return args.reduce((a, b) => a + b, 0);
}
// agrs.length
```

###  Assign Variables from Nested Objects

```javascript
const LOCAL_FORECAST = {
  yesterday: { low: 61, high: 75 },
  today: { low: 64, high: 77 },
  tomorrow: { low: 68, high: 80 }
};

  
// const lowToday = LOCAL_FORECAST.today.low;
// const highToday = LOCAL_FORECAST.today.high;
const{today:{low:lowToday, high:highToday}}=LOCAL_FORECAST;
```





















