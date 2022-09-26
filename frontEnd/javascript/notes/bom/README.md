# JavaScript BOM:

# 🎯 Window:

**1. window size:**
```js
window.innerHeight
window.inerWidth
window.outerHeight
window.outerWidth
```

**2. window resize:**

```js
window.resizeBy()
window.resizeTo()
```
**3. window move:**
```js
window.moveBy()
window.moveTo()
```
**4. window opener**

**5. window console:**
```js
// OBJECTS:
console.log()
console.clear()

console.assert()
// USAGES:(this method method writes a message to the console if an expression evaluates to false.)
let x = 5;
let y = 5;
const myArr = ["Orange", "Banana", "Mango", "Kiwi" ];
console.assert(x + y == 11, myArr);

console.count()
// USAGES:(The count() method counts the number of times console.count() is called.)
console.count('Hello')

console.error()
// USAGES:(The error() method writes an error message to the console.)
const myArr = ["Orange", "Banana", "Mango", "Kiwi"];
console.error(myArr);

console.group() // The group() method starts a message group.
console.groupCollapsed() // The groupCollapsed() method starts a collapsed message group.
console.groupEnd() // The groupEnd() ends a message group.
console.info() // The info() method writes a message to the console.

console.table() // The table() method writes a table to the console.
// USAGES:
const car1 = {name:"Audi", model:"A4"}
const car2 = {name:"Volvo", model:"XC90"}
const car3 = {name:"Ford", model:"Fusion"}
console.table([car1, car2, car3], ["model"]);

console.time()
console.timeEnd()
console.trace()
console.warn() // The warn() method writes a warning to the console.

```

**6. OTHERS:**
```js
window.open()
window.close()
window.closed()
// USAGES:
const open_window = document.querySelector('#open');
const close_window = document.querySelector('#close');
const check = document.querySelector('#check');
const para = document.querySelector('#text');

let myWindow;
open_window.addEventListener("click", ()=>{
  myWindow = window.open('https://guthib.com');
});

close_window.addEventListener("click", ()=>{
  myWindow.close();
});

console.log(myWindow);

check.addEventListener("click", ()=>{
  if(!myWindow){
    para.innerHTML = 'Window has never been opened!...!';
  }else{
     if(myWindow.closed){
       para.innerHTML='Window closed';
     }
     else{
       para.innerHTML='Window opened';
     }
  }
});


window.scrollX(0,0)
window.scrollY(0,0)
window.scrollBy(0,10px)
window.scrollTo(0,0)
window.stop()
window.screenTop
window.self
window.atob()

```

# 🎯 Screen:
```js
screen.availHeight
screen.availWidth
screen.height
screen.width
screen.availTop
screen.avaiLeft
screen.colorDepth
screen.pixelDepth
screen.orientation

```

# 🎯 Location:

**For redirect to an url:**
```js
location.href = 'https://example.com'; 
location.assign('https://example.com'); 
location.replace('https://example.com');
``` 

```js
location
location.href
location.origin
location.protocol
location.host
location.hostname
location.port
location.pathname
location.search
location.hash
location.assign:(){...}
location.reload:(){...}
location.replace:(){...}
location.toString:(){...}
location.valueOf:(){...}
```

# 🎯 History:
```js
history.length:...
history.scrollRestoration:...
history.state:...
history.back:(){...}
history.forward:(){...}
history.go:(){...}
history.pushState:(){...}
history.replaceState:(){..
```

# 🎯 Navigator:
```js
navigator.appName
appCodeName
navigator.appVersion
cookieEnabled
geolocation
navigator.platform
navigator.product
navigator.userAgent
navigator.language
navigator.languages
navigator.onLine
javaEnabled()

```

# 🎯 Popup alert:
```js
alert()
prompt()
confirm()
```

# 🎯 Timing Event:
```js
setTimeout(()=>{
  
}, 1000);

setImterval(()=>{
  
},1000);

clearTimeout()
clearInterval()

```



