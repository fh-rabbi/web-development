<h1 align="center">Redux</h1>

### 🤔 What is redux?

> ***A small JS Library
for managing medium/large amount of states globally in your app.
useContext + useReducer Hook ideas will help you to understand redux.***

### 🚨 Main Concepts:
1. `State`
2. `Action`
3. `Reducer`
4. `Store`
5. `Dispatch`

<details>
<summary>Multiple Reducers</h4></summary>

```js
// State,Action,Reducer,Dispatch,Store
const { createStore,applyMiddleware,combineReducers } = require('redux');

// State:
const countState = {
   count: 0
}

const cartState = {
   cartItems: []
}

// Action:
function getCount(){
   return {
      type: 'get_count'
   }
}

function updateCount(){
   return {
      type: 'update_count'
   }
}

function getCarts(){
   return {
      type: 'get_cart'
   }
}

function addCart(item){
   return {
      type: 'add_cart',
      payload: item
   }
}

function countReducer(state = countState, action){
   const {type,payload} = action;
   if(type == 'get_count'){
      return state;
   }
   if(type == 'update_count'){
      return {
         count: state.count + 1
      }
   }
   else{
      return state;
   }
}

function cartReducer(state = cartState, action){
   const {type,payload} = action;
   if(type == 'get_cart'){
      return state;
   }
   if(type == 'add_cart'){
      return {
         cartItems: [...state.cartItems,payload]
      }
   }
   else{
      return state;
   }
}

// Combine reducers:
const rootReducer = combineReducers({
   countR: countReducer,
   cartR: cartReducer
});

const store = createStore(rootReducer);

store.subscribe(()=>{
   console.log(store.getState());
});

store.dispatch(getCount());
store.dispatch(updateCount());
store.dispatch(getCarts());
store.dispatch(addCart('Apple'));

```

</details>

<details>
<summary>Use Middleware</h4></summary>

```js
// State,Action,Reducer,Dispatch,Store
const { createStore,applyMiddleware,combineReducers } = require('redux');
const { default:logger } = require('redux-logger');

// State:
const countState = {
   count: 0
}

// Action:
function getCount(){
   return {
      type: 'get_count'
   }
}

function updateCount(){
   return {
      type: 'update_count'
   }
}


function countReducer(state = countState, action){
   const {type,payload} = action;
   if(type == 'get_count'){
      return state;
   }
   if(type == 'update_count'){
      return {
         count: state.count + 1
      }
   }
   else{
      return state;
   }
}


const store = createStore(countReducer,applyMiddleware(logger));

store.subscribe(()=>{
   console.log(store.getState());
});

store.dispatch(getCount());
store.dispatch(updateCount());

```

</details>

<details>
<summary>API Calling using redux-thunk</h4></summary>

```js
const { createStore,applyMiddleware } = require('redux');
const thunk = require('redux-thunk').default;
const axios = require('axios');
const URL = 'https://jsonplaceholder.typicode.com/todos';

// State:
const initialState = {
   todos: [],
   isLoading: false,
   error: null
}

// action,reducer,store,dispatch

// Reducer:
const reducer = (state=initialState,{type,payload}) => {
   switch (type) {
      case 'get_todos_request':
         return {
            ...state,
            isLoading: true
         }
         break;
      
      case 'get_todos_success':
         return {
            ...state,
            todos: payload,
            isLoading: false
         }
         break;
         
      case 'get_todos_failed':
         return {
            ...state,
            isLoading: false,
            error: payload
         }
         break;
      
      default:
         state;
   }
}

// Fetching data:
const fetchData = () => {
   return (dispatch) => {
      dispatch({type:'get_todos_request'});
      axios.get(URL)
      .then(res=>{
         const data = res.data.map(d=>d.title);
         dispatch({type:'get_todos_success',payload:data})
      })
      .catch(err=>{
         const message = err.message;
         dispatch({type:'get_todos_failed',payload:message})
      })
   }
}

// Create store:
const store = createStore(reducer,applyMiddleware(thunk));

store.subscribe(()=>{
   console.log(store.getState());
})

store.dispatch(fetchData());
```

</details>


<details>
<summary>React-redux counter app</summary>

