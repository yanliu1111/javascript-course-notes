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

```javascript
//Function declaration
function calcAge1(birthYear) {
    return 2037 - birthYear;
}
const age1 = calcAge1(1991);

//Function expression: anonymous function, all of this below is expression
const calcAge2 = function (birthYear) {
    return 2037 - birthYear;
} // expression produces a value that value in store it into calcAge2
const age2 = calcAge2(1991);
console.log(age1, age2);
```

- Set a calcAge2 variable, this variable holds all function value.

- Function just as a number or a string or a Boolean value

- Function is not type, not like a string or number type.

- Big different,  we can call the function declaration in the beginning, then define a function next. It works. This is happening, because of a process called <u>hoisting</u> 吊装. Even it might not be such a good idea in many cases.

- ```javascript
  const age1 = calcAge1(1991);
  
  function calcAge1(birthYear) {
      return 2037 - birthYear;
  }
  ```

- But function express cannot reverse the sequence.

- ==Different developers prefer different formats, depends on you. Teacher likes function expressions. It forces me a nice structure where I have to define all the functions first at the top of the code and only then I can call them==

- A good habit, I like to store everything in variables. Both values and functions.

### 35 Arrow Functions

```javascript
const calcAge3 = birthYear => 2037 - birthYear;
const age3 = calcAge3(1991);
console.log(age3);
```

The return actually happens <u>implicitly</u>含蓄地 Without having to<u> explicitly</u> 明确的write the return keyword. Excellent one line function

```javascript
const yearUntilRetirement = (birthYear, firstName) => {
    const age = 2037 - birthYear;
    const retirement = 65 - age;
    //return retirment;
    return `${firstName} retires in ${retirement} years`;
}
console.log(yearUntilRetirement(1991, 'Jonas'));
console.log(yearUntilRetirement(1980, 'Bob'));
```

### 36 Functions calling other Functions

![2Capture20220906](../Typora Note/pic/2Capture20220906.JPG)

```javascript
function cutFruitPieces(fruit) {
    return fruit * 4;
}
function fruitProcessor(apples, oranges) {
    const applePieces = cutFruitPieces(apples);
    const orangePieces = cutFruitPieces(oranges);

    const juice = `Juice with ${applePieces} pieces of apple and ${orangePieces} pieces of orange.`;
    return juice;
}
console.log(fruitProcessor(2, 3));
```

### 37 Functions Summary

![Capture20220906](../Typora Note/pic/Capture20220906.JPG)

![1662497454309](../Typora Note/pic/1662497454309.png)

Make clear about ==console.log== and ==return==

“console.log” in the function, has nothing to do with returning a value.

This simply prints a message to the developer console,  but it has nothing to do with returning. “console.log” is another function call inside the calcAge function.

We always use “console.log”is because we want to see the results of our experiments in the developer console, in the browser.

### 38 Coding Challenge #1

```javascript
const calcAverage = (a, b, c) => (a + b + c) / 3;
let scoreDolphins = calcAverage(44, 23, 71);
let scoreKoalas = calcAverage(65, 54, 49);
// console.log(avgDolphins, avgKoalas);

const checkWinner = function (avgDolphins, avgKoalas) {
    console.log(avgDolphins, avgKoalas);
    if (avgDolphins >= 2 * avgKoalas) {
        console.log(`Dolphins win 🎀(${avgDolphins} vs. ${avgKoalas})`);
    } else if (avgKoalas >= 2 * avgDolphins) {
        console.log(`Koalas win 💎(${avgKoalas} vs. ${avgDolphins})`);
    }
    else { console.log(`No team wins!`) }
}
//test 1
checkWinner(scoreDolphins, scoreKoalas);
checkWinner(55, 111);
//test 2
scoreDolphins = calcAverage(85, 54, 41);
scoreKoalas = calcAverage(23, 34, 27);
checkWinner(scoreDolphins, scoreKoalas);
```

### 39 Introduction to Arrays

const friends, immutable. But I was still able to change one element.

==Is it contradiction?== that is only primitive values, are immutable. But ==an Array is not a primitive value==. So we can mutate it. 

```javascript
const friends = ['Noah', 'Mike', 'Peter'];
console.log(friends);
//Another way
const years = new Array(1991, 1984, 1998, 2020);
//array is function, new is necessary
console.log(friends[0]);
console.log(friends[2]);

console.log(friends.length); //length is object
console.log(friends[friends.length - 1]);
//friend.length-1 is a expression, is not statement
friends[2] = 'Jay';
console.log(friends);
// I can change an element, because an Array is not primitive value. But I cannot use friends = ['Allice','May'];
const firstName = 'Jonas';
const jonas = [firstName, 'Schmedtmann', 2037 - 1991, 'teacher', friends];
console.log(jonas);
console.log(jonas.length);
const calcAge = function (birthYear) {
    return 2037 - birthYear;
}
const age1 = calcAge(years[0]);//shift+alt+up
const age2 = calcAge(years[1]);//expression
const age3 = calcAge(years[years.length - 1]);
console.log(age1, age2, age3);

const ages = [calcAge(years[0]), calcAge(years[1]), calcAge(years[years.length - 1])];
console.log(ages);
```

### 40 Basic Array Operations (methods)

