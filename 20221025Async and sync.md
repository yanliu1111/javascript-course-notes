# Async and sync-GR

## 1 Function & arguments

- Pass by value: string, num, boolean

- Pass by reference: object, array

## 2 Synchronous Asynchronous

Sync: Runs immediately / in sequence / blocking

Async: runs in the future / out of order / non-blocking

```javascript
function dosomething() {
  console.log("Do something");
}
setTimeout(() => {
  console.log("Do something else");
}, 1000);//non block, async, start when I call 

dosomething();
```

sequence is settime() wait 1 scend to start,   dosomthing (), 

showing, dosomething, after 1second settime()

both functions dont affect each other

==settime () ---> dosomething()--in 1 second--> settime()==

```javascript
function dosomething() {
  console.log("Do something");
}
setTimeout(() => {
  console.log("Do something else");
}, 0); //non block, async, start when I call

dosomething();//sync first
```

==dosomething() sync function is first, then async function setTime()==

```javascript
setTimeout(() => {
  console.log("Do something else");
}, 0); 
```

👆 This pattern is async -- ==call back==

## 3 Promises

```javascript
doSomethingAsyn()
.then(()=>{
    return 123;
})
.then((result)=>{
    console.log(result);//123
})
```

我build async func，所以我和下面的 function 不干擾，但是我Async function裏是sync function 組成是.then()

### async/await

- syntactic sugar

- make async code feel procedural

- 

  ```javascript
  async function run(){
      try{
      await doSomethingAsync();
      } catch (err){
          //This is equivalent to the '.catch() ' method
      }
  }
  run();
  ```

  https://represent.opennorth.ca/api/

  ```javascript
  import fetch from "node-fetch";
  async function run() {
    const response = await fetch(
      "https://represent.opennorth.ca/postcodes/T2G0E7"
    );
    console.log(response);
  }
  ```

  meta information

When i should use ==Async await==, only use await when function callback from promise

how do you know it is promise?

![1666702899867](../Typora Note/pic/1666702899867.png)

if you remove await, you will see promise pending, where is my container

waiting the promise finish and store in response container

```
You'll want to res.send() whatever message you want displayed to the user.

eg

app.get('/result', (req,res)=>{
  ... possibly some code here
  if (winner === 'player1') {
    .... some code here
    res.send(...something)
  } else {
    ... other code
    res.send(...something...else)
  }
})
```

























