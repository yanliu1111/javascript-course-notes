# Free code camp questions

## section 2 JavaScript Fundamental Part1

[website]( https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/#basic-javascript)

[程序员free code camp学习体会](https://www.youtube.com/watch?v=t2AoIBEOtiE&list=PLYg5MzKmj0ImdbrgZ7PJNBVcG47c8dMsj&index=5)

### Basic JavaScript

Varibale name lowercase “firstname”/ camal case “firstName”

 ==NO== number in the front and & sign inside , or upper case in the front “Firstname”, this is only for OOD

illgeal, but never use “name” and “Person”“function”

I can use _ and $ sign in the front “_function”“​\$name”

Like very normal convention “Let PI = 3.1415”PI --> upper case

Cleaner code:  First set much better

```javascript
let myFirstJob ="Programmer";
let myCurrentJob ="Teacher";

let Job1 ="Programmer";
let Job2 ="Teacher";
```

LECTURE: Values and Variables
1. Declare variables called 'country', 'continent' and 'population' and
assign their values according to your own country (population in millions)
2. Log their values to the console

```javascript
let country = "China";
let continent = "Asia";
let population = 700;
console.log(country);
console.log(continent);
console.log(population);
```

	### Data type

Value : points to objective and primitive data

Primitive data: 7 data type : Number, string, bullion, undefined, null, symbol and big int

1. Number: Floating point numbers / use for decimals and integers

   :point_right:<u>let age = 23;</u> which means 23.0

2. String:  sequence of characters / Use for text  :point_right: <u>let firstName = ‘Yan’;</u>

3. Boolean: Logical type that can only be true or false / Used for taking decisions  :point_right: <u> let fullAge = true</u>;
4. Undefined: Value taken by a variable that is yet defined (‘empty value’) :point_right:<u>let children</u>
5. Null: Also means ‘empty value’
6. Symbol (ES2015) : Value that is unique and cannot be changed

7. BigInt (ES2020): Larger integers than the Number type can hold

:point_up: :JavaScript has dynamic typing: you dont have to manually define the data type of the value stored in a variable. Instead, data types are determined automatically.

For example, varibale x can initially be a number and then later a string, that’s not a problem at all. And this can of course be very useful but it can also be the source of some difficult to find books which means errors in our code.

### Comments

//   means comment line;         /* --- */  means comment block

comments / divid code zone / dont want to delete but not excute the code

```javascript
let javascriptIsFun = true;
console.log(typeof javascriptIsFun);
//boolean
javascriptIsFun = 'YES!';
console.log(typeof javascriptIsFun);
//string
```

==short cut key==: ctrl +/   : change to comment line

```javascript
console.log(typeof null);
//object
```

This is mistake in JS, should be undefined.

### Let Const Var

let : declare in the beginning, then we can change from boolean to string. Mutable variable

const: :point_right: <u>const brithYear =1991;</u>  then you cannot change to :point_right:  <u> brithYear =1990;</u> Immutable variable

so let can declare empty variable, but const cannot.

Teacher recommends SET CONST as possible as you can, no mutable variable less errors in your code.

==Use Const as much as possible==

Never do ==scope==, means not declare any name in the beginning, for example:

lastName = “Liu”;

console.log (lastName); This is no error in console,==but this is bad code!==

### Basic Operator

operator precedence,  check website:  [Mozilla JS Operator Precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)

```javascript
let x, y;
x=y=25-10-5;// 25-10-5 left to right; x=y=10 right to left
console.log(x,y);
```

** means exponentiation, for example: 2**3= 8

Logical thing: Value define from Right to Left

Assignment would be from Right to Left

Y= 10, then x =10

If Value define (assignment would be) from left to righr, not right

x and y are undefine, x=y would be error

Grouping: ()  parentheses  for example (a+b) / 2 is ==the highest precedence==

```javascript
//Math operators
const now = 2037;
const ageJonas = now - 1991;
const ageSarah = now - 2018;
console.log(ageJonas, ageSarah);

console.log(ageJonas * 2, ageJonas / 10, 2 ** 3);

const firstName = 'Jonas';
const lastName = ' Schmed';
console.log(firstName + lastName);

//Assignment operators
let x = 10 + 5; //15
x += 10; //x=x+10=25
x *= 4; // x=x*4 = 100
x++; //x=x+1=101
x--; //x=x-1=100

//Comparison operators for boolean
console.log(ageJonas > ageSarah); // <, >, >=, <=
console.log(ageSarah >= 18);

// It is better dont directly show results, it always load in a variable Name

const isFullAge = ageSarah >= 18;
//Smart JS, to decide isFullAge is boolean
console.log(now - 1991 > now - 2018);
// assignment sequencing is now-1991, then now -2018, then compare >
```

### Coding challenging #1

 ```javascript
const marksWeights = 78;
const marksHeight = 1.69;
const johnWeights = 92;
const johnHeight = 1.95;
const marksBMI = marksWeights / marksHeight ** 2;
// console.log(marksBMI);
const johnBMI = johnWeights / johnHeight ** 2;
// console.log(johnBMI);
// const markHigherBMI = marksBMI / johnBMI;
// console.log(markHigherBMI > 1);

const markHigherBMI = marksBMI > johnBMI;
console.log(marksBMI, johnBMI, markHigherBMI)
// If you change number, you still dont use let, you can use const.
// Just change number.
 ```

### Template literal

Use backticks, a lot of cleaner

Many developers actually started using backticks for all strings, because you dont have to think about which quotation marks you should use, you just use ==backticks==, ALWAYS!

```javascript
const firstName = 'Jonas';
const job = 'teacher';
const birthYear = 1991;
const year = 2037;

const jonas = "I'm " + firstName + ", a " + (year - birthYear) + " year old " + job + "!";
console.log(jonas);

const jonasNew = `I'm ${firstName}, a ${year - birthYear} year old ${job}!`;
console.log(jonasNew);

console.log(`Just a regular string ...`);

console.log('String with \n\
multiple \n\
line');

console.log(`String
multiple
line`);
```

### IF statement

```javascript
const age = 19;
// const isOldEnough = age >= 18;

if (age >= 18) {
    console.log(`Sarah can start driving license 🚙`)
}
```

```javascript
const age = 15;

if (age >= 18) {
    console.log(`Sarah can start driving license 🚙`)
} else {
    const yearLeft = 18 - age;
    console.log(`Sarah is too young, wait another ${yearLeft} years 😀`);
}
```

if (){

} else {

}

==Control structure==, which code block excute which doesnt excute

```javascript
const birthYear = 1998;

if (birthYear <= 2000) {
    let century = 20;
} else {
    let century = 21;
}
```

we have problem, I defined variable inside in code block, so i cannot get result outside console.log

So I have to put ==let== outside of block, then you can get console outside.

```javascript
const birthYear = 1998;
let century
if (birthYear <= 2000) {
    century = 20;
} else {
    century = 21;
}
console.log(century);
```

### Coding challenging 2 #

Practice if else statement

```javascript
const marksWeights = 78;
const marksHeight = 1.69;
const johnWeights = 92;
const johnHeight = 1.95;
const marksBMI = marksWeights / marksHeight ** 2;

const johnBMI = johnWeights / johnHeight ** 2;
console.log(marksBMI, johnBMI);
//const markHigherBMI = marksBMI > johnBMI;

if (marksBMI >= johnBMI) {
    console.log("Mark's BMI is higher than John's!");
} else {
    console.log("John's BMI is higher than Mark's!");
}
//using template literal to include the BMI values
if (marksBMI >= johnBMI) {
    console.log(`Mark's BMI (${marksBMI}) is higher than John's (${johnBMI})!`);
} else {
    console.log(`John's BMI (${johnBMI}) is higher than Mark's (${marksBMI})!`);
}
```

### Type conversion and  Coercion

JS can convert to number, string , and Boolean, but we cannot convert something undefined or to null. We just tried convert to number and string, not Boolean, because Bloonean behave in a special way. 

==contrentruitive== 矛盾的

```javascript
//type conversion
const inputYear = 1991;
console.log(typeof inputYear);
//number
const inputOtherYear = '1991';
console.log(Number(inputOtherYear), inputOtherYear);
console.log(Number(inputOtherYear) + 18);
console.log(Number('Jonas'));
console.log(typeof NaN);
//NaN is number, means invalid number

console.log(String(23), 23);
//not important part
//type coercion, means JS automatically convert data type in the scens
console.log('I am' + 23 + ' years old');
console.log('I am' + String(23) + ' years old');
//Confusing time, sometime convert, sometime not
console.log('23' - '10' - 3); //10
console.log('23' + '10' + 3); //23103
console.log('23' * '2'); //46, and same as dividing
```

### 21 Truthy and Falsy Values

5 falsy values : 0, ‘ ’, undefined, null, NaN

```javascript
console.log(Boolean(0)); //false, means falsy boolean
console.log(Boolean(undefined));//false
console.log(Boolean('Jonas'));//true, no empty string is truthy boolean
console.log(Boolean({}));//true, object
console.log(Boolean(''));//false

//very rare use, Jonas never used before
const money = 0;
if (money) {
    console.log(`Don't spend it all;)`);
} else {
    console.log(`You should get a job!`);
}

let height;
if (height) {
    console.log('YAY! Height is defined');
} else {
    console.log('Height is undefined');
}
```

### 22 Equality Operators: \==vs.===

===means strick equal operator

== (==this is loose equality operator==) does type coercion, for example‘18’==18; true; for clearner code, and avoid error in the code, use strick equal operator

```javascript
const favourite = Number(prompt("What is your favourite number?"));
console.log(favourite);
console.log(typeof favourite);
if (favourite === 23) { //23===23
    console.log('Cool! 23 is an amazing number!')
} else if (favourite === 7) {
    console.log('7 is also cool');
} else if (favourite === 9) {
    console.log('9 is also cool');
} else {
    console.log('Number is 23 or 7 or 9');
}

if (favourite !== 23) console.log('Why not 23?');
```

### 24 Logical Operators

```javascript
const hasDriverLicense = true;
const hasGoodVision = true;
console.log(hasDriverLicense && hasGoodVision);
console.log(hasDriverLicense || hasGoodVision);
console.log(!hasDriverLicense);

// if (hasDriverLicense && hasGoodVision) {
//     console.log('Sarah is able t drive!');
// } else {
//     console.log('Someone else should drive...');
// }

const isTired = false;
if (hasDriverLicense && hasGoodVision && !isTired) {
    console.log('Sarah is able to drive!');
} else {
    console.log('Someone else should drive...');
}
```

### Coding Challenging 3

==Win10: windows + .==

==show all emoji==

My answer, the best part I thought is ==sequence== . I put the < 100 && <100 at the first condition.

```javascript
let avgDolphins;
let avgKoalas;
avgDolphins = (82 + 112 + 103) / 3;
avgKoalas = (94 + 80 + 123) / 3;
console.log(avgDolphins);
console.log(avgKoalas);
// if (avgDolphins > avgKoalas) {
//     console.log('Dolphins team wins!');
// } else if (avgDolphins > avgKoalas) {
//     console.log('Koalas team wins!');
// } else {
//     console.log('Teams draw!');
// }
//Bonus 1
//Bonus 2

if (avgDolphins < 100 && avgKoalas < 100) {
    console.log('no team wins the trophy.');
} else if (avgDolphins > 100 && avgKoalas < 100) {
    console.log('Dolphins team wins!');
} else if (avgKoalas > 100 && avgDolphins < 100) {
    console.log('Koalas team wins!');
} else if (avgKoalas > 100 && avgDolphins > 100 && avgDolphins > avgKoalas) {
    console.log('Dolphins team wins!');
} else if (avgKoalas > 100 && avgDolphins > 100 && avgKoalas > avgDolphins) {
    console.log('Koalas team wins!');
} else {
    console.log('Teams draw!');
```

Tearcher answer

```javascript
// const scoreDolphins = (96 + 108 + 89) / 3;
// const scoreKoalas = (88 + 91 + 110) / 3;
// console.log(scoreDolphins, scoreKoalas);
// if (scoreDolphins > scoreKoalas) {
//     console.log('Dolphins win the trophy🏆');
// } else if (scoreDolphins < scoreKoalas) {
//     console.log('Koalas win the trophy🏆');
// } else if (scoreDolphins === scoreKoalas) {
//     console.log('Both win the trophy');
// }

const scoreDolphins = (96 + 108 + 89) / 3;
const scoreKoalas = (88 + 91 + 110) / 3;
console.log(scoreDolphins, scoreKoalas);
if (scoreDolphins > scoreKoalas && scoreDolphins >= 100) {
    console.log('Dolphins win the trophy🏆');
} else if (scoreDolphins < scoreKoalas && scoreKoalas >= 100) {
    console.log('Koalas win the trophy🏆');
} else if (scoreDolphins === scoreKoalas && scoreDolphins >= 100 && scoreKoalas >= 100) {
    console.log('Both win the trophy');
} else {
    console.log('No one wins the trophy 😥');
}
```

### 26 The switch statement

<u>Switch is less and less use now, but for this example, switch statement is more readable.</u>

```javascript
const day = 'Wednesday';
switch (day) {
    case 'Monday': //day === 'Monday'
        console.log('Plan course structure');
        console.log('Go to coding meetup');
        break;
    case 'Tuesday':
        console.log('Prepare theory videos');
        break;
    case 'Wednesday':
    case 'Thursday':
        console.log('Write code examples');
        break;
    case 'Friday':
        console.log('Record videos');
        break;
    case 'Saturday':
    case 'Sunday':
        console.log('Enjoy the weekend');
        break;
    default:
        console.log('Not a valid day!');
}
```

```javascript
const day = 'Wednesday';
if (day === 'Monday') {
    console.log('Plan course structure');
    console.log('Go to coding meetup');
} else if (day === 'Tuesday') {
    console.log('Prepare theory videos');
} else if (day === 'Wednesday' || day === 'Thursday') {
    console.log('Write code examples');
} else if (day === 'Friday') {
    console.log('Record videos');
} else if (day === 'Saturday' || day === 'Sunday') {
    console.log('Enjoy the weekend');
} else {
    console.log('Not a valid day!');
}
```

###  27 Statements and Expressions

Expressions produce values,  and the statements are like full sentences that translate our actions.

The actions mean you want the program to perform.

for example,  const str = ‘23 is bigger’; ==end with ; means statement, it didnt produce value, it wants to perform the code==

JS wants put statement and expressions in different places.

### 28 	Ternary operator 三元运算符

```javascript
const age = 23;
// age >= 18 ? console.log('I like to drink wine🍷') :
//     console.log('I like to drink water🥛');

const drink = age >= 18 ? 'wine🍷' : 'water🥛';// drink = expression, becasue produce a value
console.log(drink);

let drink2; //have to declare outside of block
if (age >= 18) {
    drink2 = 'wine🍷'; // then reassign in the block
} else {
    drink2 = 'water🥛';
}
console.log(drink2);
console.log(`I like to drink ${age >= 18 ? 'wine🍷' : 'water🥛'}`);
```

==Mention== that the ternary operator is not thought as a replacement of if/else statements. We still need if/else all the time. For example, when we have bigger blocks of code that we need to execute based on a condition. In that case the ternary operator is not gonna work.

But ternary operator is good option, when we need to take a quick decision.

And that’s especially true in places where JS really expects an expression, just like here in this template literal. 

```javascript
console.log(`I like to drink ${age >= 18 ? 'wine🍷' : 'water🥛'}`);
```

### Coding Challenging 4

```javascript
//ifstatement
const bill = 40;
	if (bill >= 50 && bill <= 300) { console.log(`The bill was ${bill}, the tip was ${bill * 0.15}, and the total value ${bill * 1.15}`); }
	else { console.log(`The bill was ${bill}, the tip was ${bill * 0.2}, and the total value ${bill * 1.2}`); }

//Ternary operator
const bill = 40;
const tip = bill <= 300 && bill >= 50 ? bill * .15 : bill * .2;
console.log(`The bill was ${bill}, the tip was ${tip}, and the total value ${bill + tip}`);
```























































































