# Json:

> ***JSON is an open standard file format and data interchange format that uses human-readable text to store and transmit data objects consisting of attribute–value pairs and arrays. It is a common data format with diverse uses in electronic data interchange, including that of web applications with servers***

## package.json
```json
{
  "type" : "comonjs"
}
```

## data.Json
```json
{
  "name" : "smith",
  "age" : 20
}
```

## main.js
```js
const data = require('./data.json');
console.log(data);
```