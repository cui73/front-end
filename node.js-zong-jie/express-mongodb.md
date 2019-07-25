# express mongodb

#### Why use MongoDB/Mongoose <a id="why-use-mongodbmongoose"></a>

* Node.js and MongoDB are a pair made for each other. Being able to use JSON across the board and JavaScript makes development very easy.
* Mongoose is an object modeling package for Node that essentially works like an ORM.
* Mongoose allows us to have access to the MongoDB commands for CRUD simply and easily.

#### Adding Mongoose to Express Application <a id="adding-mongoose-to-express-application"></a>

MongoDB provide native driver for Node.js called “mongodb” which you can use to connect to MongoDB and perform various CRUD operation. There is another more popular MongoDB recommended node module called “mongoose” and this one we are going to use.

First of all, you need install Mongoose in your project \(package.json\) like any other dependency — using NPM. To install it, use the following command inside your project folder:

```text
npm install mongoose --save
```

**NOTE: Installing Mongoose adds all its dependencies, including the MongoDB database driver, but it does not install MongoDB itself. If you want to install a MongoDB server then you can download installers from** [**here**](https://docs.mongodb.com/manual/administration/install-community/) **for various operating systems and install it locally. You can also use cloud-based MongoDB instances.**

Then you need to setup the connection for the mongodb using mongoose in your project, see `/config/database.js` as below:

```text
const mongoose = require('mongoose');const db = mongoose.connection;mongoose.connect('mongodb://127.0.0.1:27017/yourDatabase');db.once('open', function() {  console.log('mongodb connected.');});
```

**NOTE: In order to run setup the connect from your express app to mongodb, you have to run the mongodb in your local first by** **`mongod`, then you will see something like** **`waiting for connections on port 27017`** **in your terminal, which means mongodb is up and running in your local machine. If you prefer using a cloud mongodb host,** [**mLab**](https://mlab.com/) **is one of the most popular cloud database service and you have the option to get the Sandbox Plan for free.**

#### CRUD And RestFul API <a id="crud-and-restful-api"></a>

CRUD is an acronym for Create, Read, Update and Delete. It is a set of operations we get servers to execute \(POST, GET, PUT and DELETE respectively\). This is what each operation does:

* Create \(POST\) - Make something
* Read \(GET\)\_- Get something
* Update \(PUT\) - Change something
* Delete \(DELETE\)- Remove something

#### Define Models <a id="define-models"></a>

Models are defined using the Schema interface. The Schema allows you to define the fields stored in each document along with their validation requirements and default values.

Let's create a Schema for our first model `User`:

```text
const mongoose = require('mongoose');const Schema = mongoose.Schema;​// create user schemaconst userSchema = new Schema({  firstName: String,  lastName: String,  username: {type: String, required: true, unique: true},  password: {type: String, required: true},  location: String,  created_at: Date,  updated_at: Date,});​// the schema is useless so far// we need to create a model using it
```

Each key in our code userSchema defines a property in our documents which will be cast to its associated SchemaType. For example, we've defined a property `username` which will be cast to the String SchemaType, as well as it cannot be empty and it has to be the unique value.

Following are all valid Schema Types.

* String
* Number
* Date
* Buffer
* Boolean
* Mixed
* Objectid
* Array

Here is the [link to the official documentation for `SchemaType`](http://mongoosejs.com/docs/schematypes.html), where you can find details for other parameters for a property in the `Schema`.

Then let's create the `User` model using the `userSchema`:

```text
const mongoose = require('mongoose');const Schema = mongoose.Schema;​// create user schemaconst userSchema = new Schema({  firstName: String,  lastName: String,  username: {type: String, required: true, unique: true},  password: {type: String, required: true},  location: String,  created_at: Date,  updated_at: Date,});​// the schema is useless so far// we need to create a model using itconst User = mongoose.model('User', userSchema);​// make this available to our users in our Node applicationsmodule.exports = User;
```

So now we have our first model `User`, what can we do with the new model?

#### Read <a id="read"></a>

* Find all

```text
// get all the usersUser.find({}, function(err, users) {  if (err) throw err;​  // object of all the users  console.log(users);});
```

* Find one

```text
// get the user with username haochuanUser.find({username: 'haochuan'}, function(err, user) {  if (err) throw err;​  console.log(user);});
```

* Find by ID

```text
// get a user with ID of 1User.findById(1, function(err, user) {  if (err) throw err;​  // show the one user  console.log(user);});
```

#### Update <a id="update"></a>

* Get and then update

```text
// get a user with ID of 1User.findById(1, function(err, user) {  if (err) throw err;​  // change the users location  user.location = 'uk';​  // save the user  user.save(function(err) {    if (err) throw err;​    console.log('User successfully updated!');  });});
```

* Find and then update

```text
// find the user haochuan// update him to haochuan_newUser.findOneAndUpdate(  {username: 'haochuan'},  {username: 'haochuan_new'},  function(err, user) {    if (err) throw err;​    // we have the updated user returned to us    console.log(user);  },);
```

* Find by id and update

```text
// find the user with id 1// update username to haochuan_newUser.findByIdAndUpdate(1, {username: 'haochuan_new'}, function(err, user) {  if (err) throw err;​  // we have the updated user returned to us  console.log(user);});
```

#### Delete <a id="delete"></a>

* Get then remove

```text
// get the user haochuanUser.find({username: 'haochuan'}, function(err, user) {  if (err) throw err;​  // delete him  user.remove(function(err) {    if (err) throw err;    console.log('User successfully deleted!');  });});
```

* Find then remove

```text
// find the user with username haochuanUser.findOneAndRemove({username: 'haochuan'}, function(err) {  if (err) throw err;​  // we have deleted the user  console.log('User deleted!');});
```

* Find by Id then remove

```text
// find the user with id 1User.findByIdAndRemove(1, function(err) {  if (err) throw err;​  // we have deleted the user  console.log('User deleted!');});
```

#### Run a function before saving <a id="run-a-function-before-saving"></a>

We also want to have a `created_at` variable to know when the record was created, as well as a `update_at` variable to know when the record was updated . We can use the Schema `pre` method to have operations happen before an object is saved.

```text
// on every save, add the dateuserSchema.pre('save', function(next) {  // get the current date  const currentDate = new Date();​  // change the updated_at field to current date  this.updated_at = currentDate;​  // if created_at doesn't exist, add to that field  if (!this.created_at) this.created_at = currentDate;​  next();});
```

[  
](https://gzqsjtu.gitbook.io/workspace/nodejs)

