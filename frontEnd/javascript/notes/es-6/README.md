## 💡 Es-6 Cheatsheets:

01. **New ES6 syntax:**
    * `Variables`
    * `Default function parameters`
    * `Rest parameter` *The rest parameter (...) packs the elements into an array.*
    * `Spread operator` *The spread operator (...) unpacks the elements of an iterable object.*
    * `Object literal syntax extensions`
    * `for...of & for...in loop`
    * `Octal and binary literals`
    * `Template literals`

02. **Destructuring:**
    * `Array Destructuring`
    * `Object Destructuring`

03. **ES6 Modules:**
    * `ES6 modules`

04. **ES6 Classes:** `A JavaScript class is a blueprint for creating objects. A class encapsulates data and functions that manipulate data.`
    * `Class`
    * `Getters and Setters`
    * `Class Expression`
    * `Static methods`
    * `Static Properties`
    * `Computed property`
    * `Inheritance`

05. **Arrow Functions:**
    * `Arrow functions syntax`
    * `Arrow functions: when you should not use`

06. **Symbol:**
    * `Symbol`

07. **Iterators & Generators:**
    * `Iterators`
    * `Generators`
    * `yield`

08. **Promises:**
    * `Promises`
    * `Promise chaining`
    * `Promise composition: Promise.all() & Promise.race()` 
    * `Promise error handling`

09. **ES6 collections:**
    * `Map`
    * `Set`

10. **Array extensions:**
    * `Array.of()`
    * `Array.from()`
    * `Array.find()`
    * `Array.findIndex()`


11. **Object extensions:**
    * `Object.assign()`
    * `Object.is()`

12. **String extensions:**
    * `String startsWith()`
    * `String endsWith()`
    * `String includes()`

13. **Proxy & Reflection:**
    * `Proxy`
    * `Reflection`

## ☀️ New ES6 syntax:

<details>
<summary>Variables</summary>

1. ***let***:
   * `Variables are declared using the let keyword are block-scoped, are not initialized to any value, and are not attached to the global object.`
   * `Redeclaring a variable using the let keyword will cause an error.`
   * `A temporal dead zone of a variable declared using the let keyword starts from the block until the initialization is evaluated.`
2. ***const:***
   * `The const keyword creates a read-only reference to a value. The readonly reference cannot be reassigned but the value can be change.`
   * `The variables declared by the const keyword are blocked-scope and cannot be redeclared.`

</details>

<details>
<summary>Default functions parameters</summary>

```js
// Example 1:
function say(message='Hi') {
    console.log(message);
}

say(); // 'Hi'
say(undefined); // 'Hi'
say('Hello'); // 'Hello'

// Example 2:
function createDiv(height = '100px', width = '100px', border = 'solid 1px red') {
    let div = document.createElement('div');
    div.style.height = height;
    div.style.width = width;
    div.style.border = border;
    document.body.appendChild(div);
    return div;
}

// Example 3:
function put(toy, toyBox = []) {
    toyBox.push(toy);
    return toyBox;
}

console.log(put('Toy Car'));
// -> ['Toy Car']
console.log(put('Teddy Bear'));
// -> ['Teddy Bear'], not ['Toy Car','Teddy Bear']

// Example 4:
function date(d = today()) {
    console.log(d);
}
function today() {
    return (new Date()).toLocaleDateString("en-US");
}
date();

// Example 5:
function requiredArg() {
   throw new Error('The argument is required');
}
function add(x = requiredArg(), y = requiredArg()){
   return x + y;
}

add(10); // error
add(10,20); // OK

// Example 6:
function add(x = 1, y = x, z = x + y) {
    return x + y + z;
}

console.log(add()); // 4

// Example 7:
let taxRate = () => 0.1;
let getPrice = function( price, tax = price * taxRate() ) {
    return price + tax;
}

let fullPrice = getPrice(100);
console.log(fullPrice); // 110

```

</details>

<details>
<summary>Rest parameters</summary>