1. **Index.js**

```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import { BrowserRouter as Router } from 'react-router-dom';
import { Provider } from "react-redux";
import store from './Comp/store';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <Provider store={store}>
   <Router>
     <App />
   </Router>
  </Provider>
);
```

2. **App.js**

```js
import React from 'react';
import Counter from './Comp/Counter';

function App(){
   return(
     <>
       <Counter/>
     </> 
   );
}

export default App;
```

3. **Store.js**

```js
const { createStore } = require('redux');

const initialState = {
   count: 0
}

// action,reducer,store,dispatch

const reducer = (state = initialState,{type}) => {
   switch (type) {
      case 'increment':
         return {
            count: state.count+1
         }
         break;
         
      case 'decrement':
         return {
            count: state.count-1
         }
         break;
         
      case 'reset':
         return {
            count: 0
         }
         break;
      
      default:
        return state;
   }
}

const store = createStore(reducer);

export default store;
```

4. **Counter.js**

```js
import React,{useState} from 'react';
import { useSelector,useDispatch } from 'react-redux';
import store from './store';

function Counter(){
   const count = useSelector(store => store.count);
   const dispatch = useDispatch();
   
   function handleIncrement(argument) {
      dispatch({type: 'increment'});
   }
   
   function handleDecrement(argument) {
      dispatch({type: 'decrement'});
   }
   
   function handleReset(argument) {
      dispatch({type: 'reset'});
   }
   
   return(
     <>
      <h1>Counter App</h1>
      <p>{count}</p>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
      <button onClick={handleReset}>Reset</button>
     </> 
   );
}

export default Counter;
```

</details>

<details>
<summary>React-Redux Api Calling</summary>

1. **Index.js**

```js
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import { BrowserRouter as Router } from 'react-router-dom';
import { Provider } from "react-redux";
import store from './Comp/store';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <Provider store={store}>
   <Router>
     <App />
   </Router>
  </Provider>
);
```

2. **App.js**

```js
import React from 'react';
import Home from './Comp/Home';
import './App.css'

function App(){
   return(
     <>
       <Home/>
     </> 
   );
}

export default App;
```

3. **Home.js**

```js
import React, { useEffect } from 'react';
import store, {fetchData} from './store';
import { useSelector,useDispatch } from 'react-redux'

function Demo(){
   const dispatch = useDispatch()
   const states = useSelector(state => state);
   const {todos,isLoading,error} = states;
   
   useEffect(() => {
      dispatch(fetchData());
   },[])
   
   return(
     <>
       <h2>React-Redux Fetch Data</h2>
       {isLoading && <span>Loading...</span>}
       {todos && todos.map( todo => {
          return <section class='section'>
            <li>{todo.title}</li>
          </section>
       })}
     </> 
   );
}

export default Demo;
```

4. **Store.js**

```js
const { createStore,applyMiddleware } = require('redux');
const axios = require('axios');
const {default: thunk} = require('redux-thunk');
const URL = 'https://jsonplaceholder.typicode.com/todos';

const initialState = {
   todos: [],
   isLoading: false,
   error: null
}

// action,reducer,store,dispatch

const reducer = (state = initialState,{type,payload}) => {
   switch (type) {
      case 'get_todos_request':
         return {
            ...state,
            isLoading: true
         }
         break;
         
      case 'get_todos_success':
         return {
            ...state,
            todos: payload,
            isLoading: false
         }
         break;
         
      case 'get_todos_failed':
         return {
            ...state,
            isLoading: false,
            error: payload
         }
         break;
      
      default:
        return state;
   }
}

export const fetchData = () => {
   return async (dispatch) => {
      try{
         dispatch({type:'get_todos_request'})
         const res = await axios.get(URL)
         const data = await res.data;
         dispatch({type:'get_todos_success',payload:data})
      }catch(err){
         dispatch({type:'get_todos_failed',payload:err.message})
      }
   }
}

const store = createStore(reducer, applyMiddleware(thunk));

export default store;
```

</details>


<details>
<summary>Counter app using Redux-Toolkit</h4></summary>

1. **index.js**

