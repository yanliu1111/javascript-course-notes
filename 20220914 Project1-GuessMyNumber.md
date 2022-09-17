# Project1: Guess My Number

### 70 JS script.js

document.querySelector()

querySelector is a method that’s available on the document object. Pass the selector, this Selector is same as we used in CSS. 

==.message== is same Element using in CSS.

class using .     id using #

### 71 DOM manipulation

DOM stands for Document Object Model, basically a structure representation of HTML documents.

DOM(Document object model): Structured representation of HTML document. Allows JAVASCRIPT to access HTML elements and styles to manipulate them.

![1663370016240](../../2022 study/Typora Note/pic/1663370016240.png)

![1663370358751](../../2022 study/Typora Note/pic/1663370358751.png)

Web API are libraries that are written in JS.

That are automatically available for us to use.

### 72 Selecting and Manipulating Elements

DOM manipulation code

```javascript
console.log(document.querySelector('.message').textContent);
document.querySelector('.message').textContent = '🎉 Correct Number!';
console.log(document.querySelector('.message').textContent);

document.querySelector('.number').textContent = 13;
document.querySelector('.score').textContent = 10;

document.querySelector('.guess').value = 23;
console.log(document.querySelector('.guess').value); //alt+downArrow, change the rows upside down
```

### 73 Handling Click Events

First scenarios:

```javascript
document.querySelector('.check').addEventListener('click', function () {
  const guess = Number(document.querySelector('.guess').value);
  console.log(guess, typeof guess);

  if (!guess) {
    document.querySelector('.message').textContent = '❌No number!';
    
  }
});
```

**!guess, zero is false, if guess is no input, guess is false now. First scenarios is always to assume that there is actually no input.**

Next section, we will implement all the other scenarios, for example, where this guess here is actually correct. where it’s equal to the secret number. Generate the secret number and then compare it to the guess. 

### 74 Implementing the Game Logic

#### STEP 1: COMPARE THE NUMBER

**Math.trunc(Math.random()*20) 19.9999 = 19**

```javascript
const secretNumber = Math.trunc(Math.random() * 20) + 1;
document.querySelector('.number').textContent = secretNumber;

document.querySelector('.check').addEventListener('click', function () {
  const guess = Number(document.querySelector('.guess').value);
  console.log(guess, typeof guess);

  if (!guess) {
    document.querySelector('.message').textContent = '❌No number!';
  } else if (guess === secretNumber) {
    document.querySelector('.message').textContent = '🎉 Correct Number!';
  } else if (guess > secretNumber) {
    document.querySelector('.message').textContent = '❗ Too high';
  } else {
    document.querySelector('.message').textContent = '❗ Too low';
  }
});
```

#### STEP2:  SCORE setting -1 (Score logic)

we could have stored basically i the DOM. And to do that we would always just read the value from HERE (SCREEN). Then ==Decrease== value and then write it back here to the DOM. BUT, we would not have that value in the code. So essentially our application would have no way  of knowing that score at all points. SO, it’s always good to keep a variable which actually holds the data in our code and ==NOT== just rely on the DOM to hold our data.

the variable <u>let score=20</u>; could be called a ==state variable==

- ONE if inside another, because the score can go to -11

```javascript
const secretNumber = Math.trunc(Math.random() * 20) + 1;
let score = 20;

document.querySelector('.number').textContent = secretNumber;

document.querySelector('.check').addEventListener('click', function () {
  const guess = Number(document.querySelector('.guess').value);
  console.log(guess, typeof guess);

  if (!guess) {
    document.querySelector('.message').textContent = '❌No number!';
  } else if (guess === secretNumber) {
    document.querySelector('.message').textContent = '🎉 Correct Number!';
  } else if (guess > secretNumber) {
    if (score > 0) {
      document.querySelector('.message').textContent = '❗ Too high';
      score--;
      document.querySelector('.score').textContent = score;
    } else {
      document.querySelector('.message').textContent = '💥 You lost the game!';
    }
  } else {
    if (score > 0) {
      document.querySelector('.message').textContent = '❗ Too low';
      score--;
      document.querySelector('.score').textContent = score;
    } else {
      document.querySelector('.message').textContent = '💥 You lost the game!';
    }
  }
});
```

