<!--Fundamental-->
### Javascript Fundamentals:

---

|Column1|Column2|
|---|---|
|Variables|Operators|
|Condition|Loop|
|Array|Function|
|Objects|Data types|

---

## ⚡  Variables:
<details>
<summary>View Content</summary>

```js
var a = 10;
let b = 20;
const c = 30;
```
</details>

## ⚡  Data types:
<details>
<summary>View Content</summary>

```js
number
string
bolean
null
undefined
array
object
```
</details>

## ⚡  Operators:
<details>
<summary>View Content</summary>

```
1.Arithmetick
2.Asignment
3.Comparision/Relational
4.Logical
5.Ternary
6.Bitwise
```
</details>

## ⚡  String methods:
<details>
<summary>View Content</summary>

```js
length,toUpperCase();
toLowerCase();includes();
startsWith();endsWith();
search();match();
indexOf();lastIndexOf();
replace();charAt();
charCodeAt();fromCharCode()
```
</details>

## ⚡ Numbers:
<details>
<summary>View Contents</summary>

* Extra large or extra small numbers can be written with scientific (exponent) notation:

```js
let x = 123e5;    // 12300000
let y = 123e-5;   // 0.00123

```

* Integers (numbers without a period or exponent notation) are accurate up to 15 digits:
```js
let x = 999999999999999;   // x will be 999999999999999
let y = 9999999999999999;  // y will be 10000000000000000
```

* Floating point arithmetic is not always 100% accurate:

```js
let x = 0.2 + 0.1;

// To solve the problem above:
let x = (0.2 * 10 + 0.1 * 10) / 10;

```

* Adding Numbers and Strings:

```js
// add two numbers:
let x = 10;
let y = 20;
let z = x + y; // z = 30

// add two strings:
let x = "10";
let y = "20";
let z = x + y; // 1020

// add a number and a string:
let x = 10;
let y = "20";
let z = x + y; // 1020

// add a string and a number:
let x = "10";
let y = 20;
let z = x + y; // 1020

// ???
let x = 10;
let y = 20;
let z = "The result is: " + x + y; // 1020

// ???
let x = 10;
let y = 20;
let z = "30";
let result = x + y + z; // = (10+20)+"30" = 3030

```

* Numeric Strings:

`JavaScript strings can have numeric content:`

```js
let x = 100;         // x is a number
let y = "100";       // y is a string

let x = "100";
let y = "10";
let z = x / y; // 10

let x = "100";
let y = "10";
let z = x * y;

let x = "100";
let y = "10";
let z = x - y;

```

* NaN - Not a Number:
   * `NaN is a JavaScript reserved word indicating that a number is not a legal number.`

```js
let x = 100 / "Apple"; // NaN
let x = 100 / "10"; // 10

// You can use the global JavaScript function isNaN() to find out if a value is a not a number:
let x = 100 / "Apple";
isNaN(x); // x kuno number noy? >> true

// Hexadecimal is base 16. Decimal is base 10. Octal is base 8. Binary is base 2:
let myNumber = 32;
myNumber.toString(32);
myNumber.toString(16);
myNumber.toString(12);
myNumber.toString(10);
myNumber.toString(8);
myNumber.toString(2);

```
</details>

## ⚡ Number methods:
<details>
<summary>View Content</summary>

```js
Number()
parseInt()
parseFloat()
toFixed()
toPrecision()
isFinite()
isInteger()
```
</details>

## ⚡  Math methods:
<details>
<summary>View Content</summary>

```js
Math.abs();Math.sqrt();
Math.cbrt();Math.pow();
Math.sin();Math.cos();
Math.min();Math.max();
Math.random();Math.round();
Math.trunc();Math.floor();
Math.ceil();
```
</details>

## ⚡ Functions:
<details>
<summary>View Content</summary>

```js
function sum(x,y){
 console.log(x+y); 
}
sum(10,40);

// Function expression:
var msg = function(a){
  console.log('Hello '+a);
};
msg('karim');

```
</details>

## ⚡  Condition:

<details>
<summary>View Content</summary>

```js
if (10 > 5) {
  //...
}
else if(10 == 5){
  //...
}
else{
  //...
}

switch (expression) {
  case 'case':
    // code
    break;
  
  default:
    // code
}
```
</details>

