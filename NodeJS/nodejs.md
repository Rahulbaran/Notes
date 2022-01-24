# [NodeJS]()

- Node _REPL (Read-Eval-Print-Loop)_

- All the codes written inside a moudule is wrapped into a _REPL_ function as IIFE and paremeters like `require`,`__dirname`,`__filename`,`exports` & `module` are passed into it by JavaScript Runtime.

- `arguments` is an object(array like object) in JavaScript, which contains only `length` & `index` properties.

- NodeJS has been built **asynchronously**.

- In NodeJS, Every js file is treated as module (similar to python).

- `npm` is a CLI tool to manage node packages(third party) & also a repository which contain all the node packages.

- node packages are of two types -

  - **dependencies** - The application depends on package codes
  - **devDependencies** - The application uses package code in development phase to make project consistent and faster.

- node packages can either be installed locally in project directory or globally in the system.

- **Locally** installed node packages can not be directly used in command line instead we write `scripts` in `package.json` to run those packages.

- most packages in npm follows semantic version rule which means their versions are represted using **3 numbers** (major, minor & patch versions) separated by dot.
  For Example - `nodemon - 1.18.11`

  - patch -- For bug fixes
  - minor -- some new features in package which don't affect our code
  - major -- A huge new change in the package which can break our code

- Symbols in front of version numbers & their meanings

  - `~` allows patches update only
  - `^` allows patches & minor updates
  - `*` allows major updates

- **DNS** - Domain Name System (Like a Phonebook)

- **TCP** - Transmission Control Protocol (Communication Protocol)

- **IP** - Internet Protocol (Communication Protocol)

- **HTTPS** - Data is encrypted using **SSL/TLS** Certificate

- During the **DNS** lookup, Browser matches the Domain name with actual IP Address through **Internet Service Provider(ISP)**.

- After **DNS** lookup, Browser makes a **TCP/IP Socket** Connection.

- **TCP** is responsible for converting the data in thousands small chunks (packets) while making request/response and then reassembling these packets back to its original request/response.

* **IP** is responsible for sending and routing the these data packets

- **IP** address (IPv4 - Current) is a sequence of four sets of number separated by dot(.)

- A Communication Protocol(TCP/IP/HTTP/HTTPS) is a tool for communcation between two/more parties.

- **Web Server** is simply a giant computer connected with internet and contains all the files of any website along with a **HTTP Server**.

- **Web Server** is of two types:-

  - **Static Web Server** - netlify, vercel etc.
  - **Dynamic Web Server** - Heroku, Pythonanywhere, Replit etc.

- **In Frontend Context**, JavaScript is considered to be dynamic whereas **in Backend Context**, A website is considered dynamic if templates are rendered on the server side(JavaScript is considered static in this context).

- Things like **CRUD operations in database**, **rendering templates**, **Handling payments** etc on the **Web Server** make a website **dynamic** (web applications).

- Dynamic websites are created by dynamic web servers by fetching data from a database and rendering templates, the process is known as **Server-side rendering**.

- **HTTP Server** is responsible for handling **requests** and **responses** (in the **Web Server**) based on client actions.

- **libuv** is a main component of **NodeJS** which is an open source library (developed using C++) with focus on

  - **Asyncio** (Asynchronous Input Output) - It gives **NodeJS** access to our system internal structure (file System, Networking etc.)
  - **Event Loop** - Heart of **NodeJS** architecture
  - **Thread Pool** - Provides 4(or more when configured) additional threads separate from the main thread, which is generally used for heavy tasks in the application.

- To set no. of threads in **Thread Pool**, We use `process.env.UV_THREADPOOL_SIZE`.

- **Synchronous** Code never runs in event loop, that's why it is avoided in NodeJS to prevent blocking of code execution.

- Along with **V8 Engine(Developed using JS & C++)** & **libuv**, **NodeJS** also depends on **http-parser, c-ares(for DNS Lookup), OpenSSL(For cryptograhpy), zlib(For File Compression)**

- **I/O Polling & Callbacks** - Things like networking, file access etc.

- **NodeJS** follows the **Event Driven Architecture** which is based on **Observer Pattern**. When an event is emitted then **event listener(event observer)** will catch up the event & run callback function.

