<h1 align="center"><a href="#">MongoDB</a></h1>

## What is MongoDB?
> ***MongoDB is a document-oriented NoSQL database used for high volume data storage. Instead of using tables and rows as in the traditional relational databases, MongoDB makes use of collections and documents. Documents consist of key-value pairs which are the basic unit of data in MongoDB. Collections contain sets of documents and function which is the equivalent of relational database tables. MongoDB is a database which came into light around the mid-2000s.***

## What is Mongoose?

> ***Mongoose is a JavaScript object-oriented programming library that creates a connection between MongoDB and the Node.js JavaScript runtime environment.***

### How to install & use MongoDB in Android

* [geeksforgeeks](https://www.geeksforgeeks.org/how-to-install-mongodb-on-android/amp/)

### Difference between RDBMS & MongoDB

<div align="center">

|Relation|Non Relation|
|--------|------------|
|Database|Database|
|Tables|Collections|
|Rows|Documents|
|Columns|Fields|

</div>

---
<h1 align="center"><a href="#">Core Topics</a></h1>

## Create Document 
* obj.save()
* insertOne()
* insertMany([])
    
* ***Built in Validator:***
   ```js        
   uppercase:true
   lowercase
   unique
   enum
   trim
   minlength
   maxlength
   min --> `For Number` 
   max --> `For Number` // max: 12 --> 0-12!
   enum --> `For Number`
   ```
* ***Custom Validator:***
  ```js
  validate(value){
    if(value < 0){
      throw new Error ('')
    }
    message: ''
  }
  ```

## Read Document
* `.find({})`
* `.findOne({})`
* `.select({name: 1})`
* `.limit(10)`
* ***Relational Operator:***
   ```js
   // gt,gte,lt,lte,eq,ne,in,nin
   
   async function getUsers(){
      try {
         const all_users = await 
            user.find({email: {$ne:'smith@gmail.com'}});
         console.log(all_users);
      } catch (e) {
         console.log(e);
      }
   }
      
   // in & nin usages:
   user.find({skills: {$nin:['Java']}});
   ```
* ***Logical Operator:***
  ```js
   // and,or,nor,xor
   
   async function getUsers(){
      try {
         const all_users = await 
            user.find({$or: [{userName:'SMITH123'},{skills: {$nin:['Php']}}]});
         console.log(all_users);
      } catch (e) {
         console.log(e);
      }
   }        
  ```
* ***Sorting & Counting:***
  * `.sort(1)`
  * `countDocuments()`
  * 💡 **Demo:**
  ```js
   async function getUsers(){
      try {
         const all_users = await 
            user.find()
            .select({userName:1})
            .sort({userName:-1}) // <- (z-a) Sorting!
            // .countDocuments(); // <- Count total document!
         console.log(all_users);
      } catch (e) {
         console.log(e);
      }
   }
  
  ```

## 3. Update Document
* updateOne(filter,updatedValue)
* updateMany(filter,updatedValue)
* findByIdAndUpdate(filter,updatedValue)
* **💡 Demo:**
   ```js
   async function updateUser(_id,userName){
      try {
         const _user = await 
            // user.updateOne({_id},{
            //    $set: {
            //       userName: 'Sakib'
            //    }
            // });
            
            // user.updateMany({userName},{
            //    $set: {
            //       userName: 'John Doe'
            //    }
            // });
            
            user.findByIdAndUpdate({_id},{
               $set: {
                  userName: 'Adams Smith'
               }
            },{new:true}); // <- {new:true} <- it's just for log the changes!
         console.log(_user);
      } catch (e) {
         console.log(e);
      }
   }    
   ```

## Delete Document
* deleteOne(filter)
* deleteMany(filter)
* findByIdAndDelete(filter)
* **💡 Demo:**
   ```js
   async function deleteUser(_id){
      try {
         // const result = await user.deleteOne({_id});
         const result = await user.findByIdAndDelete({_id});
         console.log(result);
         getUsers()
      } catch (e) {
         console.log(e);
      }
   }
   ```

<h1 align="center"><a href="#">Usages</a></h1>

### 🔺 Step 1:
* *npm i mongoose*
* ***db.js:***
    
    ```js
    const mongoose = require('mongoose') 
    const URL = 'connection string';
    
    const connectionParams = { 
      useNewUrlParser: true, 
      useUnifiedTopology: true
    } 
    
    mongoose.connect(URL,connectionParams) 
     .then( () => { 
       console.log('Connected to mongodb database successfully…!');
    }) 
    .catch( (err) => { 
      console.error(`${err}`);
    });
    ```

### 🔺 Step 2:
* *Make Schema Model*
* ***user.model.js:***
    
    ```js
    const mongoose = require("mongoose");

    const userSchema = new mongoose.Schema({
      email: {
        type: String,
        reuire: true,
      },
      password: {
        type: String,
        reuire: true,
      },
      createdOn: {
        type: Date,
        default: Date.now,
      }
    });

    module.exports = mongoose.model("user", userSchema);
    ```

### 🔺 Step 3:
* ***app.js:***

    ```js
    const user = require(./user.model);
    require('./db);
    ```

### 🔺 Step 4:
* ***CRUD Operation***
    
    ```js
    // get all users
    const getAllUsers = async (req,res) => {
      try {
        const users = await User.find();
        res.status(200).json(users);
      } catch (error) {
        res.status(500).send(error.message);
      }
    };
    
    // get specific user
    const getOneUser = async (req,res) => {
      try {
        const user = await User.findOne({id:req.params.id});
        res.send(user);
      } catch (e){
        res.send(e);
      }
    };
    
    // create new user
    const createUser = async (req,res) => {
      try {
        const newUser = new User({
          name: req.body.name,
          age: Number(req.body.age),
        });
        await newUser.save();
        res.send(newUser);
      } catch(e){
        res.send(e);
      }
    };
    
    // update specific user
    const updateUser = async (req,res) => {
      try {
        const user = await User.findOne({id:req.params.id});
        user.name = req.body.name;
        user.age = req.body.age;
        await user.save();
        res.send(user);
      } catch (e){
        res.send(e);
      }
    };
    
    // delete specific user
    const deleteUser = async (req,res) => {
      try {
        await User.deleteOne({id:req.params.id});
        res.json({message: 'user deleted'});
      } catch (e){
        res.send(e);
      }
    };
    ```


