# Storage Api:

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

## Cookie:
```js
document.cookie ='user=rabbi;expires=Sun, 04 Jun 2022 16:42:00 GMT';
console.log(document.cookie);
```