- We can have more than one **event observer** for same event.

- Concept of **Video Streaming** is based on `Streams`.

- **Readable Stream** in **NodeJS** emits `data` event, which we can use to write `response` as **Writeable Stream**. Other events are `end` & `error`.

- Hitting `Tab` in **Node REPL**, will return all the _global variables_ available in **node**.

- Hitting `Tab` after mentioning a **construtor** will result all the methods associated with the prototype of that **constructor**.

- There are things like reading file system,writing in files etc. which we can do using **nodejs** which is not possible in **browser** and `fs` module is used for this purpose.

## fs module (built-in)

- There are various methods provided by the module which we can utilize to read,write,open,rename etc with a file.

#### Synchronous Operations

- **readFileSync()**
- **writeFileSync()**
- **renameSync()** >>> Rename a file and move into given path
- **unlinkSync()** >>> To delete a file permanently

#### Asynchronous Operations

- **readFile()**
- **writeFile()**
- **rename()**
- **unlink()**

**NOTE :-** We can use asynchronous methods of `fs module` either by passing callbacks (will cause callback hell) or by importing the methods from `fs/promises` & then using `async/await` duo.

## http Module (built-in)

- Used to create a development server.

- `createServer` method is used to create a server.

- There are built-in events like `request`, `close` etc. which are emitted by the `http` module itself, that's why we just have to use **event observers** for catching those events.

## url Module (built-in)

- Used for url reading.

## slugify Module (third)

- Used for url reading.

- slug is unique part of an url string

## nodemon Module (third)

- Used to restart server whenever any change is made in working directory.

## events Module (built-in)

- The module is used to emit custom events and then listen (observe) to those events for executing callbacks.

## crypto Module (built-in)

- Used for cryptographic operations like encrypting data, comparing encrypted data with original data etc.

## module Module (built-in)

- It gives the information about nodejs core modules

## superagent Module (third party)

- Used to make http request for fetching data.
- Along with callback, it also supports `promises`.

## Express Module (third party)

- a third party module to develop node application with easier syntaxes.

- Automatically figures out `Content-Type` while making request.

- While making **POST** request for sending data to the server, we have to use **Middleware** (in **express**) to get the payload data.

- `express.json()` **Middleware** parses incoming requests with JSON Payloads and based on `body-parse`.

- **Middleware** is just a function which modify(process) the data during **REQUEST RESPONSE CYCLE** and it is called so because of being in between `request` and `response`.

- Everything in **Express** is **Middleware**, even the route handler functions (callback functions).

- All the **Middlewares** together are called, **Middleware Stack.**

- In **Middleware** functions we have access to `next()` function and the last **Middleware** in the **Middleware Stack** is route handler, which does not need `next()`.

- Request and Response objects go through each and every **Middleware** in the **Middleware Stack** for processing and the whole process is like a **Pipeline**.

- **Status Code** 201 denotes that something has been created.

- **Dynamic route** is created using **:(variable name)**. For example - `/api/v1/tours/:id`

- `request.params`returns an object which contains all the variables used in **dynamic route**.

- Using **?** symbol in front of an variable in the given route, will make it optional. For Example - `/api/v1/tours/:id?`

- After receiving a request from client **Express** creates a request object & a response object.

- We can chain multiple routes together using `app.route()`.

- We can create our own **Middleware** functions.

- We need to call `next()` in **Custom Middleware** to avoid stucking of **Request Response Cycle**.

- To make a **Custom Middleware** available to all the routes, we have to define it before all the routes otherwise **Request Response Cycle** will ignore the **Middleware** for those routes which are declared before the **Middleware**.

- We can also use **3rd Party Middleware** to make coding rapid.

- **Express** stores all the **Middleware** functions in an array (**Middleware Stack**). The process of adding **Middleware** functions and optional path to the array, is known as **Mounting**.

- **Mounting a Router** means creating separate routers for separate resources and then use them as **Middlewares**. These Separate Routers are sometimes also called **mini apps** because they have their own routes.

```bash
const tourRouter = express.Router();
tourRouter.route('/').get(getAllTours);

app.use('/api/v1/tours', tourRouter);
```

- `express.Router()` is used to separate the **routes** in separate files. It appears like a mini-application inside an application.