```js
// rest parameter:
function nums(x,y,z){
  console.log(x,y);
  for(fruit in z){
    console.log(`Fruit ${fruit} = ${z[fruit]}`);
  }
}
let fruits = ['apple','orange','banana','grapes'];
nums(10,20,fruits);


// Example 1:
function sum(a,b,...c){
  let total = a+b;
  for(let value of c){
    total += value;
  }
  console.log(total);
}
sum(1,2,3,4,5,6);


// Example 2:
// Calculate the total of numbers only:
function demo(...arg){
  return arg
  .filter(nums => typeof nums == 'number')
  .reduce((prev,curr) => prev+curr);
}
const result = demo('hi',1,2,undefined,3,4);
console.log(result);


// Example 3:
function funney(type,...arg){
  return arg.filter(x => typeof x == type);
}
let r = funney('number',10,20,'hi',100,'hello',null,undefined);
console.log(r);


// rest parameter in a dynamic function
var showNumbers = new Function('...numbers', 'console.log(numbers)');
showNumbers(1, 2, 3);

```
</details>

<details>
<summary>Spread operator</summary>

### Summary:

* The spread operator is denoted by three dots (…).
* The spread operator unpacks elements of iterable objects such as arrays, sets, and maps into a list.
* The rest paramter is also denoted by three dots (…). However, it packs the remaining arguments of a function into an array.
* The spread operator can be used to clone an iterable object or merge iterable objects into one.

```js
// Simple example of spread operator:
let nums1 = [1,2,3];
let nums = [...nums1,4,5,6];
console.log(nums);

// Example 1:
function compare(a, b) {
    return a - b;
}
let arr = [1,2];
let result = compare(...arr);
console.log(result);

// Example 2:
let rivers = ['Nile', 'Ganges', 'Yangte'];
let moreRivers = ['Danube', 'Amazon'];
rivers.push(...moreRivers);
console.log(rivers);

// Example 3 (Constructing array literal):
let initialChars = ['A', 'B'];
let chars = [...initialChars, 'C', 'D'];
console.log(chars); // ["A", "B", "C", "D"]

// Example 4 (Concatenating arrays1):
let numbers = [1, 2];
let moreNumbers = [3, 4];
let allNumbers = [...numbers, ...moreNumbers];
console.log(allNumbers); // [1, 2, 3, 4]

// Example 5 (Copying an array:
let scores = [80, 70, 90];
let copiedScores = [...scores];
console.log(copiedScores); // [80, 70, 90]

// Awesome Example:
chars = ['A', ...'BC', 'D']; //> ...BC wil be B C (separate)   
console.log(chars); // ["A", "B", "C", "D"]

```
</details>

<details>
<summary>Objects literal syntax</summary>

```js
// Object property initializer shorthand:
function createMachine(name, status) {
    return {
        name,
        status
    };
}


{
  let name = 'Computer',
    status = 'On';

  let machine = {
   name,
   status
  };
  console.log(machine);
}


// Computed property name:
{
  let name = 'machine name';
  let machine = {
     [name]: 'server',
    'machine hours': 10000
  };

  console.log(machine[name]); // server
  console.log(machine['machine hours']); // 10000
  
  //
  let prefix = 'machine';
  machine = {
    [prefix + ' name']: 'server',
    [prefix + ' hours']: 10000
  };
  console.log(machine['machine name']); // server
  console.log(machine['machine hours']); // 10000
}


// Concise method syntax:
{
  // Regular syntax:
  var server = {
	name: "Server",
	restart: function () {
		console.log("The" + this.name + " is restarting...");
	}
 };
 
 // Es-6 syntax:
 var server = {
    name: 'Server',
    restart() {
        console.log("The" + this.name + " is restarting...");
    }
  };
}


// spaces in the property name:
var server = {
    name: 'Server',
    restart() {
        console.log("The " + this.name + " is restarting...");
    },
    'starting up'() {
        console.log("The " +  this.name + " is starting up!");
    }
};

server['starting up']();
```

</details>

<details>
<summary>for…of</summary>

### Summary:
1. `Use the for...of loop to iterate over elements of an iterable object.`
2. `for…of iterates over the element of an array`
3. `for…in statement iterates over the properties `

