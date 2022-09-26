## Authentication with JWT:

> `JWT`: ***json web token***

* **app.js**

```js
const express = require('express');
const jwt = require('jsonwebtoken');
const app = express();
const cors = require('cors');

// parse the body
app.use(express.json());
app.use(express.urlencoded({extended: true}));

// setup cors
app.use(cors());


/* 
==========================
database  connection
==========================
*/
const mongoose = require('mongoose') ;
const url = 'mongodb+srv://<username>:<password>@cluster0.lhkjd.mongodb.net/dbName';
const connectionParams = { 
  useNewUrlParser: true, 
  useUnifiedTopology: true
};

mongoose.connect(url,connectionParams, (err) => {
  if(err){
    return console.log(err);
  }else{
    console.log('Connected to MongoDB Successful!');
  }
}) 


/* 
==========================
schema  and model
==========================
*/
const userSchema = mongoose.Schema({
  name: {
    type: String,
    required: true
  },
  username: {
    type: String,
    required: true
  },
  password: {
    type: String,
    required: true
  }
});
const user = mongoose.model('user',userSchema);


// registration handler
app.post('/register', async (req,res) => {
  try{
    const newUser = new user({
      name: req.body.name,
      username: req.body.username,
      password: req.body.password
    });
    await newUser.save();
    res.status(200).json({
      mesaage: 'Registration successful.',
      newUser
    }) 
  }catch(err){
    console.log(err);
  }
});


// login checker middleware
const checkLogin = async (req,res,next) => {
  try {
    const token = req.headers.auauthorization;
    const decoded = jwt.verify(token, 'ilovecoding');
    const {name,username} = decoded;
    req.name = name;
    req.username = username;
    next()
  } catch (e) {
    next('Authentication failure');
  }
};

// home route
app.get('/' ,checkLogin,(req,res) => {
  console.log(req.username);
  res.status(200).json({
    id: 100,
    book: 'Bela furabar age',
    amount: 2
  })
});


// login handler
app.post('/login' ,async (req,res) => {
  try{
    const {username,password} = req.body;
    const _user = await user.findOne({username});
    if(_user && _user.password == password){
      const token = jwt.sign( {
        name: req.body.name,
        username
      }, 'ilovecoding');
      res.status(200).json({
        token,
        message: 'Login successful'
      });
    }else{
      res.status(401).json({
        message: 'Authentication failed'
      })
    }
  }catch(err){
    console.log(err);
    res.status(500).json(err);
  }
});


// Start server
app.listen(3000, () => {
  console.log('Server is running ...');
});
```