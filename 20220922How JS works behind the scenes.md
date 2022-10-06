# How JavaScript Works Behind the Scenes

### 89. An High - level Overview of JS

1. Procedural programming
2. Object-oriented programming (OOP)
3. Functional programming (FP)

JS is very flexible and versatile. It is a ==prototype-based==, object-oriented approach.

Most of JS are objects, such as array. But except primitive values such as number, string, etc.

Why we can use array, and use PUSH method? Because prototypal inheritance. Basically, we create arrays from an array blueprint, which is like a template and this is called the prototype. This prototype contains all the array methods and the arrays that we create in the code then inherit the methods from the blueprint. So we can use them on the arrays.

![1663979302930](../Typora Note/pic/1663979302930.png) 

#### First class function

In a language with first-class functions, functions are simply treated as variables.

![1663980548332](../Typora Note/pic/1663980548332.png)

#### Dynamically-typed language

![1663980657013](../Typora Note/pic/1663980657013.png)

Cause BUG! didn’t declare data type.

#### Non-blocking event loop

**Concurrency model: **how the JS engine handles multiple tasks happening at the same time.

![1663981753740](../Typora Note/pic/1663981753740.png)

### 90. The JS engine and runtime

![1664057320172](../Typora Note/pic/1664057320172.png)

Parsing code: read code

During the parsing process, the code is parsed into a data structure called the abstract syntax tree or ==**AST**==.

Represent the entire code inside the engine, no relate with DOM tree.

**Compiles:** take AST and compiles it into machine code.

![1664058500352](../Typora Note/pic/1664058500352.png)

#### call back queue

all the callback function that are ready to be executed. 

==click==   ==timer==    ==data==  ...

For example, we attach event handler functions to DOM elements like a button to react to certain events, these event handler functions are also called callback functions.

A ==click==, the callback function will be called. And here is how that actually works behind the scenes. The callback function is put into the callback queue. The when the stack is empty, the callback function is passed to the stack, so that it can be executed. And this happens by something called the event loop.

#### Event loop

the event loop is how JS’s nonblocking concurrency model is implemented. 

Now, we will go over why this makes JS nonblocking om a special lecture about the event loop later. Its important to remember that JS can exist outside of browsers, for example, in Node.js.

![1664059409929](../Typora Note/pic/1664059409929.png)

The browser provides API

Just remember, that different JS runtimes do exist.

### 91. Execution contexts and the call stack

#### What’s inside execution context?

1. Variable Environment
   - let, const and var definitions
   - functions
   - arguments object 参数对象
2. Scope chain
3. This keyword

👆 creation phase

Execution contexts belonging to arrow functions, do not get their own arguments keyword, nor do they get the this keyword. 

arrow function don’t have the arguments object and this keyword, instead they can use closest regular function parent. 

任务 call stack 从global 累上来，到first（）到second（）function，JS只有一条 主线，second （）function 结束，回归first（）function，回归Global function 



![1664066770217](../Typora Note/pic/1664066770217.png)

```javascript
//函数声明式
function funcDeclaration() { 
	return 'A function declaration'; 
} 
//函数表达式 
var funcExpression = function () { 
	return 'A function expression'; 
}
```

其他小知识：

通常函数声明和函数表达式是可以相互互换使用，但有时函数表达式结果理解代码不需要一个临时的函数名。

### 92. Scope and The scope Chain

Scoping and variable environment same, but actually different

![1664145661030](../Typora Note/pic/1664145661030.png)

![1664146820182](../Typora Note/pic/1664146820182.png)



==**Important**==

![1664147809022](../Typora Note/pic/1664147809022.png)

The scope chain does get the variable environments from the execution context as shown by the red arrows here, BUT that’s it! The order of function calls is not relevant to the scope chain at all.

![1664148479698](../Typora Note/pic/1664148479698.png)

b and C are not in right side. Error!

![1664148998370](../Typora Note/pic/1664148998370.png)

### 93. Scoping in Practice

```javascript
'use strict';

function calcAge(birthYear) {
  const age = 2037 - birthYear;
  function printAge() {
    const output = `${firstName}, you are ${age}, born in ${birthYear}`;
    console.log(output);

    if (birthYear >= 1981 && birthYear <= 1996) {
      var millenial = true;
      const firstName = 'Steven'; // first fetch in scope, doesnt care global variable
      const str = `Oh, and you're a millendial, ${firstName}`;
      console.log(str);

      function add(a, b) {
        return a + b;
      }
    }
    // console.log(str);Error: because const and let are block variables, they are valiable only inside the block
    console.log(millenial); // But if we create var inside, var is not block scope, it is function scope, Now var still in the BIG function scope.
    // console.log(add(2, 3)); Error: in strict model, function is affected by leaving inside block scope. If move 'use strict', this works!
  }
  printAge();

  return age;
}

