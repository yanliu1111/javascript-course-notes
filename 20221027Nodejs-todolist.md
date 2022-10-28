# Node.js to do list - freeCodeCampe project

## Creat read update and destory or delete (Crud)

[Youtube resource](https://www.youtube.com/watch?v=qwfE7fSVaZM&t=18442s)

if you connect database, never sync

if we try to connect to the database and only if we’re successful then we spin up the server. If not well then we’ll just kill the application  and in order to do that we need to restructure our code a bit where i am not going  to invoke mongoose connect in the connect.js. I’ll refactor the code and I’ll set it up as function and instead we will invoke it in the app.js and in order to do that we’ll just remove 

` .then(() => console.log("CONNECTED TO THE DB..."))`

  `.catch((err) => console.log(err));`

Change to a function

```javascript
const connectDB = (url) => {
  return mongoose.connect(connectionString, {
    useNewUrlParser: true,
    useUnifiedTopology: true,
    useCreateIndex: true,
    useFindAndModify: false,
  });
};
module.exports = connectDB;
```

目的：只有 鏈接成功，`npm start`沒有報錯后，才啓動 mongoose

Since I know the connectdb return a promise connect. I can set the function as aync and that way we can use the await keyword

