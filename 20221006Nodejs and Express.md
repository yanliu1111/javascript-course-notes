# Node.js and Express.js - Full Course

## 1 Node.js learning

start, check `node -v`, check `npm --v`

build package.json: `npm init -y`

load dependencies properties, so there show package-lock

`npm i lodash`and node_modeles folder, have to ==.gitignor==

## 2 我的流程

1 在github上建立 express tutorial的repo，不要有readme

2 在建立一個空文件夾，可以在vscode上操作，和模擬聯係的folder并列，我不在模擬聯係的folder直接用，自己創建新的。

3建立app.js第一個文件在新文件夾裏。

==4忘記為什麽可以直接使用node了？我怎麽install node的？==

 check 9.26 note!

5查看我的空文件夾裏 

start, check `node -v`, check `npm --v`

6 都有各自版本，之後參考文件夾的package json很重要。

我需要在自己的folder裏 build package.json: `npm init -y`

7 我自己的新文件夾裏有package.json.

8 對比參考文件的，複製粘貼 過來，尤其是script和dependence兩個部分

9 `npm install` 按照package.json裏的dependence文件，下載需要的module，建立 node_modules 和 package-lock.json

10建立`.gitignore`, put in `/node_modules`



### 1 Callback: sync and async  

```javascript
const { readFile, writeFile } = require("fs");
console.log("Staring");
readFile("./content/first.txt", "utf-8", (err, result) => {
  if (err) {
    console.log(err);
    return;
  }
  //   console.log(result);
  const first = result;
  readFile("./content/second.txt", "utf-8", (err, result) => {
    if (err) {
      console.log(err);
      return;
    }
    const second = result;
    writeFile(
      "./content/result-async.txt",
      `Here is the result : ${first}, ${second}`,
      (err, result) => {
        if (err) {
          console.log(err);
          return;
        }
        console.log("Done with this task");
      }
    );
  });
});
console.log("Starting the next");

```

==In async file,==

$ node 11-fsAsync.js 
Staring
Starting the next
Done with this task
we can offload that task and then we start a next task right away
==In sync file,==

following the sequence, up to down, problem: many users block

Staring
Done with this task

Starting the next

In next, we’ll use ==async await== because it is easier to work with it.

### 2 HTTP module

revolve around server setup aka http module

`<a href="/">back home</a>`navigate back

==modules and dependencies== are interchangeable/ any of these names package dependency or module at the end of the day they all mean the same thing lastly.

[npmjs](npmjs.com)

“devDependencies”{

“nodemon”:“^2.0.7”

}

`npm i nodemon -D`or `npm i nodemon --save-dev`

nodemon is watching the application

nodemon automatically just restarts the app

npm uninstall packageName

新安裝步驟

1 npm i bootstrap, 自動加入package.jason

2 package.jason 新加dependencies



但是，我可以直接

1 remove/delete node_modules folder 和 package-lock文件

2在package.jason 裏remove bootstrap的dependencies

3 根據 package.jason, npm install, New UPDATE back without Bootstrap



npm install -g nodemon : install nodemon ==globally==

#### How to use Gatsby CLI

https://www.gatsbyjs.com/docs/reference/gatsby-cli/

Gatsby command line tool (CLI) is the main entry point for getting up and running with a Gatsby app and for using functionality including like running a development server and building out your Gatsby app for deployment.

You need install ==globally!==

either using npx or I just use locally dependencies.

What is npx?

it stands for execute and official name is the package runner. It is a feature that was introduced in npm 5.2 and 

