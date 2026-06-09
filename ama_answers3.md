# JavaScript Interview Questions & Answers

## 1. Why should we not use `var` in JavaScript?

**Answer:**
We generally avoid `var` because:

- It is **function-scoped**, not block-scoped.
- It can be **redeclared** accidentally.
- It gets **hoisted** and initialized with `undefined`, which can cause bugs.

Example:

```js
if (true) {
  var x = 10;
}
console.log(x); // 10
```

Here, `x` is accessible outside the block.

Using `let`:

```js
if (true) {
  let x = 10;
}
console.log(x); // Error
```

`let` and `const` are safer because they are block-scoped.

---

## 2. Difference between `for...of` and `for...in`

### `for...of`
Used to iterate over **values**.

```js
const arr = ["a", "b", "c"];

for (const value of arr) {
  console.log(value);
}
```

Output:

```text
a
b
c
```

### `for...in`
Used to iterate over **keys/indexes**.

```js
const arr = ["a", "b", "c"];

for (const key in arr) {
  console.log(key);
}
```

Output:

```text
0
1
2
```

| Feature | for...of | for...in |
|----------|----------|----------|
| Returns | Values | Keys/Indexes |
| Used for | Arrays, Strings, Iterables | Objects |
| Example Output | "a", "b", "c" | 0, 1, 2 |

---

## 3. What is a Promise in JavaScript?

**Answer:**

A Promise is an object that represents the eventual result of an asynchronous operation.

States:

1. Pending
2. Fulfilled
3. Rejected

Example:

```js
const promise = new Promise((resolve, reject) => {
  resolve("Success");
});

promise.then(result => {
  console.log(result);
});
```

Output:

```text
Success
```

---

## 4. What does `npm init --yes` do?

**Answer:**

It creates a `package.json` file with default values automatically.

```bash
npm init --yes
```

Equivalent to:

```bash
npm init -y
```

Without asking questions interactively.

---

## 5. Tell some Higher Order Functions

**Answer:**

A Higher Order Function is a function that:

- Takes another function as an argument, OR
- Returns a function.

Common examples:

```js
map()
filter()
reduce()
forEach()
sort()
```

Example:

```js
const nums = [1, 2, 3];

const doubled = nums.map(num => num * 2);

console.log(doubled);
```

Output:

```text
[2, 4, 6]
```

---

## 6. How to include a JavaScript file in HTML?

**Answer:**

Using the `<script>` tag.

```html
<script src="script.js"></script>
```

Usually placed before the closing `</body>` tag.

```html
<body>
  <script src="script.js"></script>
</body>
```

---

## 7. What is the `this` keyword?

**Answer:**

`this` refers to the object that is currently executing the function.

Example:

```js
const person = {
  name: "Nova",
  greet() {
    console.log(this.name);
  }
};

person.greet();
```

Output:

```text
Nova
```

Here, `this` refers to the `person` object.

---

## 8. What is the type of `NaN`?

**Answer:**

```js
console.log(typeof NaN);
```

Output:

```text
number
```

Although `NaN` means "Not a Number", its type is actually `number`.

---

## 9. What happens if we don't return anything from a function and print its value?

**Answer:**

JavaScript automatically returns `undefined`.

Example:

```js
function greet() {
  console.log("Hello");
}

const result = greet();

console.log(result);
```

Output:

```text
Hello
undefined
```

---

## 10. What is a Function Expression?

**Answer:**

A function assigned to a variable is called a function expression.

```js
const greet = function () {
  console.log("Hello");
};

greet();
```

Difference:

```js
// Function Declaration
function greet() {}
```

```js
// Function Expression
const greet = function () {};
```

Function expressions are not fully hoisted.

---

## 11. Which module is needed to perform file operations?

**Answer:**

Node.js uses the built-in `fs` module.

```js
const fs = require("fs");
```

Examples:

```js
fs.readFile();
fs.writeFile();
fs.appendFile();
fs.unlink();
```

---

## 12. Are Function Declarations hoisted?

**Answer:**

Yes, function declarations are completely hoisted.

Example:

```js
greet();

function greet() {
  console.log("Hello");
}
```

Output:

```text
Hello
```

Because the entire function is hoisted.

---

## 13. What are First Class Functions?

**Answer:**

In JavaScript, functions are treated like values.

They can:

- Be assigned to variables
- Be passed as arguments
- Be returned from functions

Example:

```js
const greet = function () {
  console.log("Hello");
};

function execute(fn) {
  fn();
}

execute(greet);
```

Output:

```text
Hello
```

---

## 14. What is Inversion of Control (IoC)?

**Answer:**

Inversion of Control means handing over control of execution to another piece of code.

Example:

```js
setTimeout(() => {
  console.log("Executed later");
}, 1000);
```

Here, JavaScript runtime decides when to execute the callback.

Promises help reduce issues caused by IoC (Callback Hell).

---

## 15.What is the use of `typeof`?

**Answer:**

`typeof` is used to check the data type of a value.

Examples:

```js
typeof 10;
```

Output:

```text
"number"
```

