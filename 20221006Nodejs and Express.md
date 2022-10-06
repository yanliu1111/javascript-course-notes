# Node.js and Express.js - Full Course

## 1 Nodejs

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





