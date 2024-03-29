# [NodeJS]()

- _REPL(Read-Eval-Print-Loop)_
- All the codes written inside a moudule is wrapped into a _REPL_ function as IIFE and paremeters like `exports`, `module`, `require`, `__filename` & `__dirname` are passed into it by JavaScript Runtime.
- `arguments` is an object(array like object) in JavaScript, which contains only `length` & `index` properties. Outside a function, It contains all the details about modules.

```js
console.log(arguments); // returns an object containing properties:- exports, module, require, __filename, __dirname
```

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

- Event loop executes tasks in `process.nextTick queue` first, and then executes `promises microtask queue`, and then executes `macrotask queue(setImmediate, setTimeout etc)`.

## Modules

- Some of the **built-in** modules are `node:fs`, `node:http`, `node:url`, `node:events`, `node:process`, `crypto`, `events`

> An **http header** is basically a piece of information sent as response for a request.

### slugify Module (third)

- Used for url reading.
- slug is unique part of an url string

### nodemon Module (third)

- Used to restart server whenever any change is made in working directory.

### events Module (built-in)

- The module is used to emit custom events and then listen (observe) to those events for executing callbacks.
- There is also some third party modules like `EventEmitter2` & `EventEmitter3` which are way more efficient than built-in `events` module.

### crypto Module (built-in)

- Used for cryptographic operations like encrypting data, comparing encrypted data with original data etc.

### module Module (built-in)

- It gives the information about nodejs core modules
- It contains a `wrapper` property which returns the **wrapper function** used to wrap a module.

### superagent Module (third party)

- Used to make http request for fetching data.
- Along with callback, it also supports `promises`.

### Express Module (third party)

- a third party module to develop node application with easier syntaxes.
- Automatically figures out `Content-Type` while making request.
- While making **POST** request for sending data to the server, we have to use **Middleware** to get the payload data.
- `express.json()` **Middleware** parses incoming requests with JSON Payloads and based on `body-parse`.

#### Middleware

- **Middleware** is just a function which has access to the `request` object, `response` object & next middleware function(**next**) during **REQUEST RESPONSE CYCLE**.
- Everything in **Express** is **Middleware**, even the route handler functions (callback functions).
- All the **Middlewares** together are called, **Middleware Stack.**
- In **Middleware** functions we have access to `next()` function and the last **Middleware** in the **Middleware Stack** is route handler, which does not need `next()`.
- Request and Response objects go through each and every **Middleware** in the **Middleware Stack** for processing and the whole process is like a **Pipeline**.

- Middleware functions can perform the following tasks:
  - Execute any code.
  - Make changes to the request and the response objects.
  - End the request-response cycle.
  - Call the next middleware function in the stack.
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

```js
const tourRouter = express.Router();
app.use("/api/v1/tours", tourRouter);

tourRouter.route("/").get(getAllTours);
```

- `express.Router()` is used to separate the **routes** in separate files. It appears like a mini-application inside an application.
- **PARAM MIDDLEWARE** is the **MIDDLEWARE** which triggers its callback(It takes `req`, `res`, `next` & `val` parameters) only for a certain parameter. and it is used for the router's route which have the parameter(placeholder).
- Param callback functions are local to the router on which they are defined. They are not inherited by **mounted apps or routers**. Hence, param callbacks defined on router will be triggered only by route parameters defined on router routes.
- We can chain multiple **Middleware** functions with any route.

```js
const checkProperties = (req, res, next) => {
  const tour = req.body;

  if (!(tour.place_name && tour.state && tour.country)) {
    return res.status(404).json({
      status: "fail",
      message: "place_name or state or country is missing"
    });
  }
  next();
};

router
  .route("/")
  .get(tourController.getAllTours)
  .post(checkProperties, tourController.createTour);
```

- **Static Files** are the files (such as **html, css, images & js files**) which are not directly accessed by **Routes** and we have to use **Built-in Express Middleware** `express.static('<folder name>')` to access them.
- **node** first looks for the route for the requested url then it goes for folder mentioned in `express.static()` **Middleware** from where **Static Files** are served and then it serves the file if it is in the folder.

