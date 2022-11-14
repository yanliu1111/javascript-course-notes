# HTML CSS

## HTML

HyperText Markup Language

```javascript
<html>

</html>
```

*Metadata* is data (information) about data.

### HTML Attributes

each attributes has different meaning, inside “ ”

```html
<div id="my-container" class="card">
```



## CSS

Cascading Style Sheets (CSS) 

```css
h1 {
color:blue;
font-size:24px;
...
}
```

selector=h1, property=font-size, value=24px

### Selectors

- element selector such as div

- ```css
  div {
    font-size:
   }
  ```

- ID selector 

```css
#my-container  {
margin: 50px
}
```

```css
.card{
border-radius:10px;
}
```

trageting class if has dot .

####  Browser Support

http://caniuse.com/

blue: inner content for the element

orange: margin , how much space outside of the element

think about padding, but outside

#### Google Fonts

h1 has the default Font setting, Body setting is only for no specific setting, so cannot affect h1

#### defer and async

defer: wait until entire DOM has render first. Then go ahead to next script.

similar with async, defer will always run after dominate downloaded. Async could run at any time. Go to fetch js file, dont block any  run next. whenever the fetch comes back JS file, then run it. 

Go to fetch, continue on, only JS file once loading first. 

defer has work sequence, async donest have work sequence

```javascript
 <script src="index.js" aync></script>
  </head>
  <body>
    <div class="container">
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
    </div>
```

defer means make the rows grid in web first, then run index.js. Dont block

in index.js

`document.addEventListener("DOMContentLoaded", () => { })`

Only run the code putin the scop once `DOMContentLoaded`

```javascript
</head>
  <body>
    <div class="container">
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
    </div>
    <script src="index.js"></script>
```

把script放在下面是爲了不干擾上面div DOM的運行，但現在==不是好方法== waist time to this end and get js file

I perfer put in HEADER, go ahead to get the req eariler, JS file comes back to me as soon as possible. Asyn means not interrupting DOM load.

可以放在header裏，加上aync就可以

 <script src="index.js" aync></script>

如果是defer 意味著 先run DOM 之後再run js，和放在後面一樣。

 <script src="index.js" defer></script>

```javascript
<script src="jquery.com/jquery" defer></script>
    <script src="index.js" defer></script>
  </head>
  <body>
    <div class="container">
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
      <div class="row"></div>
    </div>
```

因爲是defer，順序是DOM -> jquery -> index.js

#### querySelector VS getElementById

```javascript
  const myInput = document.querySelector("#my-input");
  const myInput = document.getElementById("my-input");
```

`querySelector`, is for searching all elements, less choice than `getElementById`

`getElementById`  is for ID, quicker than `querySelector`



## Practice with Public APIs

two great sources of APIs, some have tutorials and instructions.

 https://rapidapi.com/hub

 https://publicapi.dev/

https://world.openfoodfacts.org/data









