# Js DOM:

1. Selecting elements:

   * ```getElementById()```
   * ```getElementsByClassName()```
   * ```getElementsByTagName()```
   * ```getElementsByName()```
   * ```querySelector()```
   * ```querySelectorAll()```

2. Traversing elements:

   * ```Get the parent element```
   * ```Get child elements```
   * ```Get siblings of an element```

3. Manipulating elements:

   * ```createElement()```
   * ```appendChild()```
   * ```replaceChild()```
   * ```removeChild()```
   * ```textContent```
   * ```innerHTML```
   * ```innerHTML vs. createElement```
   * ```DocumentFragment```
   * ```insertBefore()```
   * ```insertAfter() helper function```
   * ```append()```
   * ```prepend()```
   * ```insertAdjacentHTML()```
   * ```cloneNode()```
   * ```hasChildNodes and has isEqualNode```
   * ```Create Element With Template Literal```

4. Working with Attributes:

   * ```setAttribute()```
   * ```getAttribute()```
   * ```removeAttribute()```
   * ```hasAttribute()```

5. Manipulating Element’s Styles:

   * ```style property```
   * ```cssText property```
   * ```getComputedStyle()```
   * ```className property```
   * ```classList property```
   * ```Element’s width & height```

6. Working with Events:

   * ```JavaScript events```
   * ```Handling events```
   * ```Page Load Events```
   * ```Mouse events```
   * ```Keyboard events```
   * ```Focus Events```
   * ```Clipboard Events```
   * ```Media Events```
   * ```Drag and Drop Events```
   * ```Scroll events```
   * ```scrollIntoView```
   * ```haschange event```
   * ```Event Delegation```
   * ```dispatchEvent```
   * ```Custom Events```
   * ```MutationObserver```


7. Scripting Web Forms:

## 🚦 Selecting elements:

<details>
<summary>View Content</summary>

```Js
const a = document.getElementById('btn');
const b = document.getElementsByClassName('box')[0];
const c = document.getElementsByTagName('div')[0];
const d = document.getElementsName('languages');
const e = document.querySelector('.para');
const f = document.querySelectorAll('p')[0];

// classname,tagname,querySelectorAll always return a nodelist:
// convert nodelist into array:
const divElement = document.querySelectorAll('div');
Array.from(divElement).map(element=>{
  //...
});
```
</details>


## 🚦 Traversing elements:

<details>
<summary>View Content</summary>

```Js

// select parent:
var ol = document.querySelector('ol');
// select child using parent:
var studentA = ol.querySelector('student-A'); 

// Getting parent element:
const li = document.querySelector('list1');
const parent = li.parentNode;
const parent = li.parentElement;

// Getting Children:
// Get the first child element:
let firstChild = parentElement.firstChild;
let firstElementChild = parentElement.firstElementChild;

// Get the last child element:
let lastChild = parentElement.lastChild;
let lastElementChild = parentElement.lastElementChild;

// Get all child elements:
let children = parentElement.childNodes;
let children = parentElement.children;

// get a specific child element:
var studentC = ol.children[2];

// Get siblings of an element
var studentB = studentA.nextElementSibling;
var studentB = studentC.previousElementSibling;
```
</details>


## 🚦 Manipulating elements:

<details>
<summary>View Content</summary>

