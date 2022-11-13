<div align="center">
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTNc9x1b405zUvHTsRm6f3WdimHs1m1YbZ1eQ&usqp=CAU" alt="" />
</div>

# What is Nodejs
* Node.js is an open-source server side runtime environment built on Chrome's V8 JavaScript engine. It provides an event driven, non-blocking (asynchronous) I/O and cross-platform runtime environment for building highly scalable server-side application using JavaScript.

* Node.js can be used to build different types of applications such as command line application, web application, real-time chat application, REST API server etc. However, it is mainly used to build network programs like web servers, similar to PHP, Java, or ASP.NET.

***Node.js was written and introduced by Ryan Dahl in 2009. Visit Wikipedia to know the history of Node.js.***

---

<p id="top"></p>

## Core Topics In Nodejs

* [Local Modules](#local)
* `Built In Modules`
   * [**fs** module](#fs)
   * [**os** module](#os)
   * [**path** module](#path)
   * [**url** module](#url)
   * [**events** module](#events)
   * [**http** module](#http)
* [Environment Variable](#env)
* [Stream & Buffers](#stream)
* [Pipe Stream](#pipe)

## Miscellanious
* [Manage Nodejs Version](#nvm)
* [Styling Console](#styling)
* [Getting User Input](#userinput)

---

<p id="local"></p>

#### 🔹 Local Modules:
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
[⬆ Back to Top](#top)

<p id="fs"></p>

### 🔹 Fs Modules:
```js
#!/usr/bin/node
const fs = require("fs");
const chalk = require("chalk");

// Colors:
const red = chalk.red;
const cyan = chalk.cyan;

/* 
===================
| Asynchronous Way|
===================
*/
// Create a new file:
function createFile(){
   fs.writeFile('a.txt', 'apple', (err) => {
      if (err) {
         console.log('[*] Something went wrong!');
         return;
      }
      console.log('[*] File Created Successful!');
   });
}

// Read File:
function readFile(){
   fs.readFile('a.txt','utf-8', (err,data)=>{
      if(err){
         console.log('[*] Something went wrong!');
      }
      else{
         console.log('[*] File read Successful:');
         console.log('Content:'+ red(data));
      }
   });
}

// Create a folder:
function createFolder(){
   fs.mkdir('test',(err)=>{
      if(err){
         console.log(red('[*] Something went wrong!'));
      }
      else{
         console.log(cyan('[*] Folder Created Successful'));
      }
   });
}

// Read folder content:
function readFolder(){
   fs.readdir('./test', (err,data)=>{
      if(err){
            console.log(red('[*] Something went wrong!'));
         }
         else{
            console.table(cyan(data[0]));
         }
   });
}


/*
===================
| Synchronous Way |
===================
*/
// Create Folder:
function createFolder(){
   try {
      fs.mkdirSync('test2');
      console.log('[*] Folder Created Successful.');
   } catch (e) {
      console.log(e);
   }
}

// Update File:
function updateFile(){
   try {
      fs.appendFileSync('a.txt',' orange');
      console.log('[*] File Updated Successful.');
   } catch (e) {
      console.log(e);
   }
}

// Check if a folder exists:
console.log(fs.existsSync('test')); // --> return: true

// Rename a folder:
try {
  fs.renameSync('test', 'bug');
  console.log('Folder Renamed.');
} catch (err) {
  console.error(err);
}

// Remove a folder:
try {
   fs.rmSync('test2', { recursive: true, force: true });
   console.log('Folder deleted.');
} catch (e) {
   console.log(e);
}

```
[⬆ Back to Top](#top)

<p id="os"></p>

### 🔹 Os Modules:
```js

```
[⬆ Back to Top](#top)

<p id="path"></p>

### 🔹 Path Modules:
```js

```
[⬆ Back to Top](#top)

<p id="url"></p>

### 🔹 Url Modules:
```js

```
[⬆ Back to Top](#top)

<p id="http"></p>

### 🔹 Http Modules:
```js

```
[⬆ Back to Top](#top)

<p id="events"></p>

### 🔹 Events:
```js
const EventEmitter = require('events');
const event = new EventEmitter();

event.on('waterFull', (sc) => {
  console.log('Please turn of the motor! ' + sc );
})

event.emit('waterFull', 200);
```
[⬆ Back to Top](#top)

<p id="env"></p>

### 🔹 Environment Variable:
```js
// uid=10 node filename
// console.log(process.env.uid);

require("dotenv").config();
const name = process.env.UNAME;
console.log(name);

```
[⬆ Back to Top](#top)

<p id=""></p>

<p id="stream"></p>

### 🔹 Streams & Buffers:
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
[⬆ Back to Top](#top)

<p id="pipe"></p>

### 🔹 Pipe Streams:
```js
const rstream = fs.createReadStream('b.txt');        
rstream.pipe(res);
```
[⬆ Back to Top](#top)

<p id="nvm"></p>

### 🔹 Manage Nodejs Version:
1. ***First command***
   ```sh
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.2/install.sh | bash
   ```
2. ***Second command***
   ```sh
   export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
   [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" 
   ```
3. ***Third command***
   ```sh
   nvm install nodejs 14
   ```

[⬆ Back to Top](#top)

<p id="styling"></p>

### 🔹 Styling Console:
* ***npm i chalk@4.0.0***
* [Read Docs](https://www.npmjs.com/package/chalk)

[⬆ Back to Top](#top)

<p id="userinput"></p>

### 🔹 Getting User Input:
```js
// Method 1:
const prompt = require("prompt-sync")();

const name = prompt("Type Your Name:")

console.log(`Hello, ${name}`);


// Method 2:
const inquirer = require('inquirer');

const questions1 = [
  {
    type: 'input',
    name: 'name',
    message: "What's your name?",
  },
];

const questions2 = [
  {
    type: 'input',
    name: 'name',
    message: "What's your name?",
  },
];

let name1;
let name2;
inquirer.prompt(questions1).then(answers1 => {
  name2 = answers1
  // console.log(`Name1: ${answers.name}!`);
  Demo(answers1);
});


function Demo(answers1){
   inquirer.prompt(questions2).then(answers2 => {
      name2 = answers2
      // console.log(`Name2: ${answers.name}!`);
      main(answers1,answers2);
   });
}

function main(a,b)
{
   console.log(a);
   console.log(b);
}


// Method 3:
const readline = require('readline').createInterface({
  input: process.stdin,
  output: process.stdout,
});

readline.question(`What's your name?`, name => {
  console.log(`Hi ${name}!`);
  readline.close();
});
```
[⬆ Back to Top](#top)

