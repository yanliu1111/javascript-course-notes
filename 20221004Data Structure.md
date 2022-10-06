# Section9: Data Structure, Mordern Operators and Strings

### 103 Destructuring Arrays

```javascript
const arr = [2, 3, 4];
const a = arr[0];
const b = arr[1];
const c = arr[2];

const [x, y, z] = arr;
console.log(x, y, z);
console.log(arr);

let [main, , secondary] = restaurant.categories;
console.log(main, secondary);
//Italian Vegetarian

//now I want to switching variables
// const temp = main;
// main = secondary;
// console.log(main, secondary);
//Vegetarian Vegetarian

//using destructuring
[main, secondary] = [secondary, main];
console.log(main, secondary);

const [starter, mainCourse] = restaurant.order(2, 0);
console.log(starter, mainCourse);

const nested = [2, 4, [5, 6]];
// const [i, , j] = nested;
// console.log(i, j);
const [i, , [j, k]] = nested;
console.log(i, j, k);
//default values
const [p = 1, q = 1, r = 1] = [8];
console.log(p, q, r);
```

default values would use in API

### 104 Destructuring Objects

Especially when we deal with the result of an API call, which basically means to get data from other web application, like weather data or data about movies or something like that. This data usually comes in the form of objects basically. And this destructuring is  lifesaver, it allows us to write a lot less code. 

```javascript
const { name, openingHours, categories } = restaurant;
console.log(name, openingHours, categories);
//give a new variable name
const {
  name: restaurantName,
  openingHours: hours,
  categories: tags,
} = restaurant;
console.log(restaurantName, hours, tags);

// menu=[], give a default value at the begining, incase it does not exist
const { menu = [], starterMenu: starters = [] } = restaurant;
console.log(menu, starters);
//
let a = 111;
let b = 999;
const obj = { a: 23, b: 7, c: 14 };
//{a,b}=obj, {}means in code block, so using ()
// ({ a, b } = obj);
console.log(a, b);

//nested objects
const {
  fri: { open: o, close: c },
} = openingHours;
console.log(o, c);
```

```js
const restaurant = {
...
...
oderDelivery: function (obj) {
    console.log(obj);
  },
};
restaurant.oderDelivery({
  time: '22:30',
  address: 'Via del Sole, 21',
  mainIndex: 2,
  starterIndex: 2,
});
```

```javascript
const restaurant = {
...
...
oderDelivery: function ({ starterIndex, mainIndex, time, address }) {
    console.log(
      `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delieved to ${address} at ${time}`
    );
  },
};
restaurant.oderDelivery({
  time: '22:30',
  address: 'Via del Sole, 21',
  mainIndex: 2,
  starterIndex: 2,
});
```

==it is important to realize, we ONLY passed in on object into this function.  We DIDN’T pass four arguments.==

It is only one argument, one object.

`function ({ starterIndex, mainIndex, time, address })`when we receive this one object,  we do immediately destructuring. 

在object裏的順序無關

Set default value in the beginning,

```javascript
oderDelivery: function ({
    starterIndex = 1,
    mainIndex = 0,
    time = '20:20',
    address,
  }) {
    console.log(
      `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delieved to ${address} at ${time}`
    );
  },
};
```

### 105 The Spread Operator (...)

... like taking all the elements out of the array and writing them here manually

```javascript
const arr = [7, 8, 9];
const badNewArr = [1, 2, arr[0], arr[1], arr[2]];
console.log(badNewArr);

const newArr = [1, 2, ...arr];
console.log(newArr);
console.log(...newArr);

const newMenu = [...restaurant.mainMenu, 'Gnocii'];
console.log(newMenu);
//copy array
const mainMenuCopy = [...restaurant.mainMenu];
//Join 2 arrays
const menu = [...restaurant.mainMenu, ...restaurant.starterMenu];
console.log(menu);
```

What is an iterable?

Iterable are things like all arrays, strings, maps, or sets, BUT not objects.

Most of buildin structures in JS, are now iterables, but except objects.

We can only use ... build in array, or pass value to a function

```javascript
//iterables: arrays, strings, maps, sets. But not objects
const str = 'Jonas';
const letters = [...str, ' ', 'S.'];
console.log(letters);//['J', 'o', 'n', 'a', 's', ' ', 'S.']
console.log(...str); //J o n a s
```



```javascript
const restaurant = {
...
...
...
orderPasta: function (ing1, ing2, ing3) {
    console.log(`Here is your declicious pasta with ${ing1},${ing2},${ing3}`);
  },
};
const ingredients = [
  prompt("Let's make pasta! Ingredient 1?"),
  prompt('Ingredient 2?'),
  prompt('Ingredient 3?'),
];
console.log(ingredients);
restaurant.orderPasta(ingredients[0], ingredients[1], ingredients[2]);
restaurant.orderPasta(...ingredients);
```

Object

```javascript
//Objects
const newRestaurant = { foundIn: 1998, ...restaurant, founder: 'Guiseppe' };
console.log(newRestaurant);

const restaurantCopy = { ...restaurant };
restaurantCopy.name = 'Rostorante Roma';
console.log(restaurantCopy.name);// Rostorante Roma
console.log(restaurant.name);//Classico Italiano
```

Jassica2 和 JassicaCopy lastname 在object.assign 裏一個不變，一個變化，但是控制不了deep clone，兩個一起變，指向同一個heap address

### 106 Rest pattern and Parameters



































