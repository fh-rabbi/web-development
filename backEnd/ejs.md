<h2 align="center">Embedded Javascript (ejs)</h2>

### `What is ejs & why?`

- ejs stands for embedded javascript
- ejs is a templating language.
- templating language helps us to manipulate dynamic content in HTML document.
- Templating language: ejs, handlebars, pug etc.
- Ejs allows us to run plain js in HTML
- Ejs simple, light weight, fast
- Most downloaded templating language on npm
- Founded in Feb, 2011

### Index of contents:

1. `how to use ejs`
1. `passing data`
2. `if else`
3. `loop`
4. `layout`
5. `styling`

### how to use ejs:
```js
  // first install ejs:
  npm install ejs
  
  // inside the server
  app.set('view engine', 'ejs’);
  
  // create index.ejs inside views folder
  res.render('index',{});
```

### passing data:
```js
  let pLanguages = ["c", "c++"];

  app.get("/", (req, res) => {
    res.render("index", { plNames: pLanguages });
  });

  //inside the index.ejs
   <li><%= plNames[0] %></li>
```

### if else:
```js
<% if(plNames){ %>
  <li><%= plNames[x] %></li>
  <% }else{ %>
  <p>no data found</p>
  <% } %>
```

### loop:
```js
  <% for(let x=0; x<plNames.length; x++){ %>
    <li><%= plNames[x] %></li>
  <% } %>
```

### layout:
```js
  <%- include("layout/header") %>
```

### styling:
```js
app.use(express.static('public'));
// write all styles under the public dir
```