```js
// Iterating over arrays:
let scores = [80, 90, 70];
for(var score of scores){
  score += 5;
  console.log(score);
}

let colors = ['Red', 'Green', 'Blue'];
for(var [index,color] of colors.entries()){
  console.log(`${color} is at index ${index}`);
}

// for(var y of colors.entries()){
//   console.log(y);
// }


// In-place object destructuring with for…of:
const ratings = [
    {user: 'John',score: 3},
    {user: 'Jane',score: 4},
    {user: 'David',score: 5},
    {user: 'Peter',score: 2},
];
let total = 0;
for(var {score} of ratings){
  total += score;
}
console.log(total);


// Iterating over strings:
let str = 'abc';
for(var x of str){
  console.log(x);
}


// Iterating over Map objects:
colors = new Map();
colors.set('red', '#ff0000');
colors.set('green', '#00ff00');
colors.set('blue', '#0000ff');

for(var value of colors){
  console.log(value);
}


// Iterating over set objects:
let fruits = new Set(['apple','banana','orange']);
for(fruit of fruits){
  console.log(fruit);
}


// for...of vs. for...in:
let scores = [10,20,30];
scores.message = 'Hi';

console.log("for...in:");
for (let score in scores) {
  console.log(score); 
}

console.log('for...of:');
for (let score of scores) {
  console.log(score);
}
```

</details>

<details>
<summary>Octal and binary literals</summary>

### Summary:
1. `Octal literals start with 0o followed by a sequence of numbers between 0 and 7.`
2. `Binary literals start with 0b followed by a sequence of number 0 and 1.`


```js
// Octal literals:
var x = 057; //> Es-5 syntax
console.log(x); // 47

var x = 058;
console.log(x); //> 58

let c = 0o51; //> Es-6 syntax
console.log(c); //> 41 


// Binary literals:
let e = parseInt('111',2);
console.log(e); // 7

let f = 0b1111;
console.log(f); // 7

```

</details>

<details>
<summary>Template literals</summary>

```js
// Multiline strings:
let msg = 'Multiline \n\
string';

console.log(msg);
//Multiline
//string

msg = ['This text',
         'can',
         'span multiple lines'].join('\n');   
console.log(msg);

let text = `hello 
    guys`;
console.log(text);


// Complex Example:
let {title, excerpt, body, tags} = post;

let postHtml = `<article>
<header>
    <h1>${title}</h1>
</header>
<section>
    <div>${excerpt}</div>
    <div>${body}</div>
</section>
<footer>
    <ul>
      ${tags.map(tag => `<li>${tag}</li>`).join('\n      ')}
    </ul>
</footer>`;


// Tagged templates literals:
function format(literals, ...substitutions) {
    let result = '';

    for (let i = 0; i < substitutions.length; i++) {
        result += literals[i];
        result += substitutions[i];
    }
    // add the last literal
    result += literals[literals.length - 1];
    return result;
}

let quantity = 9,
    priceEach = 8.99,
    result = format`${quantity} items cost $${(quantity * priceEach).toFixed(2)}.`;

console.log(result); // 9 items cost $80.91.
```
</details>

## ☀️ Destructuring:

<details>
<summary>Array destructuring</summary>

```js
// Array destructuring:
function get_scores(){
  return [50,60,70,80,90];
}
let [x,y,...z] = get_scores();
console.log(x,y,z);

// Variable swaping:
var a = 10 , b = 20;
var [a,b] = [b,a];
console.log(a);

// Setting default values:
let get_items = () => {
  return [10,20];
};
let item = get_items();
let third_item = item[2] != undefined ? item[2] : 0;
console.log(third_item);
// ANOTHER METHOD:
let [,,t=0] = get_items();
console.log(t);

// If the getItems() function doesn’t return an array and you expect an array, the destructing assignment will result in an error:
function getItems() {
    return null;
}

let [x = 1, y = 2] = getItems();

// A typical way to solve this is to fallback the returned value of the getItems() function to an empty array like this:
function getItems() {
    return null;
}

let [a = 10, b = 20] = getItems() || [];

console.log(a); // 10
console.log(b); // 20


// Nested array destructuring:
function getProfile() {
    return [
        'John',
        'Doe',
        ['Red', 'Green', 'Blue']
    ];
}
let [fName,lName,[c1,c2,c3]] = getProfile();
console.log(fName,lName,c1,c2,c3);


// Let see some Example:
// Swapping variables:
let a = 10, 
    b = 20;

[a, b] = [b, a];

console.log(a); // 20
console.log(b); // 10


// Functions that return multiple values:
function stat(a, b) {
    return [
        a + b,
        (a + b) / 2,
        a - b
    ];
}
let [sum,div,sub] = stat(10,20);
console.log(sum,div,sub);
```
</details>