```Js
// Create element:
const new_element = document.createElement('h1');
// Create text node:
const new_text = document.createTextNode('Hello im a heading 1');
// Append child:
new_element.appendChild(new_text);

// replace child:
const ol = document.querySelector('ol');
const li_1 = ol.children[0];
const new_list = document.createElement('li');
ol.replaceChild(new_list,li_1);

// Remove child:
const div_element = document.querySelector('div');
const h1 = div_element.child[1];
div.removeChild(h1);

// text content and innerHTML:
let para1 = document.querySelector('#para1');
para1.textContent = 'Text changed';
para1.innerHTML = 'Text also changed';

// ** innerHTML vs. createElement: **
// createElement is more performant...
// createElement is more secure...
let div = document.querySelector('.container');

let p = document.createElement('p');
p.textContent = 'JS DOM';
div.appendChild(p);

let div = document.querySelector('.container');
div.innerHTML += '<p class="note">JS DOM</p>';
/*
However, using the innerHTML causes the web browsers to reparse and recreate all DOM nodes inside the div element. Therefore, it is less efficient than creating a new element and appending to the div. In other words, creating a new element and appending it to the DOM tree provides better performance than the innerHTML.
*/

// DocumentFragment:
/*
Use the DocumentFragment to compose DOM nodes before updating them to the active DOM tree to get better performance
*/
let languages = ['JS', 'TypeScript', 'Elm', 'Dart','Scala'];

let langEl = document.querySelector('#language');

let fragment = new DocumentFragment();
languages.forEach((language) => {
    let li = document.createElement('li');
    li.innerHTML = language;
    fragment.appendChild(li);
});

langEl.appendChild(fragment);

// insertBefore():
const box_div = document.querySelector('.box');
const heading1 = document.querySelector('h1');
const heading2 = document.createElement('h2');
heading2.innerHTML = 'im a heading2';
box_div.insertBefore(heading2,heading1);

// insertAfter():
/*
not available this function
but, we can make this with logic!
*/

// append() and prepand():
let paragraph = document.querySelector('p');
p.append(' Hello');
p.prepend('Hi ');

// insertAdjacentHTML:
const list = document.querySelector('#list');
list.insertAdjacentHTML('beforebegin','<h1>Heading 1</h1>');
list.insertAdjacentHTML('afterbegin','<h2>Heading 2</h2>')
list.insertAdjacentHTML('beforeend','<h3>Heading 3</h3>')
list.insertAdjacentHTML('afterend','<h4>Heading 4</h4>')

// cloneNode:
let li = document.querySelector('li_1');
let cloned_node = li.cloneNode();
console.log(li);

// hasChildNodes and has isEqualNode:
const div1 = document.querySelector('.div1');
const div2 = document.querySelector('.div2');
let has_childs = div1.hasChildNodes();
console.log(has_childs);
let is_equal = div1.isEqualNode(div2);
console.log(is_equal);

// Create element with template literal:
const div = document.createElement('div');
div.innerHTML = `
   <div class="box">
   <h1 class="text">Hello</h1>
   </div>
 `;

```

</details>


## 🚦 Working With Attributes:

<details>
<summary>View Content</summary>

```js
// Working with Attributes:
const div = document.querySelector('div');
div.setAttribute('class','new_class'); // for set a new attribute
div.getAttribute('class'); // return class Attribut value
div.removeAttribute('id'); // id will be removed
div.hasAttribute('class'); //> [true] if class include in (div)
```

</details>



## 🚦 Manipulating Elements Styles:

<details>
<summary>View Content</summary>

```Js
// Style property:

let h1 = document.querySelector('h1');
h1.style.color = 'red';

//for override inline style:
h1.style.cssText = 'color:black;background-color:yellow';

// also for override inline style:
h1.setAttribute('style','color:orange;background-color:black')

// for concatenate inline style with new style:
h1.style.cssText += 'font-family:serif;';


// cssText property:

let ul = document.querySelector('ul');
ul.children[1].style.cssText = `
  color:purple;
  font-weight:bold;
  font-size:2rem;
  margin-left:10px;
  list-style-type:none;
