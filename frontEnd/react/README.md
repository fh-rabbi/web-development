<h1 align="center">REACT NOTES</h1>
<details>
<summary>React Roadmap</summary>

© `Thanks` to [Nishasingla](https://instagram.com/nishasingla05)

![Fundamentals](https://user-images.githubusercontent.com/71178740/182988945-0a7baf71-ece3-4321-8e0d-0a14e18cd82c.jpg)
![Advanced](https://user-images.githubusercontent.com/71178740/182989194-d81767a3-997b-41a3-9819-d2a63db94fc5.jpg)
![Ecosystem](https://user-images.githubusercontent.com/71178740/182989006-6fd132a9-e938-4c2e-9e67-1923a2dfae53.png)

</details>


### `Learn React:`

1. [w3schools](https://www.w3schools.com/react)

2. [30-Days-Of-React](https://github.com/Asabeneh/30-Days-Of-React)

3. [React-For-Everyone](https://github.com/Asabeneh/React-For-Everyone)

### `React cheatsheets:`
1. [developer-cheatsheets](http://www.developer-cheatsheets.com/react)

2. [devhints](https://devhints.io/react)

---

<a id="fundamentals"/>

## Fundamentals:

* [What is react js?](#react)
* [create-react-app](#cra)
* [JSX](#jsx)
* `Components`
    * [Class Component](#ccom)
    * [Functional Component](#fcom)
* [Components Lifecycle](#lifecycle)
* [Conditional Rendering](#conditions)
* [List,Keys & Map](#list)
* `Hooks:`
    * [useState](#useState)
    * [useEffect](#useEffect)
* [Props & Destructuring](#props)
* [Events](#events)
* [Forms](#forms)
* [PropTypes](#propTypes)
* [Memo](#memo)

<a id="advanced"/>

<a id="advanced"/>

## Advanced:

* [Composition vs Inheritance](#Composition)
* [Higher Order Components](#Higher)
* [Rendering Props](#Render)
* [Context](#Context)
* [Lazy Loading](#Lazy)
* `Styling Components:`
    * [Inline CSS + Internal CSS](#Inline)
    * [External CSS](#External)
    * [Moduler CSS](#Moduler)
    * [Styled Components](#Styled)
    * [Bootstrap](#bootstrap)
    * [Tailwindcss](#tailwindcss)
    * [Sass](#sass)
* `Hooks:`
    * [useMemo](#useMemo)
    * [useCallback](#useCallback)
    * [useRef](#useRef)
        * [Forward Ref](#Forward)
    * [useContext](#useContext)
    * [useReducer](#useReducer)
    * [Custom Hooks](#Custom)
* `Router:`
    * [Basic routing](#Basic)
    * `Hooks:`
        * [Link]()
        * [NavLink]()
        * [useNavigate]()        
        * [useLocation](#useLocation)
    * [Dynamic routing](#Dynamic)
    * [Private Routing](#Private)
    * [Query parameter](#Query)
        * `useSearchParams`
    * [Form Handling With (Formik)](#formik)
    * [Google Map Api]

<a id="Firebase"/>

## React Firebase:
* [Hosting](#hosting)
* [Realtime Database](#RealtimeDB)
* [Firestore Database](#FirestoreDB)
* `Authentication:`
    * [Email Password](#emailauth)
    * [Phone](#)
    * [Google](#googleauth)
    * [Facebook](#)
    * [Github](#)

---

<div align="center">

`Fundamentals Section`

</div>

---

<a id="react"/>

### What is react:
> `React` is a free and open-source front-end JavaScript library for building user interfaces based on UI components and (SPA) Single Page Application.

**[⬆ Back to Top](#fundamentals)**

<a id="cra"/>

### create-react-app:
`npx create-react-app my-app`</br>
**[⬆ Back to Top](#fundamentals)**

<a id="jsx"/>

### JSX:
> JSX stands for JavaScript XML. JSX allows us to write HTML in React. JSX makes it easier to write and add HTML in React.
```js
export default function Demo(){
  const name = 'Karim';
  const myElement = <h1>I Love JSX!</h1>;
  return(
    <div>
      <h2>Hello {name}</h2>
      <h3>{Math.random()}</h3>
      {myElement}
    </div>
  );
}
```

**[⬆ Back to Top](#fundamentals)**

<a id="ccom"/>

### Class Component:
```js
import React from 'react';

class Demo extends React.Component {
  constructor(props){
    super(props);
    this.state = {
      name: 'smith',
      age: 20
    }
  }
  
  handleClick = () => {
    this.setState({
      name: 'David',
      age: 21
    })
  }
  
  render(){
    return(
      <>
        <h2>Hello JSX!</h2>
        <div>
          <li>Name: {this.state.name}</li>
          <li>Age: {this.state.age}</li>
        </div>
        <button onClick={this.handleClick}>Change Data</button>
      </>
    );
  }
}

export default Demo;
```

**[⬆ Back to Top](#fundamentals)**

<a id="fcom"/>

### Functional Component:
```js
export default function Demo(){
  return(
      <h1>Hello !</h1>
    )
}
```

<a id="react"/>

<a id="lifecycle"/>

### Components Lifecycle:

> *Each component in React has a lifecycle which you can monitor and manipulate during its three main phases. The three phases are: Mounting, Updating, and Unmounting.*

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTPh82_VC2g4jttU0Ww8502rQePEJRwipp85A&usqp=CAU)

**[⬆ Back to Top](#fundamentals)**

<a id="conditions"/>

### Conditional Rendering:

> `Using if,else statement:`

```js
export default function Demo(){
  const age = 18;
  let text;
  if(age >= 18){
    text = 'You are adult!';
  }
  else{
    text = 'You are child!';
  }
  return(
    <h1>{text}</h1>
  );
}
```

> `Using ternary operator:`

```js
export default function Demo(){
  const age = 18;
  let text;
  return(
    <h1>{age >= 18 ? text = "adult" : "child"}</h1>
  );
}
```

> `Using logical operator:`

```js
import {useState} from 'react';

export default function Demo(){
  const [age,setAge] = useState(18);
  return(
    age && <h1>Age: {age}</h1>
  );
}
```

**[⬆ Back to Top](#fundamentals)**

<a id="list"/>

### List,Keys & Map:
```js
const data = [
  {
    id: 1,
    name: 'smith',
    age: 20
  },
  {
    id: 2,
    name: 'david',
    age: 22
  }
  ]

export default function Demo(){
  return(
    data.map(obj => <h2 key={obj.id}>Name: {obj.name}</h2>)
  );
}
```

**[⬆ Back to Top](#fundamentals)**

<a id="useState"/>

### useState:
```js
import {useState} from 'react';

export default function Demo(){
  const [name,setName] = useState('David');
  
  const handleClick = () => {
    setName('Smith')
  }
  
  return(
    <div>
      <h2>{name}</h2>
      <button onClick={handleClick}>Change Name</button>
    </div>
  );
}
```

**[⬆ Back to Top](#fundamentals)**

<a id="useEffect"/>

### useEffect:
```js
import {useEffect} from 'react';

export default function Demo(){
  
  // This code will be execute when the Component are rendered!
  useEffect(()=>{
    alert('im useEffect')
  },[])
  
  return(
    <div>
      <h2>Testing useEffect</h2>
    </div>
  );
}
```

**[⬆ Back to Top](#fundamentals)**

<a id="props"/>

### Props & Destructuring:
```js
// App.js
const data = [
  {
    id: 1,
    name: 'smith',
    age: 20
  },
  {
    id: 2,
    name: 'david',
    age: 22
  }
  ]
export default function App(){
  return(
    <Demo data={data} />
  )
}


// Demo.js
export default function Demo(props){
  const {data} = props;
  return(
    <div>
      <h2>{data[0].name}</h2>
    </div>
  );
}
```

**[⬆ Back to Top](#fundamentals)**

<a id="events"/>

### Events:
```js
import {useState} from 'react';

function App() {
  
  const [text,setText] = useState('');
  
  const updateValue = (e)=>{
    setText(e.target.value);
  };
  
  const submit = ()=>{
    alert(text);
  };
  
  return (
    <>
    <input onChange={updateValue} type="text" value={text} />
    <button onClick={submit}>Submit</button>
    </>
  );
}

export default App;
```

**[⬆ Back to Top](#fundamentals)**

<a id="forms"/>

### Forms:
```js
import {useState} from 'react';

export default function Demo(props){
  const {text} = props;
  const [data,setData] = useState({
    name: '',
    email: ''
  });
  
  const submit = (e) => {
    e.preventDefault();
    alert(data.name+' || '+data.email)
  }
  
  const change = (e) => {
    setData({
      ...data,
      [e.target.name]: e.target.value
    })
  }
  
  return(
    <form onSubmit={submit} class="form m-3">
      <label for="">Name:</label>
      <input onChange={change} class="form-control" type="text" name="name" id="" value={data.name} />
      <label for="">Email:</label>  
      <input onChange={change} class="form-control" type="email" name="email" id="" value={data.email} />
      <button class="mt-2 btn btn-danger" type="submit">Submit</button>
    </form>
  );
}
```

**[⬆ Back to Top](#fundamentals)**

<a id="propTypes"/>

### PropTypes:
```js
import PropTypes from 'prop-types';

export default function Demo(props){
  const {text} = props;
  return(
    <div>
      <h2>{text}</h2>
    </div>
  );
}

Demo.propTypes = {
  text: PropTypes.string
}


Demo.defaultProps = {
  text: "john doe"
}
```

**[⬆ Back to Top](#fundamentals)**

<a id="memo"/>

### Memo:

> `When to use React.memo()`

![](https://dmitripavlutin.com/static/c07d2ce4ede6301197b9605a75ae9b4e/47a22/when-to-use-react-memo-infographic.webp)

```js
//App.js
import Demo from './Demo'
import {useState} from 'react';

export default function App(){
  const [name,setName] = useState('david');
  const [data, setData] = useState('smith');
  
  const handleClick = () => {
    setName('smith');
  }
  
  return(
    <>
      <Demo data={data}/>
      <h2>Name: {name}</h2>
      <button onClick={handleClick}>Change Name</button>
    </>
  )
}


// Demo.js
import {useEffect,memo} from 'react';

function Demo({data}){
  
  alert('demo rendered !')
  
  return(
    <>
      <h1>{data}</h1>
    </>
  );
}

export default memo(Demo);
```

**[⬆ Back to Top](#fundamentals)**

---

<div align="center">

`Advanced Section`

</div>

---

<a id="Composition"/>

### Composition vs Inheritance:

> `Composition:`

```js
// App.js
import Inheritance from './Inheritance'
import Demo from './Demo'

export default function App(){
  return(
    <>
      <Demo>
        {({addEmoji}) => <Inheritance addEmoji={addEmoji}/>}
      </Demo>
    </>
  );
}


// Demo.js
import React from 'react';

class Demo extends React.Component {
  constructor(props){
    super(props);
  }
  
  addEmoji(text,emoji){
    return `${emoji} ${text} ${emoji}`
  }
  
  render(newText){
    let text = 'Hello Im Demo';
    if(newText){
      text = newText;
    }
    return this.props.children({addEmoji:this.addEmoji})
  }
}

export default Demo;


// Inheritance.js
import Demo from './Demo';

function Inheritance({addEmoji}){
  let text = addEmoji('Okey!','✔️');
  // alert(addEmoji)
  return text;
}

export default Inheritance;
```

> `Inheritance:`

```js
// App.js
import Inheritance from './Inheritance'
import Demo from './Demo'

export default function App(){
  return(
    <>
      <Inheritance/>
    </>
  );
}


// Demo.js
import React from 'react';

class Demo extends React.Component {
  constructor(props){
    super(props);
  }
  
  addEmoji(text,emoji){
    return `${emoji} ${text} ${emoji}`
  }
  
  render(newText){
    let text = 'Hello Im Demo';
    if(newText){
      text = newText;
    }
    return(
      <div>
        <h1>{text}</h1>
      </div>
    );
  }
}

export default Demo;


// Inheritance.js
import Demo from './Demo';

class Inheritance extends Demo {
  constructor(){
    super();
  }
  render(){
    let text = this.addEmoji('Hello Im Inheritance','😍');
    // alert(this.addEmoji?'found':'notFound')
    return super.render(text);
  }
}

export default Inheritance;
```

**[⬆ Back to Top](#advanced)**

<a id="Higher"/>

### Higher Order Components:

> *A higher-order component is a function that takes a component and returns a new component. A higher-order component (HOC) is the advanced technique in React.js for reusing a component logic. Higher-Order Components are not part of the React API. They are the pattern that emerges from React’s compositional nature. The component transforms props into UI, and a higher-order component converts a component into another component.*

```js
// App.js
import Click from './hoc/Click'
import Hover from './hoc/Hover'

export default function App(){
  return(
    <>
      <Click/>
      <Hover/>
    </>
  );
}


// Click.js
import WithCount from './WithCount'
import {useState} from 'react';

function Click({count,handleClick}){

  return(
    <>
      <h2>Clicked {count} time </h2>
      <button onClick={handleClick}>Click Me</button>      
    </>
  )
}

export default WithCount(Click);


// Hover.js
import WithCount from './WithCount'
import {useState} from 'react';

function Hover({count,handleClick}){
  
  return(
    <h2 onMouseOver={handleClick}>Clicked {count} time </h2>
  )
}

export default WithCount(Hover);


// WithCounter.js
import {useState} from 'react'

export default function WithCount(OriginalComponent){
  function NewComponent(){
    const [count,setCount] = useState(0);
  
    const handleClick = () => {
      setCount(count+1);
    }
    return(
      <OriginalComponent count={count} handleClick={handleClick}/>
    )
  }
  return NewComponent;
}
```

**[⬆ Back to Top](#advanced)**

<a id="Render"/>

### Render Props:

> Render prop is a prop that `defines` render logic to other `component`.

* `Basic render prop:`

```js
// App.js
import Demo from './Demo';

const isLoggedIn = true;
export default function App(){
  return(
    <>
      <Demo name={ (isLoggedIn) => isLoggedIn ? 'Logged In!' : 'Not Logged In!'} />
    </>
  );
}


// Demo.js
export default function Demo(props){
  const {name} = props;
  return name(true);
}
```

* `Advanced render prop:`

<details>
<summary>View Code</summary>

```js
// App.js
import ClickCounter from './core/ClickCounter';
import HoverCounter from './core/HoverCounter';
import Counter from './core/Counter'

const isLoggedIn = true;
export default function App() {
  return(
    <> 
      < Counter render = {
        (count, handleClick) => < ClickCounter count = {
          count
        } handleClick = {
          handleClick
        } />
      } />
      
      < Counter render = {
        (count, handleClick) => < HoverCounter count = {
          count
        } handleClick = {
          handleClick
        } />
      } />
    </>
  );
}


// Counter.js
import {useState} from 'react';

export default function Counter(props){
  const {render} = props;
  const [count,setCount] = useState(0);
  
  const handleClick = () => {
    setCount(prev => prev+1);
  }
  return render(count,handleClick);
}


// ClickCounter.js
// import {useState} from 'react';

export default function ClickCounter(props){
  // const [count,setCount] = useState(0);
  
  // const handleClick = () => {
  //   setCount(prev => prev+1);
  // }
  const {count,handleClick} = props;
  return(
    <>
      <div class="container p-4">
        <h3 class="text-primary">
          Clicked {count} Times
        </h3>
        <button onClick={handleClick} class="btn btn-danger" type="submit">
          Count
        </button>
      </div>
    </>
  );
}


// HoverCounter.js
// import {useState} from 'react';

export default function HoverCounter(props){
  // const [count,setCount] = useState(0);
  
  // const handleHover = () => {
  //   setCount(prev => prev+1);
  // }
  const {count,handleClick} = props;  
  return(
    <>
      <div class="container p-4">
        <h3 onMouseOver={handleClick} class="text-primary">
          Hovered {count} Times
        </h3>
      </div>
    </>
  );
}
```

</details>

**[⬆ Back to Top](#advanced)**

<a id="Context"/>

### Context:

1. `React Context is a way to manage state globally.`
> ***It can be used together with the `useState` Hook to share state between deeply nested components more easily than with useState alone.***

**[⬆ Back to Top](#advanced)**

<a id="Lazy"/>

### Lazy Loading:

> *In essence, lazy loading means that a component or a part of code must get loaded when it is required. It is also referred to as code splitting and data fetching.*

![nishasingla05-20220807-0003~2](https://user-images.githubusercontent.com/71178740/183284429-945b555e-782e-4455-b931-1784b4fa4368.jpg)
![nishasingla05-20220807-0001~2](https://user-images.githubusercontent.com/71178740/183284439-e6a166b1-18d6-4f78-8459-e7a1fcfdbb6b.jpg)
![nishasingla05-20220807-0010~2](https://user-images.githubusercontent.com/71178740/183284446-f8ce7410-784d-4194-b1e4-a0ccb0b7d684.jpg)


**[⬆ Back to Top](#advanced)**

<a id="Inline"/>

### Inline CSS:
```js
// Demo.js
export default function Demo(){
  const headingStyle = {
    color: 'lime',
    background: 'black',
    textAlign: 'center',
    margin: '1rem',
    padding: '1.2rem',
    borderRadius: '3px'
  }
  return(
    <>
      <h1 style={{color:'red'}}>Hello World!</h1>
      <h1 style={headingStyle}>Hello World!</h1>
    </>
  );
}
```

**[⬆ Back to Top](#advanced)**

<a id="External"/>

### External CSS:
```js
// Demo.js
import './demo.css'

export default function Demo(){
  return(
    <>
      <h1>Hello World!</h1>
    </>
  );
}


// Demo.css
h1{
  text-align: center;
  color: red;
  margin: 10px;
  padding: 10px;
  background: #333;
  border-radius: 4px;
}
```

**[⬆ Back to Top](#advanced)**

<a id="Moduler"/>

### Moduler CSS:
```js
// Demo.js
import styles from './demo.module.css'

export default function Demo(){
  return(
    <>
      <h1 class={styles.heading1}>Hello World!</h1>
    </>
  );
}

// demo.module.css
.heading1{
  color: red;
}
```

**[⬆ Back to Top](#advanced)**

<a id="Styled"/>

### Styled Components:

> Styled-components is a popular library that is used to style React applications. It allows you to build custom components by writing actual CSS in your `JavaScript`.

```js
// Home.js
import styled, {ThemeProvider} from 'styled-components';
import GlobalStyle from './GlobalStyle'
// import MyStyle from './homeStyle';

export default function Home(){
  
  // My Theme:
  const theme = {
    color: {
      primary: '#1b3d8b'
    }
  }
  
  // My Style:
  const MyStyle = styled.div`
    background: ${({bg})=> bg};
    padding: 10px;
      h2{
        color: white;
      }
      .card{
        background: ${({theme})=> theme.color.primary};
        color: white;
        padding: 10px;
        border-radius: 7px;
      }
  `;
  
  return(
    <ThemeProvider theme={theme}>
    <GlobalStyle/>
    <MyStyle bg="#1aaba9">
      <div class="main">
        <h2>Lorem Ipsum</h2>
        <div class="card">
          <h2>Title</h2>
          <p>Autem doloribus aut perferendis voluptas vero consectetur. Sit distinctio temporibus est excepturi est. Nostrum id quod consequatur quidem eos. Est similique mollitia voluptatibus vero quia sequi et illum.</p>
        </div>
      </div>
    </MyStyle>
    </ThemeProvider>
  );
}


// GlobalStyle.js
import { createGlobalStyle } from 'styled-components';

const GlobalStyle = createGlobalStyle`
  body{
    background: black;
    display: grid;
    height: 100vh;
    place-items: center;
    font-family: 'Ubuntu', sans-serif;
  }
`;

export default GlobalStyle;
```

**[⬆ Back to Top](#advanced)**

<a id="bootstrap"/>

### Bootstrap:

* `npm i bootstrap`

```js
import '../node_modules/bootstrap/dist/css/bootstrap.min.css';
import '../node_modules/bootstrap/dist/css/bootstrap.min.js';
```

**[⬆ Back to Top](#advanced)**

<a id="tailwindcss"/>

### Tailwindcss:

```js

```

**[⬆ Back to Top](#advanced)**

<a id="sass"/>

### Sass:

* `npm i sass`

```js
import './demo.scss'
```

**[⬆ Back to Top](#advanced)**

<a id="useMemo"/>

### useMemo:

1. *The React useMemo Hook returns a memoized value.*
2. *The useMemo Hook only runs when one of its dependencies update.*

```js
import { useState,useMemo } from "react";
import ReactDOM from "react-dom/client";

const Demo = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);
  const calculation = useMemo(()=> expensiveCalculation(count),[count]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = () => {
    setTodos((t) => [...t, "New Todo"]);
  };

  return (
    <div>
      <div>
        <h2>My Todos</h2>
        {todos.map((todo, index) => {
          return <p key={index}>{todo}</p>;
        })}
        <button onClick={addTodo}>Add Todo</button>
      </div>
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
        <h2>Expensive Calculation</h2>
        {calculation}
      </div>
    </div>
  );
};

const expensiveCalculation = (num) => {
  console.log("Calculating...");
  for (let i = 0; i < 100000000; i++) {
    num += 1;
  }
  return num;
};

export default Demo;
```

**[⬆ Back to Top](#advanced)**

<a id="useCallback"/>

### useCallback:

1. *The React useCallback Hook returns a memoized callback function.*
2. *The useCallback and useMemo Hooks are similar. The main difference is that useMemo returns a memoized value and useCallback returns a memoized function.*
3. **Use the useCallback Hook to prevent the Todos component from re-rendering needlessly**

```js
// App.js
import { useState, useCallback } from "react";
import ReactDOM from "react-dom/client";
import Todos from "./Todos";

const App = () => {
  const [count, setCount] = useState(0);
  const [todos, setTodos] = useState([]);

  const increment = () => {
    setCount((c) => c + 1);
  };
  const addTodo = useCallback(() => {
    setTodos((t) => [...t, "New Todo"]);
  }, [todos]);

  return (
    <>
      <Todos todos={todos} addTodo={addTodo} />
      <hr />
      <div>
        Count: {count}
        <button onClick={increment}>+</button>
      </div>
    </>
  );
};
export default App;


// Todos.js
import { memo } from "react";

const Todos = ({ todos, addTodo }) => {
  console.log("child render");
  return (
    <>
      <h2>My Todos</h2>
      {todos.map((todo, index) => {
        return <p key={index}>{todo}</p>;
      })}
      <button onClick={addTodo}>Add Todo</button>
    </>
  );
};

export default memo(Todos);
```

**[⬆ Back to Top](#advanced)**

<a id="useRef"/>

### useRef:
```js
import { useRef } from 'react';

export default function Demo(){
  const h2 = useRef();
  
  h2.current.style.color = 'red';
  
  return(
    <h2 ref={h2}>Hello World!</h2>
  );
}
```

**[⬆ Back to Top](#advanced)**

<a id="Forward"/>

### Forward ref:
```js
// App.js
import Demo from './Demo';

export default function App(){
  return(
    <Demo/>
  );
}

// Demo.js
import { useRef,useEffect } from 'react';
import Input from './Input';

export default function Demo(){
  const inputElement = useRef();
  
  useEffect(()=>{
    inputElement.current.focus();
    inputElement.current.style.color = 'red';
  },[])
  
  return(
    <>
      <Input placeholder="Enter name" ref={inputElement} />
    </>
  );
}

// Input.js
import React from 'react';

const Input = React.forwardRef((props,ref) => {
  return(
    <>
      <input ref={ref} {...props} type="text" />
    </>
  );
})

export default Input;

```

**[⬆ Back to Top](#advanced)**

<a id="useContext"/>

### useContext:
```js
// App.js
import Counter from './core/Counter';
import MyState from './Context/MyState';

export default function App(){
  return(
    <MyState>
      <Counter/>
    </MyState>
  );
}


// Counter.js
import {useContext} from 'react';
import MyContext from '../Context/MyContext';

export default function Counter(){
  const GlobalData = useContext(MyContext);
  const {name,count,handleClick} = GlobalData;
  
  return(
    <div class="container p-4">
      <h3 class="text-primary">
        Clicked {count} Times
      </h3>
      <button onClick={handleClick} class="btn btn-danger" type="submit">
        Count
      </button>
      <h2>Hello {name}!</h2>
    </div>
  );
}


// MyContext.js
import {createContext} from 'react';

const MyContext = createContext();

export default MyContext;


// MyState.js
import {useState} from 'react';
import MyContext from './MyContext';

const MyState = (props) => {
  const [count,setCount] = useState(0);
  
  const handleClick = () => {
    setCount(count+1);
  }
  
  // data 
  const data = {
    name: 'Karim',
    count,
    handleClick
  }
  
  return(
    <MyContext.Provider value={data}>
      {props.children}
    </MyContext.Provider>
  );
}

export default MyState;
```

**[⬆ Back to Top](#advanced)**

<a id="useReducer"/>

### useReducer:
```js
import {useState,useReducer} from 'react';

export default function Demo(){
  // const [data,setData] = useState(['apple','orange','banana']);
  // const [loading,setLoading] = useState(true);
  
  // const click = () => {
  //   setData([
  //       'C',
  //       'Python',
  //       'Java'
  //     ])
  // }
  
  
  const reducer = (state,action) => {
    if(action.type === 'CHANGE_DATA'){
      return [...state,'c','java','python']
    }
  }
  
  const [data,dispatch] = useReducer(reducer,['apple','orange','banana']);
  
  const click = () => {
    dispatch({
      type: 'CHANGE_DATA',
      payload: ['C','Java','Javascript']
    })
  }
  
  return(
    <>
      {data.map(d=>{
        return <li>{d}</li>
      })}
      <button onClick={click}>Add New Data</button>
    </>
  );
}
```

**[⬆ Back to Top](#advanced)**

<a id="Custom"/>

### custom hooks:
```js
// Demo.js
import useFetch from './useFetch'

export default function Demo(){
  const data = useFetch('https://jsonplaceholder.typicode.com/posts');
  
  return(
    <div class="container">
      {data && data.map(d=>{
        return <div>
          <li class="list-item">{d.title}</li>
          <p>{d.body}</p>
        </div>
      })}
    </div>
  );
}


// useFetch.js
import {useState,useEffect} from 'react';

export default function useFetch(url){
  const [data,setData] = useState([]);
  
  useEffect(()=>{
    const getData = async() => {
      const res = await fetch(url)
      const data = await res.json();
      setData(data);
    }
    
    getData();
  })
  
  return data;
}
```

**[⬆ Back to Top](#advanced)**

<a id="Basic"/>

### Basic routing:

⬇️ `npm install react-router-dom`

```js
====================
App.js
====================
import React from 'react';
import NavBar from './pages/NavBar'
import Home from './pages/Home'
import About from './pages/About'
import Contact from './pages/Contact'

import {
  BrowserRouter as Router,
  Routes,
  Route
} from 'react-router-dom';

const App = () =>{
    return(
      <div>
      <Router>
        <NavBar/> 
        <Routes>
          <Route path="/home" element={<Home/>}/>
          <Route path="/about" element={<About/>}/>
          <Route path="/contact" element={<Contact/>}/>
        </Routes>
      </Router>
      </div>
      )
}
export default App;


====================
NavBar.js
====================
import {Link} from 'react-router-dom'

const NavBar = ()=>{
  return(
    <>
      <nav className="nav bg-dark">
        <li className="nav-item"><Link className="nav-link" to="/">Home</Link></li>
        <li className="nav-item"><Link className="nav-link" to="/about">About</Link></li>
        <li className="nav-item"><Link className="nav-link" to="/contact">Contact</Link></li>
      </nav>    
    </>
    )
}
export default NavBar;


====================
Redirect:
====================
import { useNavigate } from "react-router-dom";

const Contact = ()=>{
  const navigate = useNavigate();
  return(
    <>
     <h1>Contact Page</h1>
     <button onClick={()=>{
       navigate("/")
     }}>Go To Home</button>
    </>
    )
}
export default Contact;
```

**[⬆ Back to Top](#advanced)**

<a id="Dynamic"/>

### Dynamic routing:

1. *App.js:*

```js
import React from 'react';
import NavBar from './pages/NavBar'
import Home from './pages/Home'
import About from './pages/About'
import Contact from './pages/Contact'
import Blogs from './dynamicRouting/Blogs'
import Blog from './dynamicRouting/Blog'

import {
  BrowserRouter as Router,
  Routes,
  Route
} from 'react-router-dom';

const App = () =>{
    return(
      <div>
      <Router>
        <NavBar/> 
        <Routes>
          <Route path="/home" element={<Home/>}/>
          <Route path="/about" element={<About/>}/>
          <Route path="/contact" element={<Contact/>}/>
          <Route path="/blogs" element={<Blogs/>}/>
          <Route path="/blogs/:title" element={<Blog/>}/>
        </Routes>
      </Router>
      </div>
      )
}
export default App;
```

2. *Blogs.js:*

```js
import {data} from './data'
import {Link} from 'react-router-dom'

const Blogs = ()=>{
  
  const lengthCutter = (str,num)=>{
    return str.slice(0,num)+'...';
  }
  
  return(
    <>
      {data.map(blogData=>{
        return <div class="container" key={blogData.id}>
         <h2>{blogData.title}</h2>
         <p>{lengthCutter(blogData.body,200)}</p>
         <Link to={blogData.title}>Read More</Link>
        </div>
      })}
    </>
    )
}
export default Blogs;
```

3. *Blog.js:*

```js
import {useParams} from 'react-router-dom'
import {useState,useEffect} from 'react'
import {data} from './data'

const Blog = ()=>{
  const [blogData,setBlogData] = useState({});
  const {title} = useParams();
  
  useEffect(()=>{
    const filteredBlog = data.filter(blog=>{
      return blog.title === title;
    })
    setBlogData(filteredBlog[0]);
  },[]);
  
  return(
    <>
     <h1>{title}</h1>
     <p>{blogData.body}</p>
    </>
    )
}

export default Blog;
```

**[⬆ Back to Top](#advanced)**

<a id="Query"/>

### Query parameter:
```js
import {useSearchParams} from 'react-router-dom'
import {useEffect} from 'react'

const Users = ()=>{
  const [searchData,setSeacrhData] = useSearchParams('');
  
  useEffect(()=>{
    setSeacrhData({id:100,name:'rabbi',age:20});
  },[])
  
  return(
    <>
      <h1>im from users</h1>
      <h2>{searchData}</h2>
    </>
    )
}
export default Users;
```

**[⬆ Back to Top](#advanced)**

<a id="Private"/>

### Private routing:
```js
// App.js
<Route path="createBlog" element={
  <ProtectedComponent isLoggedIn={isLoggedIn}>
   <TargetComponent/> // This is child component
  </ProtectedComponent>
}>

// TargetComponent.js
import {Navigate} from 'react-router-dom';
const TargetComponent = ({isLoggedIn,child})=>{
  if(!isLoggedIn){
    return <Navigate to="/" replace/>
  }
  else{
    return child;
  }
}
```

**[⬆ Back to Top](#advanced)**

<a id="useLocation"/>

### useLocation:
```js
const {useLocation} from 'react-router-dom'
const location = useLocation();
```

**[⬆ Back to Top](#advanced)**

<a id="formik"/>

### React Form Handling:

* *App.js*

```js
import Demo from './components/Demo';
import './App.css';

export default function App(){
  return(
    <Demo/>
  );
}
```

* *Demo.js*

```js
import { 
  Formik,
  Form,
  Field,
  ErrorMessage
} from 'formik';
import * as Yup from 'yup';

export default function Demo(){
  
  const initialValues = {
    name: '',
    email: ''
  };

  const validationSchema = Yup.object().shape({
    name: Yup.string().required(),
    email: Yup.string().email().required()
  });

  function handleSubmit(values,helpers){
    alert('Okey')
  }
  
  return(
    <Formik 
      initialValues={initialValues}
      validationSchema={validationSchema}
      onSubmit={handleSubmit}
    >
    {(props) => {
      return (
      <>
        <div className='console'>{JSON.stringify(props)}</div>
        <Form className='form'>
          <div class="">
            <label for="name">Name:</label>
            <Field name='name' />
            <ErrorMessage name='name' component='p' />
            {/*<input onBlur={props.handleBlur} onChange={props.handleChange} type="text" name="name" value={props.values.name}/>
            {
              props.touched.name && <p>{props.errors.name}</p> 
            }*/}
          </div>
          <div class="">
            <label for="email">Email:</label>
            <Field name='email' />
            <ErrorMessage name='email' component='p' />
            {/*<input onBlur={props.handleBlur} onChange={props.handleChange} type="email" name="email" value={props.values.email}/>
            {
              props.touched.name && <p>{props.errors.email}</p> 
            }*/}
          </div>
          <button type="submit">Submit</button>
        </Form> 
      </>
      )
    }}
    </Formik>    
  );
}
```

**[⬆ Back to Top](#advanced)**


---

<div align="center">

`React Firebase`

</div>

---

<a id="hosting"/>

### Hosting:

1. `npm install firebase`
2. `firebase init`
3. `firebase deploy`

**[⬆ Back to Top](#Firebase)**

<a id="RealtimeDB"/>

### Realtime Database:

* Get the api from firebase
* In the end of api add `/mydata.json`
* Then send form data using post method

**[⬆ Back to Top](#Firebase)**

<a id="FirestoreDB"/>

## Firestore Database:
1. **lib/firebase-config.js**
```js
........

// Initialize Firestore 
export const db = getFirestore(app);
```
2. **lib/cRef.js**
```js
import {db} from './firebase-config';
import { collection } from 'firebase/firestore';

export const cRef = collection(db, 'notes');

```
3. **create document:**
```js
import { addDoc } from 'firebase/firestore'
import { cRef } from '../lib/Cref'

async function createNewTodo(){
    try {
      await addDoc(cRef, {todo: value})
      setValue('')
    } catch (err) {
      alert(err.message)
    }
  }
```
4. **read document:**
```js
import { db } from '../lib/firebase-config'
import { getDocs,collection,deleteDoc,doc } from 'firebase/firestore'
import { cRef } from '../lib/Cref'

async function getTodos(){
    try {
      // const cRef = await collection(db, 'todos');
      const data = await getDocs(cRef);
      const docs = data.docs.map(doc => {
        return {
          id: doc.id,
          data: doc.data()
        };
      });
      set_test(docs);
      set_todos(docs);
    } catch (err) {
      alert(err.message);
    }
  }
  
  // delete document:
  async function deleteTodo(id){
    try {
      const docRef = doc(db, 'todos', id);
      await deleteDoc(docRef)
      alert('Deleted successfull')
    } catch (err) {
      alert(err.message)
    }
  }
```
5. **update document:**
```js
import { updateDoc,doc } from 'firebase/firestore';
import { db } from '../lib/firebase-config'

async function handleSubmit(event){
    try {
      event.preventDefault();
      if(id === '' && value === ''){
        return alert('Value couldn\'t be empty!')
      }
      const docRef = doc(db, 'todos', id);
      await updateDoc(docRef, {todo: value});
      setId('');
      setValue('');
    } catch (e) {
      alert(e.message)
    }
  }
```


**[⬆ Back to Top](#Firebase)**

<a id="emailauth"/>

### Email & Password Authentication::

1. ***src/firebase.js***

```js
import { initializeApp } from "firebase/app";
import { getAuth } from "firebase/auth";

const firebaseConfig = {
  apiKey: "AIzaSyC0rmBgQumWUZtUidfwwbfp82HnzYp1jIQ",
  authDomain: "react-authentication-bc56d.firebaseapp.com",
  projectId: "react-authentication-bc56d",
  storageBucket: "react-authentication-bc56d.appspot.com",
  messagingSenderId: "450085734069",
  appId: "1:450085734069:web:f56a77b1019a58f937e0fc",
  measurementId: "G-R5C1K1T66Q"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
export const auth = getAuth(app);
export default app;
```

2. ***MyState.js***

```js
import {
  createUserWithEmailAndPassword,
  signInWithEmailAndPassword,
  onAuthStateChanged,
  signOut,
  GoogleAuthProvider,
  signInWithPopup,
} from "firebase/auth";
import { auth } from "../firebase";

  function signUp(email, password) {
    return createUserWithEmailAndPassword(auth, email, password);
  }
  
  function logIn(email, password){
    return signInWithEmailAndPassword(auth, email, password);
  }
  
  function logOut(){
    return signOut(auth);
  }
  
  useEffect(()=>{
    const unsubscribe = onAuthStateChanged(auth, (currentuser)=>{
      setUser(currentuser);
    })
    
    return () => unsubscribe();
  },[])

```

3. ***components/Login.js***

```js
const handleSubmit = async (e) => {
    e.preventDefault();
    try {
      await logIn(email,password);
      navigate('/home');
    } catch(e){
      setError(e);
    }
  }
```

**[⬆ Back to Top](#Firebase)**

<a id="googleauth"/>

### Google Authentication:

1. ***MyState.js***

```js
const handleGoogleSignIn = async () => {
    try {
      await googleSignIn();
      navigate('/home');
    } catch (e) {
      setError(e.message);
    }
  }
```

2. ***Login.js***

```js
function googleSignIn() {
    const googleAuthProvider = new GoogleAuthProvider();
    return signInWithPopup(auth, googleAuthProvider);
  }
```

**[⬆ Back to Top](#Firebase)**


---