<details>
<summary>Object destructuring</summary>

```js
let person = {
    firstName: 'John',
    lastName: 'Doe'
};
let {firstName:fName,lastName:lName} = person;
console.log(fName,lName);


// Setting default values:
let person2 = {
    firstName: 'John',
    lastName: 'Doe',
    currentAge: 28
};

let { firstName, lastName, middleName = '', currentAge: age = 18 } = person2;

console.log(middleName); // ''
console.log(age); // 28


// Destructuring a null object:
function getPerson() {
    return null;
}
let { firstName, lastName } = getPerson() || {}; // you can use the OR operator (||) to fallback the null object to an empty object:
console.log(firstName, lastName);


// Nested object destructuring:
{
  let employee = {
      id: 1001,
      name: {
          firstName: 'John',
          lastName: 'Doe'
      }
  };
  let {id,name:{firstName,lastName},name} =nemployee;
  console.log(id);
  console.log(firstName); // John
  console.log(lastName); // Doe
  // It’s possible to do multiple assignement of a property to multiple variables:
  console.log(name);
}


// Destructuring function arguments:
{
  let display = ({firstName,lastName}) => console.log(`${firstName} ${lastName}`);

  let person = {
      firstName: 'John',
      lastName: 'Doe'
  };
  
  display(person);
}

```
</details>
  
## ☀️ Es-6 Modules:

<details>
<summary>Modules</summary>

```js
// module.js
export let message = 'Hi';

export function getMessage() {
  return message;
}

export function setMessage(msg) {
  message = msg;
}

export class Logger {
}

// export all var,func etc in the last of the code:
function foo() {
   console.log('foo');
}

function bar() {
  console.log('bar');
}
export {foo};

// export with aliases:
function add( a, b ) {
   return a + b;
}

export { add as sum };

// ========================
//  main.js
import {message,foo} from './module.js';
// other way:
import {message as msg} from './module.js';
// import all in one:
import * as data from './module.js';

// Re-exporting a binding:
import { sum } from './math.js';
export { sum };

// The following statement is equivalent to the statements above:
export {sum} from './math.js';
// another tricks:
export { sum as add } from './math.js';
export * from './cal.js';


// Importing without bindings:
// array.js
if (!Array.prototype.contain) {
  Array.prototype.contain = function(e) {
    // contain implementation
    // ...
  };
}

//
import './array.js';
[1,2,3].contain(2); // true


// [[[[[[[[[]]]]]]]]][[[[]]]]
// Default exports:
// sort.js:
export default function(arr) {
  // sorting here
} 

// import the above module:
import sort from './sort.js';
sort([2,1,3]);


// ======================
// Default and normal:
// sort.js
export default function(arr) {
  // sorting here
}
export function heapSort(arr) {
  // heapsort
}

import sort, {heapSort} from './sort.js';
sort([2,1,3]);
heapSort([3,1,2]);
// ======================

```
</details>
  
## ☀️ Es-6 Classes:

<details>
<summary>Class syntax</summary>

```js
// ES6 class declaration:
class Person {
    constructor(name) {
        this.name = name;
    }
    getName() {
        return this.name;
    }
}

```
</details>

<details>
<summary>Getters and Setters</summary>

```js
// 
class data {
  constructor(name){
    this.name = name;
  }
  get name(){
    return this._name;
  }
  set name(new_name){
    if(new_name == ''){
      console.log(`The name can't be empty!`);
    }else{
      this._name = new_name;
    }
  }
}

let person1 = new data('smith');
console.log(person1);

person1.name = 'rabbi'; // setter method
let a = person1.name; // getter method
console.log(a);


