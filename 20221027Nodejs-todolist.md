# Node.js to do list - freeCodeCampe project

## Creat read update and destory or delete (Crud)

[Youtube resource](https://www.youtube.com/watch?v=qwfE7fSVaZM&t=18442s)

https://mongoosejs.com/

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

### learning note20221105

after build createTask, set the schema name requirement (not NAN, and less 20Char)

Flowchart:

- app.js connects with db/connect (database) 
- app.js connects with routes/task.js

- db/connect set url with .env (require mongoose)

- routes/task.js included “getAllTasks, createTask, getTask, updateTask, deleteTask ”

- In routes file, `const express = require("express")` `const router=express.Router()`

- in routes file connects to controller/taks.js

- ```javascript
  const {
    getAllTasks, //getAllUsers --Top5
    createTask, //createUser
    getTask, //getUser
    updateTask, //updateUser
    deleteTask,
  } = require("../controllers/tasks");
  router.route("/").get(getAllTasks).post(createTask);
  router.route("/:id").get(getTask).patch(updateTask).delete(deleteTask);
  ```

- “getAllTasks, createTask, getTask, updateTask, deleteTask ”

In controller/task.js, includes one of five up founction, createTask

`const Task = require("../modules/task");`

```javascript
const createTask = async (req, res) => {
  try {
    const task = await Task.create(req.body);
    res.status(201).json({ task });
  } catch (error) {
    res.status(500).json({ msg: error });
  }
};
```

Models/task.js  `const mongoose = require("mongoose");`

```javascript
const TaskSchema = new mongoose.Schema({
  name: {
    type: String,
    required: [true, "must provid name"],
    trim: true,
    maxlength: [20, "name cannot be more than 20 characters"],
  },
```



Now rest correct operations

https://mongoosejs.com/docs/queries.html

[Model.find()](https://mongoosejs.com/docs/api.html#model_Model-find)

#### problem solving

uodate時，在底下reqbody是舊的，但是getall是新的，所以我需要runvalidator

Update name and complete, then I click on getting all the tasks its actually changed. They reason why it happening, because we are not passing in the options and as far as the options we want to do two things we want to get the new one back, in the fact we are not running the validators so when we setting up the model one of the things that I set up for the name was required equal to true. If I try to update item with name equal to an empty string, I am actually going to be successful. 

We dont have options object and in order to set it up we need to go back all the controllers, third parameter is going to be options

如果輸入name是錯誤的爲空

```javascript
"_message": "Validation failed",
        "name": "ValidationError",
        "message": "Validation failed: name: must provid name"
```

validator 就報錯，而不是去把舊信息拿出來。

### middleware



```javascript
import { asynWrapper } from "../middleware/asyn.js";

```



```javascript
export const getAllTasks = async (req, res) => {
  try {
    const tasks = await Task.find({});
    res.status(200).json({ tasks });
    
  } catch (error) {
    res.status(500).json({ msg: error });
  }
};
```

If I want to make it 👆 as argument, I try to avoid try catch

```
const tasks = await Task.find({});
res.status(200).json({ tasks });
```

This is my cake and I want to eat to, where I can still use this nice await syntax. I dont have to set up these try catch blocks. 

- we setup the try catch blocks inside the wrapper

- ```javascript
  export const asyncWrapper = (fn)=>{}
  ```

- First, `return async (req, res, next)` I wrapped my controller in my middleware, we actually invoking the async wrapper right away. Of course I want to pass in those req res and next down to my function. 

