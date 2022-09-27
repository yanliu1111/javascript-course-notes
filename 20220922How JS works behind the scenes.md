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



