const firstName = 'Jonas';
calcAge(1991);
// console.log(age); Reference Error
// printAge(); Reference Error
```

Now, what happens when we redefine a variable from a parent scope inside of an inner scope. Not creating a new variable, but simply reassigning the value of a variable. 

```javascript
if (birthYear >= 1981 && birthYear <= 1996) {
      var millenial = true;
      //creating new variable with same name as outer scope's variable
      const firstName = 'Steven'; // first fetch in scope, doesnt care global variable
      // reassigning outer scope's variable
      output = 'New output!'; // in this method, we manipulate an existing variable inside of child scope. So inside of an inner scope. We didnt create a new variable, we simply redefined a variable we access in parent scope.
      //   const output = 'New output!'; BUT if I create a new variable (const+same name), this is complete new variable which would NOT affect the output from out scope.
      const str = `Oh, and you're a millendial, ${firstName}`;
      console.log(str);

      function add(a, b) {
        return a + b;
      }
    }
```

### 94. Variable Environment: Hoisting and the TDZ

![1664469092815](../Typora Note/pic/1664469092815.png)

To recap, basically each and every let and const variable get their own temporal dead zone that starts at the begining of the scope until the line where it is defined. And the variable is only safe to use after the TDZ. 

![1664467610445](../Typora Note/pic/1664467610445.png)

TDZ temporal dead zone for job variable

#### **Why TDZ?** 

TDZ was introduced in ES6 is that  the behavior I described before makes it way easier to avoid and catch errors. 

So accessing variables before declaration is bad parctice and should be avoided. Send you an error, that is exactly what a ==Temporal Dead Zone== does. 

A second and smaller reason why the TDZ exists  is t omake const variables actually work the way they are supposed to . 

As we know, we cannot ==reassign== const variables. So it will not be possible to set them to undefined first  and then assign their real value later. 

#### **Why Hoisting** 

Using functions before actual declaration. It is essential for some programming techniques, such as mutual recursion.  Make the code a lot more readable. 

The fact that is also works for var declarations is because that was the only way hoisting could be implemented at the time. 

So the hoisting of var variables is bacically just a buproduct of hoisting functions. simply set variables to undefined,  which in hindsight is nor really that great. 

### 95 Hoisting and TDZ Practice

Yesterday, we learned Function with Greg,  I got update knowledge about function today.

Only function declaration has hoisting function, no working for function expression and arrow

Correct

```javascript
console.log (addDecl(2,3));
const addDecl (a,b){
return a+b;
}
```

Error

```javascript
console.log(addExpr(2,3));
const addExpr = function (a, b){
return a+b;
}
```

My question is how to choose when I need to use function declaration and function express?

#### Very cool! pitfall of hoisting

var numbproducts =10; \\ \undefined

so,  if (!numberproducts) deleteShoppingCart(); ==\\ \all products deleted! because is not number is undefined result.==

function deleteShoppingCart{

console.log(‘all products deleted!’);

}

```javascript
var x=1;
let y=2;
const z=3;

console.log(x===window.x);\\true
console.log(y===window.y);\\false
console.log(z===window.z);\\false
```

So in conclusion, variable declared with var, will create a property on the global window object. And that can have some implications in some cases. 



###  96 The this keyword

![1664667000462](../Typora Note/pic/1664667000462.png)

Arrow function don’t get this keyword

```javascript
const jonas = {
  firstName: 'Jonas',
  year: 1991,
  calcAge: function () {
    console.log(this);
    console.log(2037 - this.year);
  },
  greeting: () => console.log(`Hey ${this.firstName}`),
};
jonas.greeting(); 
console.log(this.firstName); //because this is window object, there is no first name and so we get undefined.
```

- Hey undefined, arrow function does not get its own this keyword, it will simply use the this keyword from its surroundings. in other words, its parents this keyword.The parent scope of ==this== greet method is the global scope.

- `console.log(this)`is window scope, global scope is window scope.

  `greeting:()=> console.log('Hely ${this.firstName}')`, parent scope is global scope is windows, windows hasnt this variable. 

  - So， 作者危險操作，create var this，he build this variable in global scope, in windows.

- We cannot accesse some property on a certain object, we dont get error, we get undefined. 

- this is not code block, it is object literal, this is the way we literally define objects. all of this in the global scope. Greeting is in global scope, arrow function doesnt have its own this keyword. Will use the this keyword from the global scope.

- console.log(this);  this is window object

```javascript
var firstName ='Matilda';
```

var is dangous, var defined in window, which translate to window dot first name. 

==You should never ever use an arrow function as a method, that’s even true if you’re not even using the this keyword in a particular method.==

You will always just use a normal function expresion, and like this, you will then prevent this kind of mistakes from happen. 

Keep consist in normal function! I can use this keyword

```javascript
const jonas = {
  firstName: 'Jonas',
  year: 1991,
  calcAge: function () {
    console.log(this);
    console.log(2037 - this.year);
  },
  greeting: function () {
    console.log(`Hey ${this.firstName}`);
  },
};
jonas.greeting();
```

Inside function call, that this keyword must be indefined. 

```javascript
const jonas = {
  firstName: 'Jonas',
  year: 1991,
  calcAge: function () {
    // console.log(this);
    console.log(2037 - this.year);
    const isMillenial = function () {
      console.log(this);
      console.log(this.year >= 1981 && this.year <= 1996);
    };
    isMillenial();
  },
  greeting: function () {
    console.log(`Hey ${this.firstName}`);
  },
};
jonas.greeting();
jonas.calcAge();
```

isMillenial(); // inside function, undefined

jonas.calcAge(); // undefined

Solution1:

```javascript
const self = this; //self or that
    const isMillenial = function () {
      console.log(self);
      console.log(self.year >= 1981 && self.year <= 1996);
    };
    isMillenial();
  },
