

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

