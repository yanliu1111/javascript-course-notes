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

### 91 Execution contexts and the call stack

#### hat’s inside excution context?4

1. Variable Environment
   - let const and var definitions
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

### 92 Scope and The scope Chain



































