<div align="center">
<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTNc9x1b405zUvHTsRm6f3WdimHs1m1YbZ1eQ&usqp=CAU" alt="" />
</div>

# What is Nodejs
* Node.js is an open-source server side runtime environment built on Chrome's V8 JavaScript engine. It provides an event driven, non-blocking (asynchronous) I/O and cross-platform runtime environment for building highly scalable server-side application using JavaScript.

* Node.js can be used to build different types of applications such as command line application, web application, real-time chat application, REST API server etc. However, it is mainly used to build network programs like web servers, similar to PHP, Java, or ASP.NET.

***Node.js was written and introduced by Ryan Dahl in 2009. Visit Wikipedia to know the history of Node.js.***

---

## Core Topics In Nodejs

* [Local Modules](#)
* `Built In Modules`
   * [**fs** module](#)
   * [**os** module](#)
   * [**path** module](#)
   * [**url** module](#)
   * [**events** module](#)
   * [**http** module](#)
* [Nodejs REPL](#)
* [Environment Variable](#)
* [Stream & Buffers](#)
* [Pipe Stream](#)

## Miscellanious
* [Install Nodejs In Android](#)
* [Manage Nodejs Version](#)
* [Styling Console](#)
* [Getting User Input](#)


---

<p id=""></p>

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

<p id=""></p>

### Local Modules:
```js

```
[⬆ Back to Top](#top)

<p id=""></p>

### Local Modules:
```js

```
[⬆ Back to Top](#top)

<p id=""></p>

### Local Modules:
```js

```
[⬆ Back to Top](#top)

<p id=""></p>

### Local Modules:
```js

```
[⬆ Back to Top](#top)

<p id=""></p>

### Local Modules:
```js

```
[⬆ Back to Top](#top)

<p id=""></p>

### Local Modules:
```js

```
[⬆ Back to Top](#top)

<p id=""></p>

### Local Modules:
```js

```
[⬆ Back to Top](#top)

<p id=""></p>

### Local Modules:
```js

```
[⬆ Back to Top](#top)