- **PARAM MIDDLEWARE** is the **MIDDLEWARE** which triggers its callbak(Param callback) only for a certain parameter and it is used for the router's route which have the parameter(placeholder).

- Param callback functions are local to the router on which they are defined. They are not inherited by **mounted apps or routers**. Hence, param callbacks defined on router will be triggered only by route parameters defined on router routes.

- We can chain multiple **Middleware** functions with any route.

- **Static Files** are the files (such as **html, css, images & js files**) which are not directly accessed by **Routes** and we have to use **Built-in Express Middleware** `express.static(<folder name>)` to access them.

- **node** first looks for the route for the requested url then it goes for folder mentioned in `express.static()` **Middleware** from where **Static Files** are served and then it serves the file if it is in the folder.

- By default **Express** sets the environment as **Development**. To check the environment, we use `app.get('env')`.

- **Environment Variables** are global variables by used by **node applications** or any other applications (like flask applications etc.) while running.

- **NodeJS** sets a lot of **Environment Variables** ,which can be accessed using `process.env` and `process.env` comes from **built-in process module**.

- There is a special variable known as **NODE_ENV**, which is used by many packages in **Express** but **Express** does not define this variable, So you have to set it manually.

- **Environment Variables** for an app (node/flask/django) are set in `.env` or `config.env` file and they are accessed using a third party **dotenv**.

## morgan Module (3rd Party)

- A **Middleware** used for _http request logging._

- It gives access to `morgan()` function which takes two arguments **format** and **options**.

- **format** - dev, common, combined, short, tiny

## Mongoose Module (3rd Party)

- A **MongoDB** driver to connect NodeJS Applications with **MongoDB**

- It is an **ODM(Object Documents Mapping)** for NodeJS.

- Here We have the concept of **Schema** & **Model**. **Schema** is converted to **Collections** and **Model** is converted to **Documents** by **Mongoose**.

- **Schema** is defined as a new object with all the values as **Schema Type**. value can also be **Schema Type Options**.

- **MODEL** is created using **Schema**, which is used as blueprint to create new documents.

- There are following ways to create new documents from a **MODEL**:-

```bash
const Tour = new mongoose.model('tour', <schema>);

// Using save() method - it is a prototype method
const newTour = new Tour({<key> : <value>});
await newTour.save();

// Using create() method - It is directly associated with the Model
await Tour.create(<object>);

// To create multiple documents we can use insertMany() method
await Tour.insertMany();
```

- SchemaType **Array** is special because it implicitly has a default value of **[] (empty array)** and to overwrite this default value, set `default : undefined`.

-

### Routing

- It is the path (url) through which user visit different pages of a website.

### APIs

- Service from which we can retrieve data.

- `__dirname` is used to retrieve current working directory.

- **API** is used to send data to browser in `JSON` format and then website which request the data, consumes it.

- **REST** - Representational State Transfer (An architecture followed to build APIs).

- **REST APIS** are also known as **RESTful APIS**.

- `PUT` and `PATCH` methods are used to update resources of an api. `PUT` is used to update whole the resources whereas `PATCH` is used to update a part of the resources.

- There are many **Response Formatting** which are used to send **JSON** data from an API call and **JSend** is simplest in all of them.

## General Terms

- **Streaming data** can cause _back pressure_ when data going on is not as fast as data coming. To avoid such situation, we need to use any tool to control coming data. In **NodeJS**, we use `pipe()` method for this which comes with every `Readable Stream`.

- _back pressure_ can cause data loss/power exhaustation.

- **NodeJS** uses **Common JS** System to get access of functions/objects/other variables from a module.

- If a module(JS File) is run directly then `require.main === module` will return `true` otherwise it will be `false`.

- `module` object has a property `filename`(equivalent to `__filename`) which can be used to obtain entry point of the current application.

- In **Common JS** System, We use either `module.exports` or `exports` to export codes.

- Using `exports`, we can directly assign variables as properties to `exports` object which can be imported in another module using either **destructuring** or **exports object** assigned to a variable.

- When `exports` object is used to export from a module then importing in another module will give us access to `exports` object and hence all the properties associated with it.

##### Module from which we export