```javascript
//add elements
const friends = ['Noah', 'Mike', 'Peter'];
const newlength = friends.push('Jay'); //normally we dont do this
//friends.push('Jay');
console.log(friends); //jay push in the array end
console.log(newlength);

friends.unshift('John');
console.log(friends);

//remove elements
friends.pop();//last
const popped = friends.pop();
console.log(popped);
console.log(friends);

friends.shift();//first
console.log(friends);

console.log(friends.indexOf('Noah'));
console.log(friends.indexOf('Bob'));

console.log(friends.includes('Noah')); //true
console.log(friends.includes('Bob')); //false

friends.push(23);
console.log(friends.includes('23'));//false, data type and string type, no type coercion

if (friends.includes('Steven')) {
    console.log(`you have a friend called Steven`)
} // nothing happened
```

### 41 Coding Challenge #2

```javascript
const calcTip = function (bills) {
    // console.log(bills)
    if (bills >= 50 && bills <= 300) {
        console.log(`${bills * 0.15}`);
    } else {
        console.log(`${bills * 0.2}`);
    }
}
calcTip(100);

const bills = [125, 555, 44];
// calcTip(bills[0])
const tips = [calcTip(bills[0]), calcTip(bills[1]), calcTip(bills[2])];
console.log(tips[0]);
```

My solution, console.log has problem, the tips array undefined.

```javascript
const bills = [125, 555, 44]
const tips = [];
const total = [];

let index = 0;
const calcTip = (bill) => {

    if (bill[index] >= 50 && bill[index] <= 300) {
        tips.push(bill[index] * 0.15);
    } else {
        tips.push(bill[index] * 0.2);
    }
    total.push(bills[index] + tips[index])
    index++;
    if (index === bill.length) {
        index = 0;
        return;
    } else {
        calcTip(bills);
    }
}

calcTip(bills);
console.log(tips, total);
```

==Student’s super cool solution!==

```javascript
const calcTip = function (bill) {
    return bill >= 50 && bill <= 300 ? bill * 0.15 : bill * 0.2
}
// const calcTip = bill => bill>=50 && bill<=300? bill *0.15 : bill*0.2;

const bills = [125, 555, 44];
// calcTip(bills[0])
const tips = [calcTip(bills[0]), calcTip(bills[1]), calcTip(bills[2])];
const totals = [bills[0] + tips[0], bills[1] + tips[1], bills[2] + tips[2]];
console.log(bills, tips, totals);
```

From course solution,

### 42 Objects, data structure type

We use curly brackets or curly braces { } , here define new objects, inside key value pairs

`Before: if else statement; switch statement; defined a function body`

The big different from Objects and Arrays:  The order of these values doesn’t matter at all when we want to <u>retrieve</u>取回 them. 

In Arrays, the order in which we specify the elements ==matters a lot==, how we access the elements.

Objects for more unstructured data, and Arrays for more order data

```javascript
const jonasArray = [
    'Jonas',
    'Schmed',
    2037 - 1991,
    'teacher',
    ['Michael', 'Peter', 'Steven']
]

//the objects define five key value pairs
const jonas = {
    firstName: 'Jonas',
    lastName: 'Schmed',
    age: 2037 - 1991,
    job: 'teacher',
    friends: ['Michael', 'Peter', 'Steven']
};
```

- Five keys, each key has value, each of this key called property

- Here, we called Jonas has five properties

- It is called object literal Syntax

### 43 Dot vs Bracket Notation

```javascript
const jonas = {
    firstName: 'Jonas',
    lastName: 'Schmed',
    age: 2037 - 1991,
    job: 'teacher',
    friends: ['Michael', 'Peter', 'Steven']
}
console.log(jonas);
console.log(jonas.lastName);
console.log(jonas['lastName']);

const nameKey = 'Name';
console.log(jonas['first' + nameKey]);
console.log(jonas['last' + nameKey]);
// [] contact with compute name
const interestedIn = prompt('what do you want to know jonas? Choose between firstName lastName age job and friends');
```

`console.log(jonas.interestedIn);`

- Undefined, undefined was what we get when we try to access a property on an object that does not exist.

- Trying to access 'interestedIn' on Jonas is undefined.

- Instead of dot expression, we use []

`console.log(jonas[interestedIn]);`

- [] needs asking compute, but dot means directly show the value.

- If I put location, there is no jonas.location property, so the result is undefined



- undefined means false results

```javascript
if (jonas[interestedIn]) {
    console.log(jonas[interestedIn]);
} else {
    console.log(`Wrong request! Choose between firstName lastName age job and friends`)
}

jonas.location = 'Portugal';
jonas['twitter'] = '@jonasschmedtman';
console.log(jonas);
```

#### Challenge

"Jonas has 3 friends, and his best friend is called Micheal"

```javascript
//Challenge
const bestFriend = jonas.friends[0];
const numFriend = jonas.friends.length;
const jonasName = jonas.firstName;
console.log(`${jonasName} has ${numFriend} friends, and his best friend is called ${bestFriend}`);
```

**Note:** check website mdn operator, ==[GO to develper.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)==

| Operater type          | Associativity | individual operators |
| :--------------------- | ------------- | -------------------- |
| Member Access          | left to right | ...  **.**   ...     |
| Computed Member Access | left to right | ...  [ .... ]        |

