// Complex Example:
let meeting = {
    attendees: [],
    add(attendee) {
        console.log(`${attendee} joined the meeting.`);
        this.attendees.push(attendee);
        return this;
    },
    get latest() {
        let count = this.attendees.length;
        return count == 0 ? undefined : this.attendees[count - 1];
    }
};

meeting.add('John').add('Jane').add('Peter');
console.log(`The latest attendee is ${meeting.latest}.`);

```
</details>

<details>
<summary>Class Expression</summary>

```js
// Class expression:
let Person = class {
    constructor(name) {
        this.name = name;
    }
    getName() {
        return this.name;
    }
};
let person1 = new Person('smith',20);
console.log(person1);


// First-class citizen:
// It means that you can pass a class into a function, return it from a function, and assign it to a variable.
function demo(aClass){
  return new aClass();
}

let data = demo(class{
  say_hi(){
   console.log('Hello geek!'); 
  }
});
data.say_hi();


// Singleton:
let app = new class {
    constructor(name) {
        this.name = name;
    }
    start() {
        console.log(`Starting the ${this.name}...`);
    }
}('Awesome App');

app.start(); // Starting the Awesome App...

```
</details>

<details>
<summary>Static methods</summary>

```js
class Person {
	constructor(name) {
		this.name = name;
	}
	getName() {
		return this.name;
	}
	static createAnonymous(gender) {
		let name = gender == "male" ? "John Doe" : "Jane Doe";
		return new Person(name);
	}
}

let p1 = new Person('smith');
console.log(p1);
// console.log(p1.createAnonymous());
let r = Person.createAnonymous();
console.log(r);

```
</details>

<details>
<summary>Static Properties</summary>

```js
class demo {
  static name = 'rabbi';
}
console.log(demo.name);


// access the static property in a static method:
{
  class Item {
	static count = 0;
	static getCount() {
		return Item.count;
	}
  }

  console.log(Item.getCount()); // 0
}


// access a static property in a class constructor or instance methods:
class Item {
	constructor(name, quantity) {
		this.name = name;
		this.quantity = quantity;
		this.constructor.count++;
	}
	static count = 0;
	static getCount() {
		return Item.count++;
	}
}


//
{
  class Item {
	constructor(name, quantity) {
		this.name = name;
		this.quantity = quantity;
		this.constructor.count++;
	}
	static count = 0;
	static getCount() {
		return Item.count++;
	}
  }
  
  let pen = new Item("Pen", 5);
  let notebook = new Item("notebook", 10);
  
  console.log(Item.getCount()); // 2
}

```
</details>

<details>
<summary>Computed property</summary>

```js
let propName = 'c';
let data = {
  a: 1,
  b: 2,
  [propName]: 3
};
console.log(data.c);


// Like an object literal, you can use computed properties for getters and setters of a class. For example::
let name = 'fullName';

class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
  get [name]() {
    return `${this.firstName} ${this.lastName}`;
  }
}

let person = new Person('John', 'Doe');
console.log(person.fullName);

```
</details>

<details>
<summary>Inheritance</summary>

```js
class data1 {
  constructor(name,age){
    this.name = name;
    this.age = age;
  }
}
let p1 = new data1('smith',20);
console.log(p1);

// Inheritance:
class data2 extends data1 {
  constructor(name,age,job=''){
    super(name,age);
    this.job = job;
  }
}
let p2 = new data2('david','22','STUDENT');
console.log(p2);
```
</details>

## ☀️ Arrow Function:
<details>
<summary>Arrow function syntax</summary>

```js
const sum = (x,y) => x+y;
let result = sum(10,20);
console.log(result);
```
</details>

<details>
<summary>When you should not use the arrow functions in ES6</summary>

1. `An arrow function doesn’t have its own this value and the arguments object. Therefore, you should not use it as an event handler, a method of an object literal, a prototype method, or when you have a function that uses the arguments object.`
2. `Avoid using the arrow function for event handlers, object methods, prototype methods, and functions that use the arguments object.`
   * **Event handlers**
   * **Object methods**
   * **Prototype methods**
   * **Functions that use the arguments object**

```js
// Event handlers:
// value of this in arrow function will be window object
const counter = {
  count: 0,
  next: () => ++this.count,
  current: () => this.count
};
console.log(counter.next());


