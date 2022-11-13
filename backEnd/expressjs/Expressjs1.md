<h1 align="center">Express Js</h1>

## 📚 Table of contents:
1. [Create server]()
2. [Http methods]()
3. [Routes and routing]()
4. [Http response]()
5. `Http request:`
    * [with query parameter]()
    * [with route parameter]()
    * [with request header]()
    * [with post request]()
6. [Send & receive form data]()
7. [Environment variable]()
8. [Express middleware]()
9. [MVC Architechture]()

### Create server:
```js
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/', (req,res) => {
  res.send('Hello!'); 
});

app.listen(PORT, () => {
  console.log('Server is running at http://localhost:'+PORT);
});
```

### Http methods:
* get
* post
* put
* delete

### Routes & routing:
```js
/* 
======================
index.js
======================
*/
const express = require('express');
const app = express();
const router = require('./demo');
const PORT = 3000;

app.use(router);

// start server
app.listen(PORT, () => {
  console.log('Server is running at http://localhost:'+PORT);
});


/* 
======================
demo.js
======================
*/
const express = require('express');
const router = express.Router();

// handle request
router.get('/', (req,res) => {
  res.send('Hello!'); 
});

module.exports = router;
```

### Http response:
```js
const express = require('express');
const app = express();
const PORT = 3000;

app.get('/api', (req,res) => {
    // res.status(200);
    // res.statusCode = 208;
    // res.send('Hello there!');
    
    // res.status(209).send('Hello');
    // res.status(210).json({
    //   name: 'smith',
    //   age: 20,
    //   skills: ['C','Java','Python']
    // })
    
    // res.send(`<h1>Hello</h1>`);
    
    // res.sendFile(__dirname+"/views/index.html");
    
    // res.redirect('/');
    
    
    res.cookie('name','david');
    res.cookie('age',21);
    // for clear cookie:
    res.clearCookie();
    
    // set value in header:
    res.append('id','200');
    res.end('Okey.');
});

// start server
app.listen(PORT, () => {
  console.log('Server is running at http://localhost:'+PORT);
});
```

### Query parameter:
```js
/* request:
* http://localhost:3000/api?a=10&b=20
*/

const express = require('express');
const app = express();
const PORT = 3000;

app.get('/api', (req,res) => {
  const data = req.query;
  console.log(data);
  res.send(data);
});

// start server
app.listen(PORT, () => {
  console.log('Server is running at http://localhost:'+PORT);
});
```

### Routes parameter:
```js
/* request:
* http://localhost:3000/api/userName/smith/userId/200
*/

const express = require('express');
const app = express();
const PORT = 3000;

app.get('/api/userName/:uName/userId/:uId', (req,res) => {
  const data = req.params;
  console.log(data);
  res.send(data);
});

// start server
app.listen(PORT, () => {
  console.log('Server is running at http://localhost:'+PORT);
});
```

### Request header:
```js
/* request:
* http://localhost:3000/api
* required set header (key:value)!
*/

const express = require('express');
const app = express();
const PORT = 3000;

app.get('/api', (req,res) => {
  const name = req.header('name');
  const age = req.header('age');
  console.log(`Name: ${name} Age: ${age}`);
  res.send({
    name,
    age
  });
});

// start server
app.listen(PORT, () => {
  console.log('Server is running at http://localhost:'+PORT);
});
```

### Post request:
```js
const express = require('express');
const app = express();
const bodyParser = require('body-parser');
const PORT = 3000;

// parse the body for receive body data:
app.use(bodyParser.urlencoded({extended:false}));
app.use(bodyParser.json());

app.post('/login', (req,res) => {
  const number = req.body.number;
  const password = req.body.password; 
  res.status(200).json({
    number,
    password
  });
  console.log(req.body);
});

// start server
app.listen(PORT, () => {
  console.log('Server is running at http://localhost:'+PORT);
});
```

### Environment variable:
> it used for store private data.

```js
// index.js
require('dotenv').config();
const envVar = process.env;
const {PORT,URL} = envVar;
console.log(PORT);
console.log(URL);

// .env
PORT=3000
URL=https://demo.com/api/user
```

### Express middleware:

> *Middleware is a function*

* #### Middleware functions can perform the following tasks:
    * `Execute code`
    * `Make changes to the req & res object `
    * `End the req & res cycle`
    * `Call the next Middleware in the stack`

* #### Types of middleware:
    * `Application level middleware`
        * app.use()
        * app.METHOD()
    * `Router level middleware`
        * router.use()
        * router.METHOD()
    * `Built in middleware`
        * express.static
        * express.json
        * express.urlencoded
    * `Third party middleware`
        * body parser
        * cookie parser

```js
// dependencies
const express = require('express');
const app = express();

// static middleware:
// for access (style.css,image etc.)
app.use(express.static('public'));

// main logic
const myMiddleWare = (req,res,next) => {
  // 1. execute code
  console.log('Im MiddleWare...!');
  
  // 2. Make changes the req Object:
  req.demo = 'Hey! Im demo!';
  
  // 3. end the req,res cycle
  res.end();
  
  // 4. call the next middleware
  next();
};

// apply middleware in all route
app.use(myMiddleWare);

app.get('/', (req,res) => {
  res.send('Hello Im Home Route.');
  console.log('Im Home Route...!');
  console.log(req.demo);
});

app.get('/about', (req,res) => {
  res.send('Hello Im About Route.');
  console.log('Im About Route...!');
  console.log(req.demo);
});

// error handling middleware
app.use((req,res,next) => {
  res.send('<h1>404! Page Not found...</h1>');
});

// other error handling middleware
app.use((err,req,res,next) => {
  res.status(500).send('Something break!')
});

// start server
app.listen(3000, () => {
  console.log('Server running...');
});
```

### MVC Architechture:

* #### MVC:
    * Models
    * Views
    * Controllers
    * Routes
```js

```