```js
import ReactDOM from 'react-dom/client';
import App from './App';
import { Provider } from 'react-redux'
import store from './app/store'

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
   <Provider store={store}>
      <App />
   </Provider>
);
```
1. **App.js**

```js
import React from 'react';
import Home from './Comp/Home';
import './App.css'

function App(){
   return(
     <>
       <Home/>
     </> 
   );
}

export default App;
```
1. **store.js**

```js
import { createSlice,configureStore } from '@reduxjs/toolkit'

// name,initialState,reducers
const counterSlice = createSlice({
   name: 'counter',
   initialState: {
      count: 0,
   },
   reducers: {
      increment: (state) => {
         state.count = state.count + 1
      },
      decrement: (state) => {
         state.count = state.count - 1
      },
      reset: (state) => {
         state.count = 0
      },
      inBy5: (state,{payload}) => {
         state.count = state.count + payload
      }
   }
});


export const {increment,decrement,reset,inBy5} = counterSlice.actions;

const store = configureStore({
   reducer: {
      counter: counterSlice.reducer
   }
})

export default store;
```
1. **Home.js**

```js
import React from 'react';
import {
   useSelector,useDispatch
} from 'react-redux'
import {
   increment,decrement,reset,inBy5
} from '../app/store'

function Home(){
   const dispatch = useDispatch();
   const states = useSelector(state => state);
   
   function handleIncrement(){
      dispatch(increment())
      // alert(increment())
   }
   
   function handleDecrement(){
      dispatch(decrement())
   }
   
   function handleReset(){
      dispatch(reset())
   }
   
   function handleinBy5(){
      dispatch(inBy5(5))
   }
   
   return(
     <>
         <h1>Home Page</h1>
         <pre>{ JSON.stringify(states) }</pre>
         <button onClick={handleIncrement}>Increment</button>
         <button onClick={handleDecrement}>Decrement</button>
         <button onClick={handleReset}>Reset</button>
         <button onClick={handleinBy5}>Increment By 5</button>
     </> 
   );
}

export default Home;
```

</details>

<details>
<summary>Api Calling using Redux-Toolkit</h4></summary>

1. **index.js**

```js
import ReactDOM from 'react-dom/client';
import App from './App';
import { Provider } from 'react-redux'
import store from './app/store'

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
   <Provider store={store}>
      <App />
   </Provider>
);
```
1. **App.js**

```js
import React from 'react';
import Home from './Comp/Home';
import './App.css'

function App(){
   return(
     <>
       <Home/>
     </> 
   );
}

export default App;
```
1. **store.js**

```js
import { createSlice,configureStore,createAsyncThunk } from '@reduxjs/toolkit'
import axios from 'axios'

export const fetchPosts = createAsyncThunk('posts/fetchPosts', async () => {
   const URL = 'https://jsonplaceholder.typicode.com/posts';
   const res = await axios.get(URL);
   return res.data;
});

const postSlice = createSlice({
   name: 'posts',
   initialState: {
      isLoading: false,
      posts: [],
      error: null
   },
   extraReducers: (builder) => {
      builder.addCase(fetchPosts.pending, (state) => {
         state.isLoading = true
      })
      builder.addCase(fetchPosts.fulfilled, (state,action) => {
         state.isLoading = false
         state.posts = action.payload
      })
      builder.addCase(fetchPosts.rejected, (state,action) => {
         state.isLoading = false
         state.error = action.error.message
      })
   }
});


const store = configureStore({
   reducer: {
      posts: postSlice.reducer
   }
})

export default store;
```
1. **Home.js**

```js
import React, { useEffect } from 'react';
import { useSelector,useDispatch } from 'react-redux'
import { fetchPosts } from '../app/store'

function Home(){
   const dispatch = useDispatch();
   const states = useSelector(state => state);
   const {isLoading} = states.posts;
   
   useEffect(() => {
      dispatch(fetchPosts());
   },[]);
   
   return(
    <>
      <h1>Home Page</h1>
      {isLoading && <img width='100%' src='https://i.pinimg.com/originals/f9/41/ae/f941ae9d16fd7d2957eea6e5b1100d1e.gif' />}
      <pre>{JSON.stringify(states,null,3)}</pre>
    </> 
   );
}

export default Home;
```

</details>