- By default **Express** sets the environment as **Development**. To check the environment, we use `app.get('env')`.
- **Environment Variables** are global variables by used by **node applications** or any other applications (like flask applications etc.) while running.
- **NodeJS** sets a lot of **Environment Variables**, which can be accessed using `process.env`. `process.env` comes from **built-in process module**.
- There is a special variable known as **NODE_ENV**, which is used by many packages in **Express** but **Express** does not define this variable, So you have to set it manually.
- **Environment Variables** for an app (node/flask/django) are set in `.env` or `config.env` file and they are accessed using a third party **dotenv**.
- **Environment Variables** can be printed in CLI using `printenv` or `env` command.
- We can set the application environment in linux

```bash
> NODE_ENV=production nodemon server.js
```

### morgan Module (3rd Party)

- A **Middleware** used for _http request logging._
- It gives access to `morgan()` function which takes two arguments **format** and **options**.
- **format** - dev, common, combined, short, tiny

### Mongoose Module (3rd Party)

- A **MongoDB** driver to connect NodeJS Applications with **MongoDB**
- It is an **ODM(Object Documents Mapping)** for NodeJS.
- Here We have the concept of **Schema** & **Model**. **Schema** is converted to **Collections** and **Model** is converted to **Documents** by **Mongoose**.
- **Schema** is defined as a new object with all the values as **Schema Type**. value can also be **Schema Type Options**.
- **MODEL** is created using **Schema**, which is used as blueprint to create new documents.
- There are following ways to create new documents from a **MODEL**:-

```js
const Tour = new mongoose.model("tour", "<schema>");

// Using save() method - it is a prototype method
const newTour = new Tour({ "<key>": "<value>" });
await newTour.save();

// Using create() method - It is directly associated with the Model
await Tour.create("<object>");

// To create multiple documents we can use insertMany() method
await Tour.insertMany();
```

- SchemaType **Array** is special because it implicitly has a default value of **[] (empty array)** and to overwrite this default value, set `default : undefined`.

#### Routing

- It is the path (url) through which user visit different pages of a website.

#### APIs

- Service from which we can retrieve data.
- `__dirname` is used to retrieve current working directory.
- **API** is used to send data to browser in `JSON` format and then website which request the data, consumes it.
- **REST** - Representational State Transfer (An architecture followed to build APIs).
- **REST APIS** are also known as **RESTful APIS**.
- `PUT` and `PATCH` methods are used to update resources of an api. `PUT` is used to update whole the resources whereas `PATCH` is used to update a part of the resources.
- There are many **Response Formatting** which are used to send **JSON** data from an API call and **JSend** is simplest in all of them.

### General Terms

- **Streaming data** can cause _back pressure_ when data going on is not as fast as data coming. To avoid such situation, we need to use any tool to control coming data. In **NodeJS**, we use `pipe()` method for this which comes with every `Readable Stream`.
- _back pressure_ can cause data loss/power exhaustation.
- **NodeJS** uses **Common JS** System to get access of functions/objects/other variables from a module.
- If a module(JS File) is run directly then `require.main === module` will return `true` otherwise it will be `false`.
- `module` object has a property `filename`(equivalent to `__filename`) which can be used to obtain entry point of the current application.
- In **Common JS** System, We use either `module.exports` or `exports` to export codes.
- Using `exports`, we can directly assign variables as properties to `exports` object which can be imported in another module using either **destructuring** or **exports object** assigned to a variable.
- When `exports` object is used to export from a module then importing in another module will give us access to `exports` object and hence all the properties associated with it.

##### Module from which we export

```js
exports.ageCalculator = year => new Date().getFullYear() - year;
```

##### Module where we import the first module

```js
const calcModule = require("<moduleName>");
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

### MVC Structure

- **MVC** - Model, View, Controller
- Every Backend development follows **MVC STRUCTURE**.
- **MODEL** - This layer is concerned with application data and it is called **Business Logic**.
- **VIEW** - It is responsible for handling requests, interacting with **MODEL** Layer & sending responses, all these are called **APPLICATION LOGIC**
- **CONTROLLER** - It is concerned with **Graphical Interface** and responsible for server-side rendering of templates, also known as **PRESENTATION LOGIC**.
- In API building, you don't have to worry about **VIEW** LAYER.