`;

  
// Get Computed Style:

// Simple getComputedStyle() example:
let h1 = document.querySelector('h1');
let style = getComputedStyle(h1);
console.log(style.color,style.background);
  
// The getComputedStyle() for pseudo-elements example:
const p = document.querySelector('p');
let style2 = getComputedStyle(p,'::first-letter');
console.log(style2.color);


// className property:

let menu = document.querySelector('.menu');
// for override existing class:
menu.className = ' text-info';
// for add new class with existing className:
menu.className += ' text-danger';
// To get a complete list of classes of an element:
console.log(menu.className);
  

// classList property:

let h1 = document.querySelector('h1');
// Getting classList from an element:
let r = h1.classList;
for(classes of r){
  console.log(classes);
};
  
// Class add(),remove(),replace(),contains() & toggle():

const div = document.querySelector('div');
div.classList.add('text-primary','bg-dark');
div.classList.remove('demo');
div.classList.replace('bg-dark','bg-info');
let hasClass = div.classList.contains('bg-info');
// toggle helpful when we create menu,popupBox etc:
div.classList.toggle('toggle-class');
console.log(hasClass);
// view all class name:
console.log(div.classList);


// Elements width and height:

let demo = document.querySelector('.demo');
  
// with border:
let off_width = demo.offsetWidth;
let off_height = demo.offsetHeight;
console.log(off_height,off_width);
  
// without border:
let cl_width = demo.clientWidth;
let cl_height = demo.clientHeight;
console.log(cl_height,cl_width);

```
![offset width and height](https://www.javascripttutorial.net/wp-content/uploads/2020/02/JavaScript-offsetWidth-and-offsetHeight.png)
![client width and height](https://www.javascripttutorial.net/wp-content/uploads/2020/02/JavaScript-clientWidth-and-clientHeight-png.png)


</details>


## 🚦 Working with Events :

<details>
<summary>View Content</summary>

```Js
// Handling Event:
let btn = document.querySelector('#btn');

// The addEventListener() method
btn.addEventListener('click', function(event) {
    console.log(event);
});

// The removeEventListener() method:
let showAlert = function() {
    alert('Clicked!');
};
btn.addEventListener('click', showAlert);

// remove the event listener
btn.removeEventListener('click', showAlert);

```

#### 🎯 Properties and methods of the event object:
|Property / Method|Description|
|-----------------|-----------------|
|detail|more information about the event|
|type|the type of event that was fired|
|target|the target element of the event|
|preventDefault()|cancel the default behavior for the event. This method is only effective if the cancelable property is true|


### 💡 Page Load Events:

<details>
<summary>View Content</summary>

1. ***DOMContentLoaded***  ```only fully loaded HTML ```*Only handle DOMContentLoaded event if you place the JavaScript code in the head, which references elements in the body section.*
2. ***load***  ```fully loaded the HTML and also external resources like images and stylesheets```

   ```js
   window.addEventListener('load' () => {
    let logo = document.createElement('img');
    // assign and onload event handler
    logo.addEventListener('load', (event) => {
        console.log('The logo has been loaded');
    });
    // add logo to the document
    document.body.appendChild(logo);
    logo.src = 'logo.png';
   });
   ```
3. ***beforeunload***  ```fires before the page and resources are unloaded. You can use this event to show a confirmation dialog to confirm if you really want to leave the page```
4. ***unload*** ```fires when the page has completely unloaded. You can use this event to send the analytic data or to clean up resources```
</details>


### 💡 Mouse Events:

> ```click``` ```dblclick``` ```mousedown``` ```mouseup``` ```mouseenter``` ```mouseleave``` ```mousemove``` ```mouseover```

### 💡 Keyboard Events:

> ```keyup``` ```keydown``` ```keypress```

> **The keyboard event object has two important properties:** ```key``` and ```code```  properties that allow you to detect which key has been pressed.

### 💡 Focus Events:

> ```focus``` ```focusin``` ```blur``` ```focusout```

### 💡 Clipboard Events:

> ```copy``` ```cut``` ```paste``` 

### 💡 Media Events:

> ```canplay```  ```play``` ```playing``` ```pause``` ```progress``` ```volumechange```

### 💡 Drag and Drop Events:

> ```dragstart``` ```dragend``` ```drag``` ```drop```

### 💡 Scroll Events:

> ```scroll``` 

### 💡 scrollIntoView Events:

```js
// scroll an element into the viewport:
const btn = document.querySelector('.btn');
const js = document.querySelector('.special');
// document.querySelector('html').style.scrollBehavior = 'smooth';
btn.addEventListener("click", ()=>{
  js.scrollIntoView(true);
  js.scrollIntoView({behavior: "smooth", block: "start", inline: "nearest"});
});


```

### 💡 haschange event:

```The hashchange event fires when the URL hash changes from one to another. In this example, it changes from #header to #footer```

> ```hashchange``` 

### 💡 Event Delegation:

> *When it is possible, you can have a single event handler on the document that will handle all the events of a particular type*

```js
let menu = document.querySelector('#menu');

menu.addEventListener('click', (event) => {
    let target = event.target;

    switch(target.id) {
        case 'home':
            console.log('Home menu item was clicked');
            break;
        case 'dashboard':
            console.log('Dashboard menu item was clicked');
            break;
        case 'report':
            console.log('Report menu item was clicked');
            break;
    }
});
``` 

### 💡 dispatchEvent:

> *Use the specific event constructor such as MouseEvent and call dispatchEvent() method on an element to generate an event from code.*

```js
let btn = document.querySelector('.btn');

 btn.addEventListener('click', function () {
        alert('Mouse Clicked');
 });

let clickEvent = new Event('click');
btn.dispatchEvent(clickEvent);
``` 

### 💡 Custom Event:

<details>
<summary>View Content</summary>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JavaScript Custom Event</title>
</head>
<body>
    <div class="note">JS Custom Event</div>
    <script>
        function highlight(elem) {
            const bgColor = 'yellow';
            elem.style.backgroundColor = bgColor;

            // create the event
            let event = new CustomEvent('highlight', {
                detail: {
                    backgroundColor: bgColor
                }
            });
            // dispatch the event
            elem.dispatchEvent(event);
        }

        // Select the div element
        let div = document.querySelector('.note');

        // Add border style
        function addBorder(elem) {
            elem.style.border = "solid 1px red";
        }

        // Listen to the highlight event
        div.addEventListener('highlight', function (e) {
            addBorder(this);

            // examine the background
            console.log(e.detail);
        });

        // highlight div element
        highlight(div);
    </script>
</body>
</html>
``` 
</details>

### 💡 MutationObserver:

> `````` 

</details>
