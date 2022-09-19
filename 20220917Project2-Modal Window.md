# Project#2  Modal Window

```javascript
'use strict';
// modal -> overlay -> close modal
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnOpenModal = document.querySelectorAll('.show-modal');
console.log(btnOpenModal);

for (let i = 0; i < btnOpenModal.length; i++)
  console.log(btnOpenModal[i].textContent);
```

- No need{}, because like an if else statement, if there is only one line of code that I want to execute, I actually dont have to create this block {}. Directly write one line after the for loop, that will be iterated over and over again.

#### 80 Working with Classes

==Event listener:== We will attach an event handler function to the element. And event handler and event listener  are pretty much the same thing.  

```javascript
'use strict';
// modal -> overlay -> close modal
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnOpenModal = document.querySelectorAll('.show-modal');
console.log(btnOpenModal);

for (let i = 0; i < btnOpenModal.length; i++)
  //console.log(btnOpenModal[i].textContent);
  btnOpenModal[i].addEventListener('click', function () {
    console.log('Button clicked');
    modal.classList.remove('hidden'); //you can remove multiple elements, except .
    overlay.classList.remove('hidden');
  });

const closeModal = function () {
  modal.classList.add('hidden');
  overlay.classList.add('hidden');
};
btnCloseModal.addEventListener('click', closeModal);
overlay.addEventListener('click', closeModal);

//DRY code
// btnCloseModal.addEventListener('click', function () {
//   modal.classList.add('hidden');
//   overlay.classList.add('hidden');
// });

// overlay.addEventListener('click', function () {
//   modal.classList.add('hidden');
//   overlay.classList.add('hidden');
// });
```

- modal.style.display='block'; image the hidden class actually had 10 properties, we need to write manually and change the values. A lot of work if write like this.

- and again, because we did it here in the loop, while we were looping over this note list, which contins all of these three buttons.

- modal.classList.remove = we can check an element contains a certain class or not.

==Continue refactoring:==

```javascript
'use strict';
// modal -> overlay -> close modal
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnOpenModal = document.querySelectorAll('.show-modal');

const openModal = function () {
  console.log('Button clicked');
  modal.classList.remove('hidden');
  overlay.classList.remove('hidden');
};

const closeModal = function () {
  modal.classList.add('hidden');
  overlay.classList.add('hidden');
};

for (let i = 0; i < btnOpenModal.length; i++)
  btnOpenModal[i].addEventListener('click', openModal);

btnCloseModal.addEventListener('click', closeModal);
overlay.addEventListener('click', closeModal);
```

We practiced adding and removing classes all the time in order to change the appearance of elements on the page.  That is because classes allow us to basically aggregate multiple CSS properties in just one, like ==container==.

Each class functions a bit like a container with a lot of properties in it. 

And here by, adding and removing them, we basically can activate and deactivate certain styles all at the same time. 

There is a third thing that we do with classes,  which is to check if a class is actually present on a certain element. - key press event 👇

#### 81 Handling an“Esc”Keypress Event

How to respond to keyboard events = global event

Add event everywhere

Three types: key down, up, and press

==keyup:== only happens when we lift or finger off the keyboard basically or off the key.

==keypress:== we keep our finger on a certain key

==keydown:== is fired as soon as we just press down the key.

the information about which key was pressed will be stored in the event that is going to occure as soon as any key is pressed.  -----But, any key included 

Now, we look at the ==event object== in order to figure out

JS call function when a key down event happens, when you do so, pass in the event object as an argument. 

```javascript
document.addEventListener('keydown', function (e) {
  //   console.log('a key was pressed');
  console.log(e.key);

  //e means event + 以下是被简化的code
  // if (e.key === 'Escape') console.log('Esc was pressed');
  //   if (e.key === 'Escape') {
  //     if (!modal.classList.contains('hidden')) {
  //       closeModal();
  //     }
  //   }

  if (e.key === 'Escape' && !modal.classList.contains('hidden')) {
    closeModal();
  }
});
```





 









