<h1 align="center">Express.js</h1>

#### `🤔 What is express.js:`
> ***Express.js, or simply Express, is a back end web application framework for Node.js, released as free and open-source software under the MIT License. It is designed for building web applications and APIs. It has been called the de facto standard server framework for Node.js.***

<details>
<summary>Express function</summary>

1. [express.json()]()
2. [express.raw()]()
3. [express.text()]()
4. [express.urlencoded({extended: true})]()
4. [express.static()]()
4. [express.Router()]()

* `USAGE:`
    * *app.use(express.json())*

</details>

<details>
<summary>App Object</summary>

1. [app.locals]()
2. [app.mountpath]()
3. [app.all()]()
4. [app.METHOD()]()
5. [app.enable()]()
6. [app.disable()]()
7. [app.enabled()]()
8. [app.disabled()]()
9. [app.engin()]()
10. [app.set()]()
11. [app.get()]()
12. [app.listen()]()
13. [app.param()]()
14. [app.path()]()
15. [app.render()]()
16. [app.route()]()
17. [app.use()]()

</details>

<details>
<summary>Request Object</summary>

1. [req.baseUrl]()
2. [req.originalUrl]()
3. [req.path]()
4. [req.hostname]()
5. [req.ip]()
6. [req.method]()
7. [req.protocol]()
8. [req.params]()
9. [req.query]()
10. [req.body]()
11. [req.cookies]()
12. [req.signedCookies]()
13. [req.secure]()
14. [req.app]()
15. [req.route]()
16. [req.header('key')]()
17. [req.get]()
18. [req.accetps]()

</details>

<details>
<summary>Response Object</summary>

1. [res.app]()
2. [res.headersSent]()
3. [res.locals]()
4. [res.append()]()
5. [res.cookie()]()
6. [res.clearCookie()]()
7. [res.send()]()
8. [res.status()]()
9. [res.sendStatus()]()
10. [res.json()]()
11. [res.jsonp()]()
12. [res.format()]()
13. [res.location()]()
14. [res.redirect()]()
15. [res.sendFile()]()
16. [res.set()]()
17. [res.type()]()

</details>

<details>
<summary>Router</summary>

1. [router.all()]()
2. [router.METHOD()]()
3. [router.param()]()
4. [router.route()]()
5. [router.use()]()

</details>

<details>
<summary>Middleware</summary>

* *Middleware is a function*

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

</details>

<details>
<summary>File uploading</summary>

1. **index.js**

```js
const express = require('express');
const app = express();
const multer = require('multer');
const UPLOAD_FOLDER = './Uploads';
const PORT = 3000;

// define storage
const storage = multer.diskStorage({
  destination: (req,file,cb) => {
    cb(null,UPLOAD_FOLDER);
  },
  filename: (req,file,cb) => {
    cb(null,file.originalname);
  }
});

// upload logic
const upload = multer({
  storage: storage
  // limits: {fileSize: 1000000}
  // fileFilter: (req, file, cb) => {console.log(file)}
  // ^ if(){
  // cb(null,true)
  //} else {
  //    cb(new Error("There was an unknown error!"));
  //  }
});

// application route
app.get('/',(req,res) => {
  res.sendFile(__dirname+'/Uploads/index.html');
});

app.post('/', upload.fields([
    {
      name: 'avatar',
      maxCount: 2
    }
  ]),(req,res) => {
  res.send('File uploaded!');
});

// default error handler
app.use((err, req, res, next) => {
  if (err) {
    if (err instanceof multer.MulterError) {
      res.status(500).send("There was an upload error!");
    } else {
      res.status(500).send(err.message);
    }
  } else {
    res.send("success");
  }
});

app.listen(PORT, ()=>{
  console.log('Server is running at http://localhost:'+PORT);
});

```

2. **index.html**

```html
<!DOCTYPE html>
<html>
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title></title>
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
</head>
<body>
  <h2>File Uploading</h2>
  <form action="http://localhost:3000" method="post" enctype="multipart/form-data" accept-charset="utf-8">
    <input type="file" name="avatar" multiple="" />
    <button type="submit">Upload</button>
  </form>
  
</body>
</html>
```

</details>


<details>
<summary>Template engine</summary>

1. **index.js**

```js
const express = require('express');
const app = express();
const path = require('path');
const hbs = require('hbs');

// set view engine
app.set('view engine', 'hbs');
// change default views dir to custom
app.set('views', `${__dirname}/temp`);
// use partials
hbs.registerPartials(`${__dirname}/temp/partials`);

app.get('/', (req, res) => {
  res.render('index',{
    demo: 'im dynamic data'
  });
});

app.get('/about', (req,res) => {
  res.render('about');
})

app.listen(3000);
```

2. **index.hbs**

```html
<!DOCTYPE html>
<html>
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title></title>
</head>
<body>

  {{>nav}}
  
 <h2>im </h2>
 <h1>{{demo}}</h1>

</body>
</html>
```

</details>

<details>
<summary>MVC Architechture</summary>


* #### MVC:
    * Models: `Database related files`
    * Views: `Public files`
    * Controllers: `Routes controllers`
    * Routes: `all routes`


* `Root dir:`
    * index.js
    * app.js
    * **models**
    * **Views**
    * **controllers**
    * **routes**

</details>
