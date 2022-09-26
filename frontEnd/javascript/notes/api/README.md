# 🌎 Web Api:

### 🔐 Forms Api
<details>
<summary>View Content</summary>

```js
let btn = document.querySelector('#btn');
let input = document.querySelector('input');
let h1 = document.querySelector('h1');
btn.addEventListener("click", check);

if(input.validity.rangeOverflow){
  input.setCustomValidity("You have made a range error!");
}

function check() {
  if(!input.checkValidity()){
    h1.innerHTML = input.validationMessage;
  }
}


```
</details>

### 🔐 Storage Api:
<details>
<summary>View Content</summary>

```js
console.log(localStorage);
console.log(sessionStorage);

// set item as key value pair:
localStorage.setItem('userName','fazle rabbi');
let user_name = localStorage.getItem('userName');
console.log(user_name);

// set object in localStorage:
let data = {
  name : 'smith',
  age : 20,
  job : 'student'
};
// get object from localStorage:
localStorage.setItem('data',JSON.stringify(data));
let get_data = localStorage.getItem('data');
console.log(JSON.parse(get_data));
// localStorage.removeItem();
// localStorage.clear()
```
</details>

### 🔐 Worker Api:
<details>
<summary>View Content</summary>

```js
// ====================
// ====================
// main.js
let h1 = document.querySelector('h1');
let btn = document.querySelector('#btn');
let alert_btn = document.querySelector('#alr');
function start_worker(){
  if(Worker !== 'undefined'){
  w = new Worker('worker.js');
  w.onmessage = function (event){
    h1.innerHTML = event.data;
  };
}
else{
  alert('Your browser doesn\'t have worker api!');
}
}

btn.addEventListener("click", start_worker);
alert_btn.addEventListener("click", ()=>{
  alert('Hello');
});
// ====================
// ====================



// ====================
// ====================
// worker.js
let i = 0;
while(i < 100000000){
  i++;
}
postMessage(i);
// ====================
// ====================


```
</details>

### 🔐 Geolocation Api:
<details>
<summary>View Content</summary>

```js
let display = document.querySelector('h1');

// console.log(navigator);
if(navigator.geolocation){
  navigator.geolocation.getCurrentPosition(showPosition,showError);
}
else{
  alert('Your browser doesn\'t support geoLocation api');
}

function showPosition(position){
  display.innerHTML = `Latitude: ${position.coords.latitude} 
  Longitude: ${position.coords.longitude}
  `;
  console.log(position.coords.accuracy);
}

function showError(error) {
  switch (error.code) {
    case error.PERMISSION_DENIED:
      display.innerHTML = "User denied the request for Geolocation."
      break;
    case error.POSITION_UNAVAILABLE:
      display.innerHTML = "Location information is unavailable."
      break;
    case error.TIMEOUT:
      display.innerHTML = "The request to get user location timed out."
      break;
    case error.UNKNOWN_ERROR:
      display.innerHTML = "An unknown error occurred."
      break;
  }
}

```
</details>

---


# 📬 Ajax:

#### `AJAX is a developer's dream, because you can:`

> * Read data from a web server - after the page has loaded
> * Update a web page without reloading the page
> * Send data to a web server - in the background
> * AJAX is not a programming language.
> * AJAX is a technique for accessing web servers from a web page.
> * AJAX stands for Asynchronous JavaScript And XML.


🚦 **4 way to call api in javascript:**

1. ```XML Http Request```
2. ```Fetch```
2. ```Axios```
2. ```Jquery```

## 📍 Request methods:
1. GET
2. POST
3. PUT
4. PATCH
5. DELETE

## 📥 XML Http Request:
<details>
<summary>View Content</summary>

```js
// Xml Http Request:
const makeRequest = (method,url,data)=>{
  const xhr = new XMLHttpRequest();
  xhr.open(method,url);
  xhr.setRequestHeader('Content-Type','application/json');
  xhr.onload=()=>{
    let x = xhr.response;
    console.log(x);
  };
  xhr.onerror=()=>{
    console.log('Something webt wrong...!');
  };
  xhr.send(JSON.stringify(data));
};

const getData = () => {
  makeRequest('GET','https://jsonplaceholder.typicode.com/posts/1');
};
getData();

const send_data = () => {
  makeRequest('POST','https://jsonplaceholder.typicode.com/posts',{
    name : 'smith',
    age : 20,
    city : 'Us'
  });
};
send_data();


// =====================
// =====================
// Another way:
let xhr = new XMLHttpRequest();
xhr.open('GET','https://jsonplaceholder.typicode.com/posts/1');
xhr.setRequestHeader('Content-Type','application/json');
xhr.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      console.log(this.responseText);
    }
  };
xhr.send();


```
</details>

## 📥 Fetch:
<details>
<summary>View Content</summary>

```js
// Getting data:
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then((response) => response.json())
  .then((json) => console.log(json));

// Posting or send data:
fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  body: JSON.stringify({
    title: 'foo',
    body: 'bar',
    userId: 1,
  }),
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
})
  .then((response) => response.json())
  .then((json) => console.log(json));

```
</details>

## 📥 Axios:
<details>
<summary>View Content</summary>

```js
// Getting data:
axios.get('https://jsonplaceholder.typicode.com/posts/1')
.then(res=>{
  console.log(res);
  console.log(res.data);
})
.catch(err=>console.log(err));

// Posting data:
axios.post('https://jsonplaceholder.typicode.com/posts',{
  name : 'smith',
  age : 20
})
.then(res=>{
  console.log(res);
  console.log(res.data);
})
.catch(err=>console.log(err));

// with async and await:
const makeRequest = async(config) => {
  let res = await axios(config);
  res = res.data;
  return res;
};

const getData = () => {
  makeRequest('https://jsonplaceholder.typicode.com/posts/1')
  .then(res=>console.log(res))
  .catch(err=>console.log(err));
};
getData();
```
</details>

## 📥 Jquery Ajax:
<details>
<summary>View Content</summary>

```js
// Normal way:
$.ajax({
  url : 'https://jsonplaceholder.typicode.com/posts/1',
  method : 'GET'
})
.then(res=>console.log(res))
.catch(err=>console.log(err));

{
  // With function:
  const makeRequest = (url,method,data) => {
  $.ajax(url,method,data)
  .then(res=>{
    console.log(res);
    return res;
  })
  .catch(err=>console.log(err));
  };
  
  const getData = () => {
    makeRequest('https://jsonplaceholder.typicode.com/posts/1','GET');
  };
  getData();
}

// With async and await:
const makeRequest = async(url,method,data) => {
  let result = await $.ajax({
    url : url,
    method : method,
    data : data
  });
  return result;
};

const sendData = () => {
  makeRequest('https://jsonplaceholder.typicode.com/posts','POST',{
    name : 'smith'
  })
  .then(res=>console.log(res))
};
sendData();
```
</details>

## 🗑️ Cookie:
<details>
<summary>View Content</summary>

```js
document.cookie ='user=rabbi;expires=Sun, 04 Jun 2022 16:42:00 GMT';
console.log(document.cookie);
```
</details>
