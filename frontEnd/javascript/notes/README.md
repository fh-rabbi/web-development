## 📚 List of content:
1. [Fundamentals](fundamental/README.md)
2. [Advanced](advanced/README.md)
3. [Dom](dom/README.md)
4. [Bom](bom/README.md)
5. [Es-6](es-6/README.md)
6. [Web Api & Ajax](api/README.md)
7. [Json](json/README.md)


# 🤔 How to ?
<details>
<summary>View Content</summary>

* [create back to top button]()

* [create sidebar navigation]()

</details>

## 😎 Tips and Tricks:
<details>
<summary>5 awesome tricks!</summary>

```js
// Remove duplicate from an array:
let data = [10,20,30,10,20,50,80,10,30];
let filtered_data = [...new Set(data)];
console.log(filtered_data);

// Turn a decimal number to an integer:
let myNum = 20.137;
myNum = myNum | 0;
console.log(myNum);

// Getting the last value of an array:
let fruits = ['apple','orange','grapes','banana'];
let last_fruit = fruits.slice(-1);
console.log(last_fruit.toString());

// Get a random index value from an array:
let persons = ['hurayra','abdullah','ibrahim','yousuf'];
let winner = persons[Math.floor(Math.random()*persons.length)];
console.log(winner);

// Detect the most lengthy word in an array:
let str = ['india','bangladesh','pakistan'];
let most_lengthy = '';
str.forEach(item=>{
  if(item.length > most_lengthy.length){
    most_lengthy = item;
  }
});
console.log(most_lengthy);

```

</details>
<!--<details>-->
<!--<summary></summary>-->

<!--</details>-->
