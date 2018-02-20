# Modern JavaScript

> Note for the course [Modern JavaScript](https://learn.tylermcginnis.com/courses/51206)

## var vs let vs const: Variable declarations in ES6 | ES2015

* 4 concepts:

  * declarations: create a new identifier

  * initialization: first assign a value to a variable

  * scope: one of [global, function, block(new)]

  * hoisting: JS will go to upper scope to find an undefined variable

* var

  * function scoped
  * undefined

* let

  * block scoped {}, including for loop or if statement before {}
  * reference error

* const
  * like let expect that it never change

## Object and Array Destructuring(解构) in JavaScript. ES6 | ES2015

```js
const tyler = {
  name: "Tyler McGinnis",
  location: "Eden, Utah"
};

// use : for renaming
let { name: who, location } = styler;

// usage:
// api can use this pattern too
function register (props) {
  var { onChangeEmail, email, onChangePassword, password, submit }  = props;
  return (
    <div>
      <span>Email:</span>
      <input type='text' onChange={onChangeEmail} value={email} />
      <span>Password:</span>
      <input type='text' onChange={onChangePassword} value={password} />
      <button onClick={submit}>Submit</button>
    </div>
  )

const csv = "1997,Ford, F350,Must Sell!!";
let [year, make, model, description] = csv.split(",");

// usage:
Promise.all([() => "profile", () => "repos"])
.then([profile, repos] => {
  return {
    profile,
    repo
  }
})
```

## Shorthand Property and Method Names in JavaScript ES6 | ES2015

```js
function formatMessage(name, id, avatar) {
  return {
    name,
    id,
    avatar,
    timestamp: Date.now(),
    save() {
      // save
    }
  };
}
```

## Computed Property Names in JavaScript | ES6 | ES2015

```js
function objectify(key, value) {
  return {
    [key]: value
  };
}
```

## Template Literals (Template Strings) in JavaScript | ES6 | ES2015

```js
function makeGreeting(name, email, id) {
  return `Hello, ${name}. We've emailed you at ${email}. Your user id is ${id}.`;
}

function makeTemplate(name, email, id) {
  return `
    <div>
      <title>${name}</title>
      <p>email</p>
    </div>
  `
```

## Arrow Functions in JavaScript | ES6 | ES2015

// Arrow function will use 'this' from where it was called
// TIP: "||" will let it run both of two expressions

```js
api.fetchRepos(lang).then(repos => {
  this.setState(
    () =>
      console.log("repos", repos) || {
        repos
      }
  );
});
```

## Default Parameters in JavaScript | ES6 | ES2015

```js
function isRequired(name) {
  throw new Error(name + "is required.");
}

// isRequired is an possible way to write validates
function calculatePayment(price = isRequired("price"), salesTax = 0.12) {
  // math
}
```

## Compiling vs Polyfills with Babel, from axios to fetch

Compiling: arrow function, destructuring...
Polyfills: fetch, includes

TIP: fetch is optional, axios is more comfortable

```js
// use Promise.all
// yarn add babel-polyfill
webpack.config.entry: ["babel-polyfill", "whatwg-fetch", ...]
```

## import, export

## Class Properties (Class Fields)

```js
class Demo {
  static propTypes = {};
  static defaultProps = {};
  state = {};
  handleChange = () => {};
}
```

## Async/Await in React(babel-polyfill)

> every async function you write will return a promise, and every single thing you await will ordinarily be a promise

```js
async function handleGetUser() {
  try {
    var user = await getUser();
    console.log(user);
  } catch (error) {
    console.log("Error in handleGetUser", error);
  }
}
```