## ⚡  Loop:

<details>
<summary>View Content</summary>

```js
// for loop:
for(x = 0;x < 10;x++){
  console.log(x);
}

// while loop:
var a = 0;
while(a < 10){
  console.log('Hello user!');
  a++;
}

// do while loop:
var a = 0;
do{
  console.log('Hello guys!');
  a++;
}while(a < 10);
```
</details>

## ⚡  Array:

<details>
<summary>View Content</summary>

```js
let fruits = ['apple','orange'];
console.log(fruits)
```
#### Array methods:
![Screenshot_20220530-112607](https://user-images.githubusercontent.com/71178740/172522666-77cf08c6-1d6b-436d-a08f-75362851030e.png)

</details>

## ⚡  Array sorting:

<details>
<summary>View Content</summary>

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();


const points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a - b});


// Find the Highest (or Lowest) Array Value:
const points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a - b});
// now points[0] contains the lowest value
// and points[points.length-1] contains the highest value


// Using Math.max() on an Array:
let arr = [1,209,30,39,29,99];
function myArrayMax(arr) {
  
  return Math.max.apply(null,arr);
}
console.log(myArrayMax(arr));

```
</details>

## ⚡  Object:
```js
let data = {
  name : 'smith'
};
```

## ⚡ Date object:

<details>
<summary>Basic Dates</summary>

>  Creating Date Objects:
> `There are 4 ways to create a new date object:`
```js
new Date()
new Date(year, month, day, hours, minutes, seconds, milliseconds)
new Date(milliseconds)
new Date(date string)
```

* How to use date object:

```js
// Specifying a month higher than 11, will not result in an error but add the overflow to the next year:
var d = new Date(2018, 15, 24, 10, 33, 30);

// Specifying a day higher than max, will not result in an error but add the overflow to the next month:
var d = new Date(2018, 5, 35, 10, 33, 30);
document.querySelector('h1').innerHTML = d;


// Using 6, 4, 3, or 2 Numbers
// 6 numbers specify year, month, day, hour, minute, second:
var d = new Date(2018, 11, 24, 10, 33, 30);
var d = new Date(2018); // iit will be treated as milliseconds.


// new Date(dateString):
var d = new Date("October 13, 2014 11:13:00");
console.log(d);


// toString():
var d = new Date();
console.log(d.toString());

// toUTCString():
var d = new Date();
console.log(d.toUTCString());

// toDateString():
var d = new Date();
console.log(d.toDateString());
```

</details>

<details>
<summary>Dates Formats</summary>

```js
const d = new Date("2015-03-25");

const d = new Date("2015-03");

const d = new Date("2015");

const d = new Date("2015-03-25T12:00:00Z");

// JavaScript Short Dates:
const d = new Date("03/25/2015");

// JavaScript Long Dates:
const d = new Date("Mar 25 2015");

// Month and day can be in any order:
const d = new Date("25 Mar 2015");

//And, month can be written in full (January), or abbreviated (Jan):
const d = new Date("January 25 2015");
const d = new Date("Jan 25 2015");

// Commas are ignored. Names are case insensitive:
const d = new Date("JANUARY, 25, 2015");

// convert date to milliseconds amd milliseconds to date:
let msec = Date.parse("March 21, 2012");
const d = new Date(msec);

```
</details>

<details>
<summary>Date Get methodss</summary>

![Screenshot_20220611-094434](https://user-images.githubusercontent.com/71178740/173171277-cda7cb76-0155-4509-95ee-9824d5efbc47.png)

#### Getting Months:

```js
const months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
const d = new Date();
console.log(months[d.getMonth()]);
```

#### Getting Days:

```js
const days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
const d = new Date();
let day = days[d.getDay()];
```

</details>

<details>
<summary>Date Set methodss</summary>

![Screenshot_20220611-095058](https://user-images.githubusercontent.com/71178740/173171417-88b6ae33-d744-4356-98cb-11aee6c4140a.png)

```js
// The setFullYear() methods:
const d = new Date();
d.setFullYear(2020);
// The setFullYear() methods can optionally set month and day:
const d = new Date();
d.setFullYear(2020, 11, 3);


