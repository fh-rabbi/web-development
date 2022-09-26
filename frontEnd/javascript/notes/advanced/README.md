# 🚀 Advanced js:

1. **Js Objects:**

   * `Properties`
   * `Method`
   * `Accessors`
   * `Constructors`
   * `Prototypes`
   * `Iterables`
   * `Set`
   * `Map`

2. **Js Functions:**

   * `Call`
   * `Apply`
   * `Bind`
   * `Closures`

3. **Js classes:**

   * `Syntax`
   * `Inheritence`
   * `Static Method`

4. **Js Async:**

   * `Asynchronous`
   * `Callbacks`
   * `Promises`
   * `Async/Await`

## ✴️ Objects:

<details>
<summary>View Content</summary>

```js
// Properties:
let data = {
  name : 'smith',
  age : 20,
};
console.log(data.name);

// Methods:
let data2 = {
  name : 'david',
  age : 22,
  dob : function (){
    console.log(`${this.name} was born in ${2022-this.age}`);
  }
};
data2.dob();

// Object constructor:
function Data(name,age){
  this.name = name;
  this.age = age;
}
let person1 = new Data('smith',20);
console.log(person1);

// inheritance:
function Data2(name,age,job){
  Data.call(this,name,age);
  this.job = job;
}
let person2 = new Data2('david',21,'Student');
console.log(person2);

// Prototype:
function Info(name){
  this.name = name;
}
Info.prototype.age = 20;
let p1 = new Info('john');
console.log(p1);

// Iterable:
let test = {
  name : 'smith',
  age : 20,
  city : 'Us',
  gpa : 4.88,
};
for(let x in test){
  console.log(`${x} : ${test[x]}`);
}

// Set:
let fruits = new Set();
fruits.add('apple');
fruits.add('orange');
fruits.delete('orange');
console.log(fruits.has('apple'));
fruits.clear();

// convert array to set:
let numbers = [1,2,3,4,9,2,1,4];
console.log(`Array = ${numbers}`);
let nums_set = new Set(numbers);
console.log(nums_set);
console.log(nums_set.size);

// Set to array:
let my_arr = [...nums_set];
console.log(my_arr);

// Map:
let my_map = new Map();
my_map.set('apple',500);
my_map.set('banana',300);
console.log(my_map.get('apple'));
console.log(my_map);

```
</details>



## ✴️ This keyword:

<details>

<summary>View Content</summary>

1.Global Rules

2.Object Rules

3.This keyword Rules

4.Clear Rules (call,bind,apply)

```js
// globaly this means window object
console.log(this);

// inside a function this means window object
function (){
  console.log(this);
}

// inside an object this means this object
let data = {
  name : 'smith',
  age : 20,
  msg : function(){
    console.log(this);
  }
}

// inside dom event this means selected element
btn.addEventListener("click", (e)=>{
  console.log(e);
});
```
</details>

## ✴️ Functions:
<details>
<summary>View Content</summary>

```js
let demo1 = {
  name : 'smith',
  display1 : function(a,b,c){
        console.log(this);
        console.log(a+b+c);
      },
  demo2 : {
    display2 : function(a,b,c){
        console.log(this);
        console.log(a+b+c);
      },
    name : 'david',
    demo3 : {
      name : 'john',
      display3 : function(a,b,c){
        console.log(this);
        console.log(a+b+c);
      },
    }
  }
};
// this means demo3 object
demo1.demo2.demo3.display3(5,5,5);
// call method:
demo1.demo2.demo3.display3.call(demo1.demo2,5,5,5);
// apply method:
demo1.demo2.demo3.display3.apply(demo1.demo2,[5,5,5]);
// bind method:
let x = demo1.demo2.demo3.display3.bind(demo1.demo2,5,5,5);
x();

// Closures:
function parent(a){
  console.log('Im the parent!');
  var x = 10;
  return function (){
    console.log(x+a);
  };
}
parent(40)();
```
</details>

## ✴️ Classes:
<details>
<summary>View Content</summary>

```js
// Classes:
class demo1 {
  constructor(name,age){
    this.name = name;
    this.age = age;
  }
}
// prototype based inheritance:
demo1.prototype.dob = function (){
  console.log(`${this.name} was born in ${2022-this.age}`);
};
let person1 = new demo1('smith',20);
console.log(person1);
person1.dob();

// class inheritance:
class demo2 extends demo1 {
  constructor(name,age,job){
    super(name,age);
    this.job = job;
  }
}
let person2 = new demo2('david',22,'STUDENT');
console.log(person2);

// class static method:
class info {
  constructor(name,age){
    this.name = name;
    this.age = age;
  }
  static demo(){
    console.log('Im just a demo');
  }
}
let person3 = new info('john',20);
console.log(person3);
//person3.demo(); //NOT WORK IN static METHOD!
info.demo(); // only it's work in static method...

```
</details>

## ✴️ Async:

<details>
<summary>View Content</summary>

```js
// Async:
// Asynchronous:
{
const task1 = () => {
  console.log('Im task one');
};

const task2 = () => {
  setTimeout(function() {
    console.log('Im task two');
  }, 1000);
};

const task3 = () => {
  console.log('Im task three');
};
task1();
task2();
task3();
}


// Callbacks:
{
  // Simple example:
  let x = 10;
  const y = () => {
    console.log('Im function Y !');
  };
  
  const sum = (a,b,callback)=>{
    console.log(a*b);
    callback();
  };
  sum(x,10,y);
  
  // Another example:
  const task1 = (callback) => {
  console.log('Im task one');
  callback();
};

const task2 = (callback) => {
  setTimeout(function() {
    console.log('Im task two');
    callback();
  }, 1000);
};

const task3 = () => {
  console.log('Im task three');
};
task1(()=>{
  task2(()=>{
    task3();
  });
});
}


// Promise:
{
  const task1 = () => {
    return new Promise((resolve,reject)=>{
      resolve('Im resolved from taskONE')
    });
  };
  
  const task2 = () => {
    return new Promise((resolve,reject)=>{
      setTimeout(function() {
        resolve('Im resolved from task TWO')
      }, 1000);
    });
  };
  
  const task3 = () => {
    return new Promise((resolve,reject)=>{
      resolve('Im resolved from task THREE')
    });
  };
  
  task1()
  .then(res=>console.log(res))
  .then(task2)
  .then(res=>console.log(res))
  .then(task3)
  .then(res=>console.log(res))
  .catch(err=>console.log(err));
}


// async await:
{
  const task1 = () => {
    return new Promise((resolve,reject)=>{
      resolve('task1 resolved')
    });
  };
  
  const task2 = () => {
    return new Promise((resolve,reject)=>{
      resolve('task2 resolved')
    });
  };
  
  const all_task = async() => {
    const t1 = await task1();
    console.log(t1);
    const t2 = await task2();
    console.log(t2);
  };
  all_task();
}

```
</details>