// Object methods:
const counter = {
  count: 0,
  next: () => ++this.count,
  current: () => this.count
};
console.log(counter.next());


// Prototype methods:
function Counter() {
    this.count = 0;
}

Counter.prototype.next = () => {
    return this.count;
};

Counter.prototype.current = () => {
    return ++this.next;
};


// Functions that use the arguments object:
const concat = (separator) => {
    let args = Array.prototype.slice.call(arguments, 1);
    return args.join(separator);
}
```
</details>

## ☀️ Symbol:
<details>
<summary>View Symbol</summary>

```js
let s = Symbol('foo');
console.log(Symbol() === Symbol()); // false
```
</details>

## ☀️ Iterators & Generators:
<details>
<summary>Iterators</summary>

</details>

<details>
<summary>Generators</summary>

</details>

<details>
<summary>yield</summary>

</details>

## ☀️ Promises:

<details>
<summary>Promises creating</summary>

```js
let p1 = new Promise((resolve,reject)=>{
  resolve('Im resolved from p1');
})
.then(res=>console.log(res))
.catch(err=>console.log(err));
```
</details>

<details>
<summary>Promise chaining</summary>

```js
const task1 = () => {
  return new Promise((resolve,reject)=>{
    resolve('Im taskOne...');
  });
};

const task2 = () => {
  return new Promise((resolve,reject)=>{
    resolve('Im taskTwo...');
  });
};

const task3 = () => {
  return new Promise((resolve,reject)=>{
    resolve('Im taskThree...');
  });
};
task1()
.then(res=>console.log(res))
.then(task2)
.then(res=>console.log(res))
.then(task3)
.then(res=>console.log(res))
.catch(err=>console.log(err));
```
</details>

<details>
<summary>Promise composition: Promise.all() & Promise.race()</summary>

1. `The Promise.all() method accepts a list of promises and returns a new promsie that resolve to an array of results of the input promises if all the input promises resolved; or reject with an error of the first rejected promise.`
2. `Use the Promise.all() method to aggregate results from multiple asynchronous operations.`

```js
const p1 = new Promise((resolve,reject)=>{
  setTimeout(function() {
    console.log('Promise 1 resolved');
    resolve('Im resolved from p1');
  }, 1000);
});

const p2 = new Promise((resolve,reject)=>{
  setTimeout(function() {
    console.log('Promise 2 resolved');
    resolve('Im resolved from p2');
  }, 2000);
});

Promise.race([p1,p2])
.then(res=>console.log(res))
.catch(err=>console.log(err));

Promise.all([p1,p2])
.then(res=>console.log(res))
.catch(err=>console.log(err));
```
</details>

<details>
<summary>Promise error handling</summary>

```js
// Normal error (outside the promises);
function getUserById(id) {
    if (typeof id !== 'number' || id <= 0) {
        throw new Error('Invalid id argument');
    }

    return new Promise((resolve, reject) => {
        resolve({
            id: id,
            username: 'admin'
        });
    });
}


// Errors inside the Promises:
let authorized = false;

function getUserById(id) {
    return new Promise((resolve, reject) => {
        if (!authorized) {
            throw new Error('Unauthorized access to the user data');
        }

        resolve({
            id: id,
            username: 'admin'
        });
    });
}

try {
    getUserById(10)
        .then(user => console.log(user.username))
        .catch(err => console.log(`Caught by .catch ${error}`));
} catch (error) {
    console.log(`Caught by try/catch ${error}`);
}


// Calling reject() function:
let authorized = false;

function getUserById(id) {
    return new Promise((resolve, reject) => {
        if (!authorized) {
            reject('Unauthorized access to the user data');
        }

        resolve({
            id: id,
            username: 'admin'
        });
    });
}

try {
    getUserById(10)
        .then(user => console.log(user.username))
        .catch(err => console.log(`Caught by .catch ${err}`));
} catch (error) {
    console.log(`Caught by try/catch ${error}`);
}