// The setMonth() methods:
const d = new Date();
d.setMonth(11);


// The setDate() methods:
const d = new Date();
d.setDate(15);
// The setDate() methods can also be used to add days to a date:
const d = new Date();
d.setDate(d.getDate() + 50);


// The setHours() methods:
const d = new Date();
d.setHours(22);


// The setMinutes() methods:
const d = new Date();
d.setMinutes(30);


// The setSeconds() methods:
const d = new Date();
d.setSeconds(30);

```

</details>

## ⚡  Typeof Operator:

<details>
<summary>View Content</summary>

```js
typeof "John"                 // Returns "string"
typeof 3.14                   // Returns "number"
typeof NaN                    // Returns "number"
typeof false                  // Returns "boolean"
typeof [1,2,3,4]              // Returns "object"
typeof {name:'John', age:34}  // Returns "object"
typeof new Date()             // Returns "object"
typeof function () {}         // Returns "function"
typeof myCar                  // Returns "undefined" *
typeof null                   // Returns "object"
```    
</details>

## ⚡  Type Conversion:

<details>
<summary>View Content</summary>

1. *Converting Strings to Numbers*

```js
Number("3.14")    // returns 3.14
Number(" ")       // returns 0
Number("")        // returns 0
Number("99 88")   // returns NaN

// The Unary + Operator:
let y = "5";      // y is a string
let x = + y;      // x is a number
```
2. *Converting Numbers to Strings*

```js
String(x)         // returns a string from a number variable x
String(123)       // returns a string from a number literal 123
String(100 + 23)  // returns a string from a number from an expression

// Or:
x.toString()
(123).toString()
(100 + 23).toString()
```
3. *Converting Dates to Numbers*

```js
d = new Date();
Number(d)          // returns 1404568027739
// The date methods getTime() does the same:
d = new Date();
d.getTime()        // returns 1404568027739
```
4. *Converting Numbers to Dates*

```js
String(Date())  // returns "Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)"
// Or:
Date().toString()  // returns "Thu Jul 17 2014 15:38:19 GMT+0200 (W. Europe Daylight Time)"
```
5. *Converting Booleans to Numbers*

```js
Number(false)     // returns 0
Number(true)      // returns 1
```

6. *Converting Booleans to Strings*

```js
String(false)      // returns "false"
String(true)       // returns "true"

// Or:
false.toString()   // returns "false"
true.toString()    // returns "true"
```
</details>

## ⚡  Bitwise Operator:

<details>
<summary>View Content</summary>

</details>

## ⚡  RegExp:

<details>
<summary>View Content</summary>

> `In JavaScript, regular expressions are often used with the two string methodss: search() and replace()`

---
#### Regular Expression Modifiers:

|name|description|
|--------|-------|
|i|`Perform case-insensitive matching`|
|g|`Perform a global match (find all matches rather than stopping after the first match)`|
|m|`Perform multiline matching`|
---
* **Use a regular expression to do a case-insensitive search for "w3schools" in a string:**

```js
// i() case-insensitive search:
let text = "Visit W3Schools";
let n = text.search(/w3schools/i);
```

* **Use a case insensitive regular expression to replace Microsoft with W3Schools in a string:**
```js
let text = "Visit Microsoft!";
let result = text.replace(/microsoft/i, "W3Schools");
// output:Visit W3Schools!
```

</details>

## ⚡  Logical Operator:

<details>
<summary>View Content</summary>

```js
let a = 10;
let b = null;
console.log(a || b);

let x = 10;
let y = 10;
let check = x == y && x > 0 ? 'true' : 'false';
console.log(check);
```
</details>

## ⚡  Ternary Operator:

<details>
<summary>View Content</summary>

```js
let age = 18;
let isAdult = age >= 18 ? 'Adult' : 'Child';
console.log(isAdult);
```
</details>

## ⚡  Error Handling:
<details>
<summary>View Content</summary>

```js
try {
  
} catch (e) {
  
}finally{
  
}
```
</details>

## ⚡  Symbol:

<details>
<summary>View Content</summary>

</details>

## ⚡  Iterator and Generator:

<details>
<summary>View Content</summary>

</details>