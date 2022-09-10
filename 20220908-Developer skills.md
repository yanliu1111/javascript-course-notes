# Section 5: Developer Skills & Editor Setup

[Prettier.io](https://prettier.io/docs/en/options.html)

```javascript
"Print to console": {
    "scope": "javascript,typescript",
    "prefix": "cl",
    "body": ["console.log();"],
    "description": "Log output to console"
  }
```

**user snippets**

### 54 Installing Node.js and Setting up a Dev Environment

- click ==go live== on the VS code bottom, your url is 127.0.0.1:5500

  ```
  npm install live-server -g
  ```

- ==npm== is the Node Package manager, which is basically a program to download tools. -g means it should be installed globally. 

==cls== clean terminal

[VS code Error - “Excution of script is disabled on this system”](https://www.youtube.com/watch?v=X7mg3pJfhZQ)

### 55 How to think like a developer

1. Make sure you 100% understand the problem. **Ask the right questions** to get a clear picture of the problem

   - Example: Project manager “we need a function that reverses <u>whatever</u> we pass into into it”
     - What does “whatever”even mean in this context? what should be reversed? Answer: Only strings, numbers, and arrays make sense t reverse...
     - What to do if something else is passed in?
     - What should be returned? Should it always be a string, or should the type be the same as passed in?
     - How to recognize whether the argument is a number, a string, or an array?
     - How to reverse a number , a string, and an array?

2. **Divide and conquer:** Breaking a big problem into smaller sub-problems.

   - SUB-PROBLEM:

     👉 Check if argument is a number, a string, or an array

     👉 Implement reversing a number

     👉 Implement reversing a String

     👉 Implement reversing an array

     👉 Return reversed value

     (Looks like a task list that we need to implement)

3. Don’t be afraid to do as much **research** as you have to 

- USE WEB POWER: **Google**, **Stack overflow**, **MDN web docs moz://a**

👉  How to check if a value is a number in JavaScript?

👉 How to check if a value is a String in JavaScript?

👉 How to check if a value is an array in JavaScript?

👉 How to reverse a number in JavaScript?

👉 How to reverse a string in JavaScript?

👉 How to reverse a array in JavaScript?

4. For bigger problems, **write pseudo-code** before writing the actual code

   ```pseudocode
   function reverse(value)
   	if value type !string && !number && !arrary
   	return value
   	
   	if value type == sting
   	reverse string
   	if value type == number
   	reverse number
   	if value type == array
   	reverse array
   	
   return reversed value
   ```

   set pseudo-code 👆

### 59 Using web power (thinking process)

2)Breaking up into sub-problems

\- How to ignore errors?

\- Find max value in temp array?

\- Find min value in temp array?

\- Substract min from max (amplitude) and return it

- Step1 Checking stack overflow and set finding max code

```javascript
const temperatures = [3, -2, -6, -1, 'error', 9, 13, 17, 15, 14, 9, 5];

const calcTempAmplitude = function (temps) {
  let max = temps[0];
  for (let i = 0; i < temps.length; i++) {
    if (temps[i] > max) max = temps[i];
  }
  console.log(max);
};
calcTempAmplitude([3, 7, 4]);
```

- Step2 set max and min

```
const calcTempAmplitude = function (temps) {
  let max = temps[0];
  let min = temps[0];
  for (let i = 0; i < temps.length; i++) {
    const curTemp = temps[i];
    if (curTemp > max) max = curTemp;
    if (curTemp < min) min = curTemp;
  }
  console.log(max, min);
};
calcTempAmplitude([3, 7, 4, 9, 1]);
```

- Step3 kick out error

```javascript
const calcTempAmplitude = function (temps) {
  let max = temps[0];
  let min = temps[0];
  for (let i = 0; i < temps.length; i++) {
    const curTemp = temps[i];
    if (typeof curTemp !== 'number') continue;
    if (curTemp > max) max = curTemp;
    if (curTemp < min) min = curTemp;
  }
  console.log(max, min);
};
calcTempAmplitude([3, 7, 4, 9, 1]);
calcTempAmplitude(temperatures);
```

- Step4 return ampplitude: means subract min from max and return it

```javascript
const calcTempAmplitude = function (temps) {
  let max = temps[0];
  let min = temps[0];
  for (let i = 0; i < temps.length; i++) {
    const curTemp = temps[i];
    if (typeof curTemp !== 'number') continue;
    if (curTemp > max) max = curTemp;
    if (curTemp < min) min = curTemp;
  }
  console.log(max, min);
  return max - min;
};

const amplitude = calcTempAmplitude(temperatures);
console.log(amplitude);
```

Problem 2: Function should now receive 2 arrays of temps

1) understanding the problem

with 2 arrays, should we implement functionality twice?

==NO, just merge two arrays==

2) sub-problems

Merge 2 arrays - check website

```javascript
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);
```

```javascript
//Concat problem

const calcTempAmplitudeNew = function (t1, t2) {
  const temps = t1.concat(t2);
  console.log(temps);

  let max = temps[0];
  let min = temps[0];
  for (let i = 0; i < temps.length; i++) {
    const curTemp = temps[i];
    if (typeof curTemp !== 'number') continue;
    if (curTemp > max) max = curTemp;
    if (curTemp < min) min = curTemp;
  }
  console.log(max, min);
  return max - min;
};

const amplitudeNew = calcTempAmplitudeNew([3, 1, 4], [9, 0, 5]);
console.log(amplitudeNew);
```

### 60 Debugging

```javascript
const measureKelvin = function () {
  const measurement = {
    type: 'temp',
    unit: 'celsius',
    // C. Fix
    //value: Number(prompt('Degrees celsius:')),
    value: 10,
  };
  // B. Find!
  console.log(measurement);
  console.table(measurement);
  //console.log(measurement.value);
  //console.warn(measurement.value);
  //console.error(measurement.value);

  const kelvin = measurement.value + 273;
  return kelvin;
};
// A. Identify
console.log(measureKelvin());
```

Debugging from Chrome

```javascript
//using for debugger
const calcTempAmplitudeBug = function (t1, t2) {
  const temps = t1.concat(t2);
  console.log(temps);

  let max = 0;
  let min = 0;
  for (let i = 0; i < temps.length; i++) {
    const curTemp = temps[i];
    if (typeof curTemp !== 'number') continue;

    debugger;
    if (curTemp > max) max = curTemp;
    if (curTemp < min) min = curTemp;
  }
  console.log(max, min);
  return max - min;
};

const amplitudeBug = calcTempAmplitudeBug([3, 5, 1], [9, 4, 5]);
console.log(amplitudeBug);
```



















