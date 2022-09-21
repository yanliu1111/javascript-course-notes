# Project#3 Pig Game

#### 82 Follow Chart

![1663598466254](../Typora Note/pic/1663598466254.png)

Build your own flow charts,  you can do so on diagrams.net  👈 very nice online drawing app that is completely free and really easy and fast to use.

Inspect the code,  we need ==class== name, and in this case also the ==IDs== to then identify and select the elements. 

Same class name with different ID. In this project, we using their unique ID instead of a class name. <u>“score--0”“score--1”</u>

\# for ID *<u>for example: #score--0</u>* ;      . for class *<u>for example: .name</u>*

Hide the ‘dice’ using ==hidden== method in CSS

```css
.hidden {
display: none；
}
```

#### 83 Rolling dice

1. Check the follow chart! Add event listener or event handler

```javascript
'use strict';
//selecting DOM elements
const score0El = document.querySelector('#score--0');
const score1El = document.getElementById('score--1');
const current0El = document.getElementById('current--0');
const current1El = document.getElementById('current--1');

const diceEl = document.querySelector('.dice');

const btnNew = document.querySelector('.btn--new');
const btnRoll = document.querySelector('.btn--roll');
const btnHold = document.querySelector('.btn--hold');
//global variable outside, put in function is not local variable

//starting conditions
score0El.textContent = 0;
score1El.textContent = 0;
diceEl.classList.add('hidden');

let currentScore = 0; //has to be outside

//Rolling dice functionality
btnRoll.addEventListener('click', function () {
  //1. Generating a random dice roll, create local variable
  const dice = Math.trunc(Math.random() * 6) + 1;
  console.log(dice);

  //2. Displaying dice
  diceEl.classList.remove('hidden');
  diceEl.src = `dice-${dice}.png`;

  //3. Check for rolled, 1:(else)if true, switch to next player
  if (dice !== 1) {
    //add dice to current score
    //currentScore=currentScore+dice;
    currentScore += dice;
    current0El.textContent = currentScore;
  } else {
  }
});
```

Next we will track, the active player left or right section.

Leave last else dice===1, for next lecture with many settings.

#### 84 Switching the Active Player

const scores = [0, 0] position 0 and position1 means active player 0 and 1

Learn the other method same as ==contain== method on the class list property. 

==.classList.remove / add== learning before, now we learn toggle method

==.classList.toggle== : it will add the class if it is not there, if it is there, it will remove it.

```javascript
'use strict';
//selecting DOM elements
const player0El = document.querySelector('.player--0');
const player1El = document.querySelector('.player--1');

const score0El = document.querySelector('#score--0');
const score1El = document.getElementById('score--1');
const current0El = document.getElementById('current--0');
const current1El = document.getElementById('current--1');

const diceEl = document.querySelector('.dice');

const btnNew = document.querySelector('.btn--new');
const btnRoll = document.querySelector('.btn--roll');
const btnHold = document.querySelector('.btn--hold');
//global variable outside, put in function is not local variable

//starting conditions
score0El.textContent = 0;
score1El.textContent = 0;
diceEl.classList.add('hidden');

const score = [0, 0];
let currentScore = 0; //has to be outside
let activePlayer = 0;

//Rolling dice functionality
btnRoll.addEventListener('click', function () {
  //1. Generating a random dice roll, create local variable
  const dice = Math.trunc(Math.random() * 6) + 1;
  console.log(dice);

  //2. Displaying dice
  diceEl.classList.remove('hidden');
  diceEl.src = `dice-${dice}.png`;

  //3. Check for rolled, 1:(else)if true, switch to next player
  if (dice !== 1) {
    //add dice to current score
    //currentScore=currentScore+dice;
    currentScore += dice;
    document.getElementById(`current--${activePlayer}`).textContent =
      currentScore;
    // current0El.textContent = currentScore;
  } else {
    document.getElementById(`current--${activePlayer}`).textContent = 0;
    currentScore = 0; //it donest point any Player
    activePlayer = activePlayer === 0 ? 1 : 0;
    player0El.classList.toggle('player--active');
    player1El.classList.toggle('player--active');
  }
});
```

#### 85 Hold Current Score















































