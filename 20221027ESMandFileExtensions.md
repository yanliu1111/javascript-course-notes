==Yan L *—* Yesterday at 5:20 PM==

Just want to share this, if I didnt use "type":"module", then I used 

```
const express = require("express");
const app = express();
const tasks = require("./routes/task");
```

 I don't need to write task.js and it works.But I know Greg said this is old style.

==Greg Fenton==

`module` \=== ECMAScript Modules (ESM)
`common` === Common JavaScript Modules (CJS)
ESM is "new" -- introduced in 2015.
CJS is "the OG" and has been around since the 90s.
WARNING: this stuff gets U-G-L-Y....keep reading at your own risk.  YOU HAVE BEEN WARNED.

==Greg Fenton==

1. Node explicitly documents that the ESM does NOT do automatic file extensions when importing:  https://nodejs.org/api/esm.html#esm_customizing_esm_specifier_resolution_algorithm

2. Note the part of the Node documentation where it states: 

> *The file extension is always necessary for these.* 

https://nodejs.org/api/esm.html#terminology

And in the section following that: 

> A file extension must be provided when using the import keyword to resolve relative or absolute specifiers

--------------------- HOWEVER  

> However, there are systems implemented before the ES6 spec was written that implements ES6-like import syntax such as Typescript and Babel. These systems assumed you can exclude file extensions in your imports. If you are using such a system to compile your ES6 imports to ES5 syntax you can exclude file extensions, sometimes, depending on if the version of the compiler you are using supports it. 

 So if you are using some other system to translate you JS before you give it to node to run, that other system can "interpret" the file extension and will include it in the JS that it generates for Node to run.

-------------------- (I warned you!) --------------------

1. There have been MANY calls for node to support automatic file extension detection....some from people that consider this a bug in Node (it is not a bug since node is DOCUMENTED to behave this way), and other calls from people who actually understand what they are talking about 

 https://lightrun.com/answers/facebook-jest-esm-should-require-file-extensions

[ESM should require file extensions](https://lightrun.com/answers/facebook-jest-esm-should-require-file-extensions)

Lightrun Answers. Where developers land when they google for errors and exceptions

2. BTW: when we get to using React for the UI layer -- it supports imports without specifying extensions because (for most React development environments) they leverage Babel (mentioned above).