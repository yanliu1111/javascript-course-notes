### 20220923 Tony course

Interesting webs: Clone third party projects: Popular projects

[Font Awesome](https://fontawesome.com/)

[Lodash](https://lodash.com/)

grouping items in array

[tailwindcss](https://tailwindcss.com/)

#### local repo and remote repo

A typical sequence of events in a developer’s day:
○ A developer will work locally on their own system in a Local Repo, making changes to
code.
○ When code is finally working, they ==add== the changes to “staging” (this must be done
before you can commit the changes);
○ They then =commit== the changes to create a “snapshot” of your project;
○ They ==push== the changes to a Remote Repo (i.e. GitHub) when the changes are
ready to be shared or deployed.
■ Note: you must ==pull== any new changes from the Remote Repo before you
can push. This is when dreaded merge conflicts need to be handled.

At any point during development, you can view the ==status== of your repo to find helpful
information of the status of your project.

==**every commit + git status **== to view the status

in Terminal, master and main means you are in repo. They are same. Old way and new way(GitHub)

==PLEASE!!! DONT repo inside repo==

It’s a pain, but you always have to ==add== your changes before you ==commit== them.
This is to prevent you from accidentally committing code you didn’t mean to.

Don’t forget to add the ==-m “commit message here”== when using the ==git
commit== command. Otherwise, your terminal will open a ==vim== window so you
can add the mandatory commit message. **<u>It’s the default command line text</u>
<u>editor</u>** on most systems and is not the most intuitive application to use. See
this [Vim cheatsheet](https://devhints.io/vim) if you need a command (:==q!== will quit without saving so
you can try committing again with the ==-m== flag).

框起来，terminal显示，去掉自己的电脑号！

`.../d/2022study/_InceptionU/C9/dailies/2022-09-23-git-and-github/_hello/Font-Awesome (6.x)`

6.x called the branch of repo

`$ git status
On branch 6.x
Your branch is up to date with “origin/6.x” `

`nothing to commit, working tree clean`

#### Create a GitHub repository

Journal repository - - add readme

index.html -- create readme

`git log`see all comit made, then `q`for quit

Tony never `git restore`

`git add README.md` when you add the modified file, RED turn to Green

`git commit -m “detail editings info”`

`git add .` if you have multiple changes, add .  = all

`git commit -m"added intro paragraph"`

`git fetch` fetch the changes from server

`git push` end

then check `git status`



#### generate webpage

![InceptionU-1](../Typora Note/pic/InceptionU-1.JPG)

👆 /(root) put the readme.md into index.html page. Root means MUST a html page inside

choose ==“Main”== choose ==“Save”==

![1664211959919](../Typora Note/pic/1664211959919.png)

location: origin means github; ‘origin/main’by 1 commit means I have commit but github doesnt

[Tony class-The browser triad, HTML CSS and JS](https://sait-wbdv.github.io/slides/f22/cpnt-260/browser-triad.html)

[Front-awesome cdnjs](https://cdnjs.com/libraries/font-awesome)

Go to front awesome web and find free icon:

https://fontawesome.com/search?m=free&o=r

icomoon allows you create custom icon of font size

https://icomoon.io/

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Hello Font Awesome</title>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css"
    />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/js/all.min.js"></script>
    <style>
      body {
        font-size: 256px;
        color: pink;
      }
      .wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
      }
    </style>
  </head>
  <body>
    <div class="wrapper">
      <i class="fa-brands fa-github"></i>
    </div>
  </body>
</html>
<!-- font awsome -->
```

------------

`$ ls -la
total 8
drwxr-xr-x 1 Yan Liu 197121   0 Sep 26 20:00 ./        
drwxr-xr-x 1 Yan Liu 197121   0 Sep 25 23:45 ../       
drwxr-xr-x 1 Yan Liu 197121   0 Sep 27 00:30 .git/     
-rw-r--r-- 1 Yan Liu 197121 872 Sep 27 00:38 index.html`

there is .git in the folder,

`rm -rf .git`VERY dangous commend 

`$ cd ../lodash/`從font awesome 文件夾跳出來，進入與之平行的另一個文件夾。

`$ cd ../../`

NOW, delete all gits in different repos, go to ==dailies== folder

`.../_InceptionU/C9/dailies
$ git status
fatal: not a git repository (or any of the parent directories): .git`

GOOD, no git init

`$ git init
Initialized empty Git repository in D:/_InceptionU/C9/dailies/.git/`

--------------------

`$ git status`
`On branch master`

`No commits yet`

`Untracked files:
  (use "git add <file>..." to include in what will be committed)
        2022-09-21-command-line/
        2022-09-23-git-and-github/
        2022-09-26-Node/`

`nothing added to commit but untracked files present (use "git add" to track)`



` ..../_InceptionU/C9/dailies (master)` now it shows master

==branch is master, default with git is master, default with github is main==





github will made the initial commit for me, 









###  20220926 Node.js - Greg R

Node.js --- JS on the server side

JS runtime

browser - frontend; backend-- server side

Before Node.js

C++ no use web server side

####  Runtime

what is the runtime?  central process unit -- CPU

Fetch a number from memory -> add+2 to it-> multiply 5 -> store back in memory 

COMPLIE - C compile to 0and1 (binary code)

V8 engine is runtime. (run JS)

#### REPL

Read , Evaluate, Print,  Loop

node my-program.js

python my-program.py

ctrl+c = quit

`c9 mkdir newFolder` create a new folder in specific location

`ls -l`

`ls -ll`

- parse result of `ls -l` with bash script

**drwxr-xr-x** : This string of letters, drwxrwxrwx , **represents the permissions that are set for this folder**. 

**-rw-r--r--** :-rwxr-xr-x for a regular file whose user class has full permissions and whose group and others classes have only the read and execute permissions.

#### Declaring Variables

==const / let / var==

constant: can only be assigned once;

let can be reassigned;

var can be reassigned too (old school)

==string / num / boolean / array / object==

array: 

const array or object, you can change items

const favouriteFruit = ['apple','orange','pear'];

比如 苹果变李子，但是 favouriteFruit 不能直接写 【“fafagag”】

favouriteFriut 【1】=“lemon”

 ['apple','lemon','pear'];   // const still can change item

const favouriteFruit =[‘fafagag’] // error!



==redirection to other folder, and rename “cooking journal”, git doesnt care==



### 20220928 Function - Greg F

some ==APIs== ask us to pass functions as parameters (a “**callback** fucntion”)

```javascript
9function sayHello(Name){
consol.log("Hello", name)
}
setTimeout(sayHello, 5000);

```

List processing and asynchronous operations use function passing “pass in a **callback**”(==delay==)

5000 - how many millisecond start excute the function, 5000 millisecond wait to call the function.

```javascript
setTimeout((name)=>console.log("Hello", name), 5000);

setTimeout(()=>console.log("Hello"), 5000);
```

👆  (  ) passong in an anonymous 空空號意思passing 一個匿名的variable

​     => passing in a lambda / passing in a function

​	passing in a callback

### 20221003 Rock paper scissors_Greg

MVP: 

npm: node package manager

```json
{
  "name": "2022-10-3-rockpaperscissor",
  "version": "0.1.0",
  "description": "Rock, paper, scissors termial game",
  "main": "index.js",
  "type": "module",
  "scripts": {
    "dosomethingcool": "echo Hi",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Yan Liu",
  "license": "ISC",
  "dependencies": {
    "readline-sync": "^1.4.10"
  }
}
```

"readline-sync": "^1.4.10"

"readline-sync": "*"         I need the lastest the version

^ : allow change next time, when you do install npm

1.4.9 => you locked the version update, 

Greg recommended to use ^, do `install npm`, automatically update to the lastest.

1.4.10  -- 4 and 10 is changable number

1.5.10 - small change, code works also!

2.0.0 - 2 is lock number, now the code is useless

Example, ` "readline-sync": "1.4.9"` -> `install npm` now package and package-lock all change to 1.4.9

`"readline-sync": "^1.4.10"`-> `npm install readline-sync`-> everything changed to the lastest version.

1 -> major version

4-> minor version

10-> patch version --> everytime update the patch when you do `install npm`











