# Ama Questions & Answers

## 1. What happens when we declare a variable without `var`, `let`, or `const`?

```javascript
name = "Naresh";
```

If a variable is declared without `var`, `let`, or `const`, JavaScript creates it as a global variable (in non-strict mode).

Example:

```javascript
x = 10;
console.log(x); // 10
```

Problems:

* Pollutes the global scope.
* Can cause unexpected bugs.
* Not allowed in strict mode.

```javascript
"use strict";
x = 10; // Error
```

---

## 2. What is JSON?

JSON (JavaScript Object Notation) is a lightweight format used for storing and exchanging data between applications.

Example:

```json
{
  "name": "Naresh",
  "age": 22,
  "city": "Bangalore"
}
```

Features:

* Human-readable.
* Language-independent.
* Commonly used in APIs.

---

## 3. What does the DEFAULT constraint do in columns?

The DEFAULT constraint provides a default value when no value is supplied during insertion.

Example:

```sql
CREATE TABLE Employee (
    id INT,
    city VARCHAR(50) DEFAULT 'Bangalore'
);
```

```sql
INSERT INTO Employee(id) VALUES(1);
```

Output:

| id | city      |
| -- | --------- |
| 1  | Bangalore |

---

## 4. What is the use of Promises?

Promises handle asynchronous operations in JavaScript.

They represent:

* Pending
* Fulfilled
* Rejected

Example:

```javascript
const promise = new Promise((resolve, reject) => {
    resolve("Success");
});

promise.then(data => console.log(data));
```

Benefits:

* Avoid callback hell.
* Better readability.
* Easier error handling.

---

## 5. What does `.sort()` do in an array of numbers?

The `sort()` method sorts array elements.

Problem:

```javascript
let arr = [10, 5, 100, 25];
arr.sort();

console.log(arr);
```

Output:

```javascript
[10, 100, 25, 5]
```

Reason:
By default, sort converts values to strings.

Correct way:

```javascript
arr.sort((a, b) => a - b);
```

Output:

```javascript
[5, 10, 25, 100]
```

Descending:

```javascript
arr.sort((a, b) => b - a);
```

---

## 6. Real-life example where Toggle is used

Toggle means switching between two states.

Examples:

* Dark Mode ↔ Light Mode
* ON ↔ OFF switch
* Show Password ↔ Hide Password
* Mute ↔ Unmute

Example:

```javascript
button.addEventListener("click", () => {
    document.body.classList.toggle("dark");
});
```

---

## 7. What is an Endpoint?

An endpoint is a URL where a client sends requests to interact with a server.

Example:

```text
GET /users
POST /users
DELETE /users/1
```

Full URL:

```text
https://api.company.com/users
```

Here `/users` is the endpoint.

---

## 8. What does `JSON.parse()` do?

`JSON.parse()` converts a JSON string into a JavaScript object.

Example:

```javascript
const jsonString = '{"name":"Naresh","age":22}';

const obj = JSON.parse(jsonString);

console.log(obj.name);
```

Output:

```javascript
Naresh
```

---

## 9. How to remove elements using DOM?

### Remove an element

```javascript
const item = document.getElementById("item");
item.remove();
```

### Remove child element

```javascript
parent.removeChild(child);
```

Example:

```javascript
const ul = document.querySelector("ul");
const li = document.querySelector("li");

ul.removeChild(li);
```

---

## 10. Difference between Synchronous and Asynchronous

| Synchronous                 | Asynchronous                    |
| --------------------------- | ------------------------------- |
| Executes one task at a time | Does not wait for previous task |
| Blocking                    | Non-blocking                    |
| Slower for long operations  | Faster and efficient            |

Synchronous:

```javascript
console.log("A");
console.log("B");
console.log("C");
```

Output:

```text
A
B
C
```

Asynchronous:

```javascript
console.log("A");

setTimeout(() => {
    console.log("B");
}, 1000);

console.log("C");
```

Output:

```text
A
C
B
```

---

## 11. Types of Scoping in JavaScript

### Global Scope

Accessible everywhere.

```javascript
let name = "Naresh";
```

### Function Scope

Accessible only inside the function.

```javascript
function test() {
    var age = 22;
}
```

### Block Scope

Accessible only inside a block.

```javascript
{
    let city = "Bangalore";
}
```

`let` and `const` are block-scoped.

---

## 12. Difference between PUT and PATCH

| PUT                     | PATCH                   |
| ----------------------- | ----------------------- |
| Updates entire resource | Updates specific fields |
| Replaces existing data  | Partially modifies data |

PUT:

```http
PUT /users/1
```

```json
{
  "name":"Naresh",
  "age":22
}
```

Entire resource gets replaced.

PATCH:

```http
PATCH /users/1
```

```json
{
  "age":23
}
```

Only age gets updated.

---

## 13. What is the Event Loop?

The Event Loop is a mechanism that allows JavaScript to handle asynchronous operations even though it is single-threaded.

Working:

1. Execute Call Stack.
2. Async tasks go to Web APIs.
3. Callback enters Callback Queue.
4. Event Loop moves callback to Call Stack when stack becomes empty.

Example:

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Timer");
}, 0);

console.log("End");
```

Output:

```text
Start
End
Timer
```

Because the callback waits for the call stack to become empty.

---

## 14. How do we check the result of a request in Postman?

### Method 1: Response Body

After clicking **Send**, check:

```text
Response → Body
```

Example:

```json
{
  "message": "User Created Successfully"
}
```

### Method 2: Status Code

Check:

```text
200 OK
201 Created
400 Bad Request
404 Not Found
500 Internal Server Error
```

### Method 3: Headers

Open:

```text
Response → Headers
```

### Method 4: Response Time

Check:

```text
120 ms
```

to see how long the request took.

### Method 5: Tests Tab

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

Used for automated API validation.

