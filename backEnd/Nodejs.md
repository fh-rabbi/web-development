<h1 align="center">Node Js</h1>
 
#### 🤔 `What is node js?`

> ***Node.js is an open-source, cross-platform, back-end JavaScript runtime environment that runs on a JavaScript Engine and executes JavaScript code outside a web browser, which was designed to build scalable network applications.***


## 📚 Index Of Contents:

* [Local Modules](#local)
* `Built In Modules:`
    * [fs Module]()
    * [os Module]()
    * [path Module]()
    * [url Module]()
    * [events Module]()
    * [http Module]()
* `External Modules`
* Stream & Buffers
* Pipe Stream

### Local Modules:
```js
// main.js
const {getAge,demo} = require('./md');
const data = require('./md');

// console.log(getAge(2002));
// console.log(demo('Smith'));
console.log(data);

========================

//md.js
// 1:
exports.getAge = (birthYear) => {
  let currYear = new Date().getFullYear();
  return currYear - birthYear;
}

// 2:
function demo(name){
  return `Hello ${name}`
}
exports.demo = demo;

// 3:
const fruits = ['apple','orange','banana','grapes'];
const text = 'Im a text!';

module.exports = {
  fruits,
  text
}
```

### Built In Modules:

* 🌎 [View Modules](https://www.w3schools.com/nodejs/ref_modules.asp)

### events:
```js
const EventEmitter = require('events');
const event = new EventEmitter();

event.on('waterFull', (sc) => {
  console.log('Please turn of the motor! ' + sc );
})

event.emit('waterFull', 200);
```

### http:

1. `Basic Server Creating:`

```js
const http = require('http');

const PORT = 3000;

const server = http.createServer((req,res)=>{
  res.write('Hello Im Server!');
  res.end();
})

server.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

2. `http routing on server:`

```js
const http = require('http');

const PORT = 3000;

const server = http.createServer((req,res)=>{
  if(req.url === '/'){
    res.writeHead(200,{'Content-Type':'text/plain'});
    res.write('Hello Im Home Page!');
    res.end();
  }
  else if(req.url === '/about'){
    res.writeHead(200,{'Content-Type':'text/plain'});
    res.write('Hello Im About Page!');
    res.end();
  }
  else{
    res.writeHead(404,{'Content-Type':'text/plain'});
    res.write('Oops! Not found.');
    res.end();
  }
})

server.listen(PORT, () => {
  console.log(`Server running on http://localhost:${PORT}`);
});
```

### url:

1 `The URL module splits up a web address into readable parts.`
2. `Parse an address with the url.parse() method, and it will return a URL object with each part of the address as properties`

```js
const http = require('http');
const url = require('url');
const fs = require('fs');

http.createServer((req,res)=>{
  
  var q = url.parse(req.url, true);
  var filename = '.' + q.pathname;
  
  fs.readFile(filename, 'utf-8', (err,data) => {
    if(err){
      return res.end('Not found');
    }
    res.write(data);
    res.end();
  })
}).listen(8080);
```

### Stream & Buffers:
```js
const http = require('http');
const fs = require('fs');

const server = http.createServer((req,res)=>{
  // Method 1:
  // fs.readFile('b.txt', 'utf-8', (err,data)=>{
  //   console.log(data);
  //   res.end('ok');
  // })
  
  // Method 2:
  // const rstream = fs.createReadStream('b.txt');        
  // rstream.on('data', (chunk) => {
  //   res.write(chunk);
  //   // console.log(chunk.toString());
  // })
  // rstream.on('end', ()=>{
  //   console.log();
  //   res.end('End');
  // })
  // rstream.on('error', (err)=>{
  //   console.log(err);
  //   res.end('Not found');
  // })
  
  // Method 3:
  const rstream = fs.createReadStream('b.txt');        
  rstream.pipe(res);
  
})

server.listen(3000);
```