```

Solution2, used arrow function instead, basically an arrow function inferites the this keyword from parent scope. 

```javascript
const jonas = {
  firstName: 'Jonas',
  year: 1991,
  calcAge: function () {
    // console.log(this);
    console.log(2037 - this.year);
    //solution 1
    //   const self = this; //self or that
    //   const isMillenial = function () {
    //     console.log(self);
    //     console.log(self.year >= 1981 && self.year <= 1996);
    //   };
    //   isMillenial();
    // },
    //Solution2 Arrow function used this keyword from its parent scope.
    const isMillenial = () =>
      function () {
        console.log(this);
        console.log(this.year >= 1981 && this.year <= 1996);
      };
    isMillenial();
  },
  greeting: function () {
    console.log(`Hey ${this.firstName}`);
  }, // cannot use arrow, no parent(windows is global), object it is not parent.
};
jonas.greeting();
jonas.calcAge();
```

#### arguments keyword is only avaiable in regular functions

```javascript
const addExpr = function (a, b) {
  console.log(arguments);
  return a + b;
};
addExpr(2, 5);
addExpr(2, 5, 8, 12); //works

//no works in arrow function
var addArrow = (a, b) => {
  console.log(arguments);
  return a + b;
};
addArrow(2, 5, 8);
```

### 99 Primitives vs Objects (primitive vs reference types)

The engine had two components, the call stack, where the function are excute/ and to heap where objects are stored in memory.

Reference type will get stored right in the memory heap. 

On the other hand, primitives or primitive types are stored in the call stack. Primitives are stored in the execution contexts in which they are declared. 

![1664906059851](../Typora Note/pic/1664906059851.png)

When we declare a variable as an object, an identifier is created, which points to a piece of memory in the stack, which in turn points to a piece of memory in the heap. That is where the object is actually stored.

Heap is like an almost unlimited memory pool.

Stack keeps a reference to where the object is actually stored in the heap so that it can find it whenever necessary. 

![1664907737841](../Typora Note/pic/1664907737841.png)



### 100🎉 Primitives vs Objects in Practice

We cannot change value in stack

We cannot change the value to a new memory address,  so `const marriedJessica =jessica`; `marriedJessica ={};` cannot work

Completely change a object, is different just change a proterty of object. `marriedJessica.lastName=‘Davis';`

```javascript
//Reference types
const jessica = {
  firstName:'Jessica';
  lastName:'Williams';
  age:27
}
const marriedJessica = jessica;
marriedJessica.lastName='Davis';
console.log('Before marriage:', jessica);
console.log('After marriage:', marriedJessica);
```

Copying objects

```javascript
const jessica2 = {
  firstName:'Jessica';
  lastName:'Williams';
  age:27
}

const jessicaCopy=Object.assign({},jessica2);
jessicaCopy.lastName='Davis'
console.log('Before marriage:', jessica2);
console.log('After marriage:', jessicaCopy);
```

JessicaCopy is indeed a real copy of the orignial. All the properties were essentially copied from one object to the other. New object was in fact created in the heap. And JessicaCopy is pointing to that object. It has a reference to that new object. 

==Problem== object.assign only works in the first level. If we have an object inside the object, then this inner object will actually still be the same. It will still point to the same place in memory. 

==Object.assign only create a shallow copy==, not a deep clone which is what we would like to have. 

```javascript
const jessica2 = {
  firstName:'Jessica',
  lastName:'Williams',
  age:27,
  family:['Alice','Bob'],
}

const jessicaCopy=Object.assign({},jessica2);
jessicaCopy.lastName='Davis'

jessicaCopy.family.push('Mary');
jessicaCopy.family.push('John');
console.log('Before marriage:', jessica2);
console.log('After marriage:', jessicaCopy);
```

**Williams doesn’t changed, because first level**

**Family object is a deeply nested object, therefore, object.assign did not really, behind the scenes, copy it to the new object. So in essence, both the objects, Jessica2 and JessicaCopy have a proterty called family, which ==points at the same object in the memory heap==. Here is array, array inside object, deep object.**

Complex: How to create a deep clone, using an external lib, for example, like lo-Dash, one of them is for deep cloning. Future section, we use external lib to do deep clone.