[Node.js Event loop](https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/#:~:text=The%20event%20loop%20is%20what,operations%20executing%20in%20the%20background.)

https://course-api.com/

What it means that Javascript is synchronous  and single threaded.

==we cannot offload the for loop==, it effectively is still going to be the blocking code, but browser nicely provides the api where we can offload to the browser. 

```javascript
console.log('first task');
console.time()
for (let i=0; i<10000000; i++){
    const h3 = document.querySelector('h3')
    h3.textContent = 'HEY everyone is waiting on me'
}
console.timeEnd()
```

result: first task -> time -> second.textcontent

```javascript
console.log('first task');
setTimeout(()=>{
    console.log('second task');
}, 0)
console.log('next task');
```

Block code, outside first then inside

result: first task -> next task -> second task

Browser does provide some nice apis where we can offload those time consuming tasks.

![1665236550200](../Typora Note/pic/1665236550200.png)

We are running our immediate tasks first and only then we run the callback so the same thing happens here where the requests are coming in let’s say that the operation is complete we first registered the callback operation is complete and instead of executing that callback right away it effectively get to put at the end of the line and then there is no immediate code run then we execute the callback.

```javascript
const{readFile}=require('fs')

console.log('started a first task');
//check file path
readFile('./content/first.txt','utf8',(err, result)=>{
    if (err){
        console.log(err);
        return
    }
    console.log(result);
    console.log('completed first task');
})
console.log('starting next task');

```

**<u>readFile is asynchronous, event loop will offload this</u>**
**<u>1 start reading the file 'start...'</u>**
**<u>2 run readFile this line, then offload 'console.log result'</u>**
**<u>3 and only when I get back to the result then run the callback</u>**
**<u>so when the file system with error or the data then we invoke 'starting next task'.</u>**
**<u>So we offload this task and keep reading the code that's why we have started the first task starting the next one so right away go to the next test. And this asynchronous one. we are offloading and once the response comes back whether its an error whether its a success. Only then we invoke the callback.**</u>



#### How to create the wrapper function4

Follow learning async next,

It is more readable, more easier to wrap your head around

But the core functionality wont change where instead of using callbacks and nesting them inside of the other callbacks and nesting more and more and more.

We’ll set up everything with async await because the syntax is cleaner and readable easily.

```javascript
const { readFile, writeFile } = require("fs").promises;
// const util = require("util");
// const readFilePromise = util.promisify(readFile);
// const writeFilePromise = util.promisify(writeFile);

const start = async () => {
  try {
    const first = await readFile("./content/first.txt", "utf8");
    const second = await readFile("./content/second.txt", "utf8");
    await writeFile(
      "./content/result-mind-grenade.txt",
      `This is awesome: ${first}${second}`,
      { flag: "a" }
    );
    console.log(first, second);
  } catch (error) {
    console.log(error);
  }
};
start();
```

Instead of complex syntax

```
//How to create the wrapper function.

// getText("./content/first.txt")
//   .then((result) => console.log(result))
//   .catch((err) => console.log(err));

//const getText = (path) => {
//   return new Promise((resolve, reject) => {
//     readFile(path, "utf8", (err, data) => {
//       if (err) {
//         reject(err);
//       } else {
//         resolve(data);
//       }
//     });
//   });
// };
```

### 3 Events

1. Event-Driven Programming
2. Used Heavily in Node.js

### 4 Stream

1. Writeable
2. Readable
3. Duplex
4. Transform

![1665456344766](../Typora Note/pic/1665456344766.png)

Node.js as a File Server

`var fs = require('fs');`

Common use for the File System module:

- Read files
- Create files
- Update files
- Delete files
- Rename files

## 3 Express.js learning

using ssh so secure shell i am going to use port 22

if I want to use http protocol and access resource that way then I am going to use 443

port from 0 to 1024, you shouldnt use it. But in local development again this is arbitrary number, you can use anything you want. 

React app we spin up the server on localhost 3000 then gatsby has i believe 8000, and then netlify CLI has 8080...

I hit the resource but nothing is happening,  there is method we always always need to include in our response and the method name 

Response.end(\[data[,encoding]\][,callback])

[nodejs .org-response.end](https://nodejs.org/api/http.html#responseenddata-encoding-callback)

`this method signals to the server that all of the response headers and body have been sent;  that server should consider this message complete. The method response.end(). MUST be called on each response.`

```javascript
const { response } = require("express");
const http = require("http");

const server = http.createServer((req, res) => {
  console.log("user hit the server");
  res.end("home page");
});
server.listen(5000);

```

We have access to http module and this is build in node, set up variable`http.createServer` calling the http

Then we have create server method, that takes in the callback which is going to be invoked every time the user hit the server and as **parameter** we have a <u>request and response objects</u> and common convention calling req and res.

In the http cycle that what happens we have a request message that is coming in where we can find a bunch of useful info about the request that is coming in. We need to respond to the browser in a meaningful manner -- that is why we have respond object. In any respond communication ending, we need `res.end` -- the signal communication over.

Issue 1: We didnt provide any info about data that we’re sending back. We dont have any metadata about the body that we’re sending out. So we are not providing any info

Issue 2: Go to local host 5000 and if I type 5000/about; or 5000/detail...

They all showed “home page”

For issue1, I am getting back the html, I need to render as html and this stuff matters `text/html` `text/plain` render as html or txt file

### 1 http status codes

[MDN resource-http status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

we are setting up status code so the browser knows what is happening with the request was it successful or error. You are not authorized to access it, 100 ones are going to be information responses

 then for successful one we have 200 so that probably is going to be the one that you’ll use the most so that means that request has succeeded 

then we have 201 we use a lot and this is once post request is successful if you add the resource successfully the server 

then you just send back to one we have 300s for redirect and these are the ones that you probably dont want to get if you are surfing the web 

So 400 is for bad request for example you are requesting some kind of data or you’re trying to do something on the server but you dont provide info. I am trying add the user but I dont provide the user name. 

401 is for unauthorized 

403 forbidden and 404 unfound send a request, but resource dont exist.

It important we use the correct status codes because we are in charge here nothing stops me from sending back the 404 meaning the resource is not found/ then you navigate to contact page for and if you inspect again the browser , you see this confusion info 404

the correct status code reflects what is happening with the request and 

####  Main Idea for HTTP

You sending back something and you need to describe to the browser well what are you sending back. Are you sending back the image, are you sending back CSS 

instantiate server 實例化

**鏈接 到 一個有 鏈接的navbar-app，出現 3個404** 

**404 in : one for styles one for browser one for logo**

- in this case, I am going to request all these resources here, and set up more else if statements where if the browser wants to get the css, then of course we’ll search css. If the browser wants to have logo then the browser gets the logo

so local address is wrong, set new variables to point the new local address

in this course, we compare two types of http http-basic and http-app

#### Express.js

2種方法可以install express.js

1. 在package.json 裏 `dependencies: “express”: “\^4.17.1”`
2. 在指定文件夾裏 terminal裏direction后，`npm install express --save`

```javascript
//setup static and middleware
app.use(express.static("./public"));
```

==**static asset**== meaning an asset where the server doesnt need to change it, we simply place it in designated folder again the common name for those folders are public or static and then we just dump all those assets in there.

For example, if we have 20 000 extra images here, i just dump them and express will take care of it all. 

Express will setup the path, main type, status codes, and all of good stuff.

include: image file, styles file, js file

1. API-Json
2. Send Data
3. RES.JSON()
4. SSR - Template
5. Send template
6. RES. Render()

https://react-projects.netlify.app/

**It doesnt have to be vanilla javascript, can be vanilla javascripe application. it can be swelled framework. It could be any fetch that data tools.**

Using Json data to front end.

1 eventally we use database for that,

2 it comes to express basics 

no matter we use server side or use Json. Just understand principles, doest matter which option we use. 

#### Express Webpage

https://expressjs.com/en/api.html#res.json

build API, anyone can use this data

```javascript
app.get("/api/products/:productID/reviews/:reviewID", (req, res) => {
  console.log(req.params);
  res.send("Hello Word");
});
```

view 改成views ，得到404， 因爲view is not a route parameter, it is not placeholder 

####  Query string parameters

https://hn.algolia.com/api

A. the key designed on the server

it is up to us to handle those query parameters

```javascript
app.get("/api/products", (req, res) => {
  const newProducts = products.map((product) => {
    const { id, name, image } = product;
    return { id, name, image };
  });
  res.json(newProducts);
});
```