```
</details>


## ☀️ ES6 collections:

<details>
<summary>set</summary>

```js
// Set usage to store uniq data:
let data = new Set();
data.add('apple');
data.add('orange');
data.add('banana');
data.delete('apple');
console.log(data.has('banana'));
//data.clear(); // all item will be clear/removed/deleted
console.log(data.size);
console.log(data.keys());
console.log(data.values());
console.log(data.entries());
data.forEach(item=>console.log(item));
console.log(data);


// array to set:
let my_arr = [1,2,3,4,5,2,3];
let nums = new Set(my_arr);
console.log(nums); //> 1,2,3,4,4

// set to array:
var n = [1,2,3,7,5,2];
let numbers = new Set(n);
var n = [...numbers];
console.log(n); //> [1,2,3,5,7]


// set union:
let a = new Set([1,2,3]);
let b = new Set([4,3,2]);
let union = new Set([...a,...b]);
console.log(union); //> 1,2,3,4


// intersaction:
var intersaction = new Set([...a].filter(item => b.has(item)));
console.log(intersaction);

```
</details>

<details>
<summary>map</summary>

```js
let fruits = new Map();
fruits.set('apple',400);
fruits.set('banana',300);
fruits.set('orange',100);
console.log(fruits.has('orange'));
fruits.delete('banana');
console.log(fruits.has('banana'));
fruits.forEach(fruit => console.log(fruit));
console.log(fruits.keys());
console.log(fruits.values());
console.log(fruits);
```
</details>

## ☀️ Array extensions:

<details>
<summary>Array of()</summary>

```js
let numbers = new Array(2);
console.log(numbers.length); // 2
console.log(numbers[0]); // undefined

let chars = Array.of('A', 'B', 'C');
console.log(chars.length); // 3
console.log(chars); // ['A','B','C']

```
</details>

<details>
<summary>Array.from()</summary>

```js
// Create an array from an array-like object:
function demo(){
  return Array.from(arguments);
}
var result = demo('apple','orange');
console.log(result);

// JavaScript Array Array.from() with a mapping function:
function demo2(){
  return Array.from(arguments,x => x+1);
}
var result = demo2(1,2,3);
console.log(result);

// JavaScript Array Array.from() with a this value:
let doubler = {
    factor: 2,
    double(x) {
        return x * this.factor;
    }
}
let scores = [5, 6, 7];
let newScores = Array.from(scores, doubler.double, doubler);
console.log(newScores);

```
</details>

<details>
<summary>Array.find()</summary>

```js
let nums = [1,2,3,3,5,8,98,1,3];
let r = nums.find(x => x/2 == 49);
console.log(r);
```
</details>

<details>
<summary>Array.findIndex()</summary>

```js
let nums = [1,2,3,3,5,8,98,1,3];
let r = nums.findIndex(x => x/2 == 49);
console.log(r);
```
</details>

## ☀️ Object extensions:

<details>
<summary>Object.assign()</summary>

```js
// Object.assign(target, ...sources)
// clone an object:
let widget = {
    color: 'red'
};

let demo = {
  name : 'color',
}
let clonedWidget = Object.assign(demo, widget);
console.log(clonedWidget);


// Using JavaScript Object.assign() to merge objects:
let para_style = {
  color : 'purple',
  border : '2px solid red',
  font_size : '1rem' //> the property of the later object overwrites this one!
};

let font_style = {
  font_size : '2rem',
  font_family : 'Serif',
  font_weight : 'bold'
};

let merged_object = Object.assign({},para_style,font_style);
console.log(merged_object);
```
</details>

<details>
<summary>Object.is()</summary>

#### Image:
![](https://www.javascripttutorial.net/wp-content/uploads/2020/01/JavaScript-sameness-comparison-table-768x935.png)

```js
console.log(Object.is(+0,-0));
```
</details>

## ☀️ String extensions:

<details>
<summary>View String New Method</summary>

```js
let str = 'Hello bangladesh!';
console.log(str.startsWith('H'));    //> true
console.log(str.endsWith('h'));      //> false
console.log(str.includes('Hello'));  //> true
console.log(str.includes('hello'));  //> false
```
</details>

## ☀️ Proxy & Reflection:

<details>
<summary>Proxy</summary>

</details>

<details>
<summary>Reflection</summary>

</details>