```bash
exports.ageCalculator = year => new Date().getFullYear() - year;
```

##### Module where we import the first module

```bash
const calcModule = require('<moduleName>');
calcModule.ageCalculator(1995);

const { ageCalculator } = require("<moduleName>");
ageCalculator(1997);
```

- `caching` in module imports caches the module and it has to **require** the module only once.

- To avoid callbacks hell which is created by using multiple callbacks one inside another, we use **Promises**.

- While making http request to **DELETE** data the response is **204**, which means no data.

### Promise

- The function passed in a `Promise` constructor is known as **executer function** which takes two parameters `resolve` or `reject` (both are functions).
- `Promise` always settles (resolve/reject) until there is any **Internal Server Error**.

- There is a function in **NodeJS** which automatically promisify any function
- One `.catch()` is enough to handle error for multiple `.then()` methods.

- `async/await` makes our code more readable by avoiding multiple `.then()`.

- We can have multiple `await` inside a function marked as asynchronous using the `async` keyword.

- function marked as `async` always returns a `promise` & to consume it, we use `.then()` & `.catch()`(If any error occurs).

- `Promise.all()` takes an array of multiple promises and waits for all of them to get **settled(fulfilled or rejected)** and then returns the **settled** values.

## MonogDB

- **NOSQL** database

- **Collections** - Similar to tables

- **Documents** - Similar to **rows** in SQL (Maximum Size of each **Document** is **16MB**)

- It uses **BSON (Binary JavaScript Object Notation)** data format to store data.

- Data are stored in **key/value pair** similar to JSON.

- **MongoDB** is very flexible which means **Documents** inside the **Collections** can have different fields.

- **db.myCol.find()** - Returns all the documents in the collections.

- **db.myCol.findOne()** - Returns the one document which matches the given condition.

- **db.myCol.insertOne()**

- **db.myCol.insertMany()**

- **db.myCol.updateOne()**

- **db.myCol.updateMany()**

- **db.myCol.replaceOne()**

- **db.myCol.replaceMany()**

- **db.myCol.deleteMany()**

- **db.myCol.deleteOne()**

- **db.version()**

- **Cluster** is like a container in **Mongodb**, which contains multiple databases.

- **db.dropDatabase()** - To drop current database in use.

- **db.getName()** - To get the name of current database in use.

- There are various operators used in **MongoDB** to filter documents:-

  1. **$lte** - It is used to query the documents where value of the field is **<=** of a specified value.

     - **Syntax** - `{field: { $lte: value}}`

  2. **$gte** - Used to query the documents where value of the field is **>=** of a specified value.

     - **Syntax** - `{field: { $gte: value}}`

  3. **$lt** - Used to query the documents where value of the field is **<** of a specified value.

     - **Syntax** - `{field : {$lt : value}}`

  4. **$gt** - Used to query the documents where value of the field is **>** of a specified value.

     - **Syntax** - `{field : {$gt : value}}`

  5. **$or** - Used to query documents based on any of the conditions passed in an array is satisfied.

     - **Syntax** - `{$or : [<condition1>, <condition2>, ...]}`

  6. **$set** - Used to set(replace) value of a field in a document or create a new field.

     - **Syntax** - `{$set: { <field1>: <value1>, ... }}`

  7. **$ne** - Used to query documents which are not equal to given value.

     - **Syntax** - `{field : {$ne : value}}`

  8. **$in** - Used to query documents where mentioned field has the any of the values specified in an array using the `in` operator.

     - **Syntax** - `{field : {$in : [<value1>, <value2>]}}`

  9. **$nin** - negation of `in` operator.

     - **Syntax** - `{field : {$nin : [<value1>, <value2>]}}`

### MVC Structure

- **MVC** - Model, View, Controller

- Every Backend development follows **MVC STRUCTURE**.

- **MODEL** - This layer is concerned with application data and it is called **Business Logic**.

- **VIEW** - It is responsible for handling requests, interacting with **MODEL** Layer & sending responses, all these are called **APPLICATION LOGIC**

- **CONTROLLER** - It is concerned with **Graphical Interface** and responsible for server-side rendering of templates, also known as **PRESENTATION LOGIC**.

- In API building, you don't have to worry about **VIEW** LAYER.
