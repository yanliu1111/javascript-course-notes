# JS Array Methods

```javascript
const companies = [
  { name: "Company One", category: "Fincance", start: 1981, end: 2003 },
  { name: "Company Two", category: "Retail", start: 1992, end: 2008 },
  { name: "Company Three", category: "Auto", start: 1999, end: 2007 },
  { name: "Company Four", category: "Retail", start: 1989, end: 2010 },
  { name: "Company Five", category: "Technology", start: 2009, end: 2014 },
  { name: "Company Six", category: "Finance", start: 1987, end: 2010 },
  { name: "Company Seven", category: "Auto", start: 1986, end: 1996 },
  { name: "Company Eight", category: "Technology", start: 2011, end: 2016 },
  { name: "Company Night", category: "Retail", start: 1981, end: 1989 },
];
const ages = [33, 12, 20, 16, 5, 54, 21, 44, 61, 13, 15, 45, 25, 64, 32];
```

### 1. for loop

```javascript
for (let i = 0; i < companies.length; i++) {
  console.log(companies[i]);
```

### 2. forEach

- forEach, it is sync, not async callback function

- function(element, index, array) same as many array functions

- same as for loop, looks nicer than for loop, no i=0 setting

- console.log, you can only show company.name for each object in array

```javascript
companies.forEach(function (Company) {
  console.log(Company.name);
});
```

### 3. filter

**get ages array higher and equal than 21**

```javascript
let canDrink = [];
for (let i = 0; i < ages.length; i++) {
  if (ages[i] >= 21) {
    canDrink.push(ages[i]);
  }
}
```

age is element position (element, index, array), it is declared by the function design

```javascript
const canDrink = ages.filter(function (age) {
  if (age >= 21) {
    return true;
  }
});
console.log(canDrink);
```

The => function, lamba

```javascript
const canDrink = ages.filter (age=> age >=21);
```

**Filter the retail companies**

```javascript
const retailCompanies = companies.filter(function (company) {
  if (company.category === "Retail") {
    return true;
  }
});
```



```javascript
const retailCompanies = companies.filter(company => company.category === "Retail");
console.log(retailCompanies);
```

if you ask two param (element, index), if only element we dont need (element)

```javascript
const retailCompanies = companies.filter(
  (company, index) => company.category === "Retail"
);
console.log(retailCompanies);
```

**Get 80s companies**

```javascript
const eightiesCompanies = companies.filter(
  (company) => company.start >= 1980 && company.start < 1990
);
console.log(eightiesCompanies);
```

**Companies less than 10years**

```javascript
const lessTenComp = companies.filter(
  (company) => company.end - company.start >= 10
);
console.log(lessTenComp);
```

### 4. map

We could create new array of anything really from the current array, this is different with other functions

```javascript
const companyNames = companies.map(function (company) {
  return company.name;
});
console.log(companyNames);
```

or you just return 1

```javascript
const test = companies.map(function (company) {
  return 1;
});
console.log(test);
```

companies [years rang]

```javascript
const testMap = companies.map(function (company) {
  return `${company.name}[${company.start}-${company.end}]`;
});
```

=>function

```javascript
const testMap = companies.map(
  (company) => `${company.name}[${company.start}-${company.end}]`
);
```

agesSquare, times2

```javascript
const ageSquare = ages.map((age) => Math.sqrt(age));
const ageTimesTwo = ages.map((age) => age * 2);
console.log(ageTimesTwo);
// ages square firstly, then x2
const ageMap = ages.map((age) => Math.sqrt(age)).map((age) => age * 2);
console.log(ageMap);
```

### 5. sort

sort companies by start years

```javascript
const sortedComp = companies.sort(function (c1, c2) {
  if (c1.start > c2.start) {
    return 1;
  } else {
    return -1;
  }
});
```

=> function

```javascript
const sortedComp = companies.sort((a, b) => (a.start > b.start ? 1 : -1));
console.log(sortedComp);
```

```javascript
console.log([(11, 2, 22, 1)].sort((a, b) => a - b)); // 1
```

👆 from function in VS code

sort ages

```javascript
const sortAges = ages.sort();
console.log(sortAges);
//wrong 11, 22, 5, 66
```



```javascript
const sortAges = ages.sort((a, b) => a - b);// descending( b-a); 66, 22, 11, 5
console.log(sortAges);
//right 5, 11, 22, 66
```



### 6.reduce

for loop

```javascript
let ageSum = 0;
for (let i = 0; i < ages.length; i++) {
  ageSum += ages[i];
}
```

reduce+function

```javascript
const ageSum = ages.reduce(function (total, age) {
  return total + age;
}, 0);
// last 0 means: total=0

```

==last 0 means: total=0==

reduce+ arrow

**how to quick change to => func removing: ==function {} return ;== ** 

```javascript
//how to quick change to => func removing function {} return
const ageSum = ages.reduce((total, age) => total + age, 0);
console.log(ageSum);
```

**Get total years for all companies**

```javascript
const totalYears = companies.reduce(function (total, company) {
  return total + (company.end - company.start);
}, 0);
```

removing `function`,

changing `{ return `to `=>`,

removing `; }`

```javascript
const totalYears = companies.reduce(
  (total, company) => total + (company.end - company.start),
  0
);

console.log(totalYears);
```

### 7. combined func

```javascript
// Combine methods
const combined = ages
  .map((age) => age * 2)
  .filter((age) => age >= 40)
  .sort((a, b) => a - b)
  .reduce((a, b) => a + b, 0);
console.log(combined);
```

```
const sleep = (ms = 2000) =>...;
async function welcome() {

await sleep();
}


```

