# Callback Function

> **Module:** 17 - JavaScript Fundamentals  
> **Class:** 05/10  
> **Topic:** Callback Function

---

# 📚 What I Learned Today

- What is a Callback Function?
- Why do we use Callback Functions?
- Passing a Function as an Argument
- Reusable Code using Callbacks
- Anonymous Callback
- Arrow Function Callback
- Synchronous vs Asynchronous Callback
- Real-life Examples
- Common Mistakes
- Interview Questions

---

# What is a Callback Function?

## Definition

**A Callback Function is a function that is passed as an argument to another function and is executed later.**

> **বাংলা:** Callback Function হলো এমন একটি Function যেটিকে অন্য একটি Function-এর Argument হিসেবে পাঠানো হয় এবং প্রয়োজন হলে পরে Call করা হয়।

---

# Why is it Called "Callback"?

প্রথম Function বলে—

> "এখন আমার কাজ শেষ হলে আমি তোমাকে আবার Call করব।"

এই "Call Back Later" থেকেই নাম এসেছে **Callback Function**।

---

# Basic Syntax

```js
function first(callback) {
  callback();
}

function second() {
  console.log("Hello");
}

first(second);
```

---

# Simple Example

```js
function greet(name) {
  console.log("Hello", name);
}

function processUser(callback) {
  const user = "Rakib";

  callback(user);
}

processUser(greet);
```

### Output

```text
Hello Rakib
```

---

# Callback with Data

```js
function registerStudent(callback) {

  console.log("Registering Student...");

  callback();

}

function userBasicInfo() {

  console.log("Name: Rakib");
  console.log("Age: 20");

}

registerStudent(userBasicInfo);
```

### Output

```text
Registering Student...
Name: Rakib
Age: 20
```

---

# Callback Receives Parameters

```js
function processUser(name, callback) {

  console.log("Processing...");

  callback(name);

}

function welcome(user) {

  console.log(`Welcome ${user}`);

}

processUser("Rakib", welcome);
```

### Output

```text
Processing...

Welcome Rakib
```

---

# Same Function, Different Work

```js
function processUser(name, callback) {

  callback(name);

}

function sendWelcome(name) {

  console.log("Welcome", name);

}

function sendReminder(name) {

  console.log("Reminder Sent To", name);

}

processUser("Rakib", sendWelcome);

processUser("Rakib", sendReminder);
```

### Output

```text
Welcome Rakib

Reminder Sent To Rakib
```

### Explanation

একই `processUser()` Function ব্যবহার করে আলাদা Callback পাঠিয়ে ভিন্ন ভিন্ন কাজ করা যাচ্ছে।

এটাই Callback-এর সবচেয়ে বড় সুবিধা।

---

# Calculator Example

```js
function calculator(a, b, operation) {

  return operation(a, b);

}

function add(x, y) {

  return x + y;

}

console.log(calculator(10, 20, add));
```

### Output

```text
30
```

---

# Multiply Example

```js
function multiply(x, y) {

  return x * y;

}

console.log(calculator(10, 20, multiply));
```

### Output

```text
200
```

---

# Anonymous Callback

```js
function sayHello(callback) {

  callback();

}

sayHello(function () {

  console.log("Hello JavaScript");

});
```

---

# Arrow Function Callback

```js
function sayHello(callback) {

  callback();

}

sayHello(() => {

  console.log("Hello Callback");

});
```

---

# Callback Inside Array Methods

```js
const numbers = [10, 20, 30];

numbers.forEach(function (number) {

  console.log(number);

});
```

### Output

```text
10

20

30
```

---

# map() Uses Callback

```js
const numbers = [1, 2, 3];

const square = numbers.map(function (number) {

  return number * number;

});

console.log(square);
```

### Output

```text
[1, 4, 9]
```

---

# filter() Uses Callback

```js
const numbers = [10, 15, 20, 25];

const even = numbers.filter(function (number) {

  return number % 2 === 0;

});

console.log(even);
```

### Output

```text
[10, 20]
```

---

# Callback with setTimeout()

```js
setTimeout(function () {

  console.log("Executed After 2 Seconds");

}, 2000);
```

এখানে `function(){}` হলো Callback Function।

---

# Real-life Analogy

ধরো তুমি Pizza Order করলে।

```text
Customer

↓

Order

↓

Restaurant Cooking

↓

Ready হলে তোমাকে ফোন করবে
```

এই "পরে ফোন করা" কাজটাই Callback-এর মতো।

---

# Why Do We Use Callback?

- Code Reuse করা যায়।
- Flexible Programming করা যায়।
- একই Function দিয়ে বিভিন্ন কাজ করা যায়।
- Event Handle করা যায়।
- Async Programming করা যায়।

---

# Synchronous Callback

```js
function hello(callback) {

  callback();

}

hello(() => console.log("Hi"));
```

সাথে সাথে Execute হয়।

---

# Asynchronous Callback

```js
setTimeout(() => {

  console.log("After 3 Seconds");

}, 3000);
```

পরে Execute হয়।

---

# Synchronous vs Asynchronous Callback

| Synchronous Callback | Asynchronous Callback |
|-----------------------|----------------------|
| সাথে সাথে Execute হয় | পরে Execute হয় |
| অপেক্ষা করে না | নির্দিষ্ট সময় পরে Run হয় |
| Example: `forEach()` | Example: `setTimeout()` |

---

# Callback Flow

```text
Main Function

↓

Callback Function পাঠানো হলো

↓

Main Function কাজ করলো

↓

প্রয়োজন হলে Callback Execute করলো
```

---

# Advantages

- Reusable Code
- Flexible Logic
- Dynamic Behavior
- Event Handling
- Async Programming

---

# Disadvantages

- Nested Callback লিখলে Callback Hell হতে পারে।
- Debug করা কঠিন হতে পারে।
- Code Readability কমে যেতে পারে।

---

# Callback Hell

```js
first(function () {

  second(function () {

    third(function () {

      fourth(function () {

        console.log("Done");

      });

    });

  });

});
```

একে Callback Hell বা Pyramid of Doom বলা হয়।

---

# Common Mistakes

## ❌ Function Call করে পাঠানো

```js
processUser(greet());
```

ভুল।

---

## ✅ Function Reference পাঠানো

```js
processUser(greet);
```

সঠিক।

---

## ❌ Callback Return না বোঝা

```js
calculator(10, 20, add());
```

ভুল।

---

## ✅

```js
calculator(10, 20, add);
```

---

# Interview Questions

## Q1. What is a Callback Function?

একটি Function যেটি অন্য Function-এর Argument হিসেবে পাঠানো হয় এবং পরে Execute হয়।

---

## Q2. Why do we use Callback?

- Reusable Code
- Async Programming
- Event Handling
- Flexible Logic

---

## Q3. What is Callback Hell?

অনেক Nested Callback একসাথে লিখলে যে Pyramid Shape তৈরি হয় তাকে Callback Hell বলে।

---

## Q4. Difference between Function Call and Function Reference?

```js
hello();
```

Function Call

```js
hello
```

Function Reference

---

## Q5. Name some JavaScript methods that use Callback Functions.

- map()
- filter()
- reduce()
- forEach()
- find()
- some()
- every()
- sort()
- setTimeout()
- setInterval()

---

# Memory Trick

```text
Callback

=

Function

Passed

As

Argument
```

মনে রাখো—

> **"Function পাঠাও, পরে Call হবে।"**

---

# One Minute Revision

- Callback Function অন্য Function-এর Argument হয়।
- Callback পরে Execute হয়।
- Function Call নয়, Function Reference পাঠাতে হয়।
- `map()`, `filter()`, `forEach()`, `setTimeout()`—সব Callback ব্যবহার করে।
- Callback Hell এড়াতে Promise এবং Async/Await ব্যবহার করা হয়।

---

# Keywords

- Callback
- Function Reference
- Function Argument
- Anonymous Function
- Arrow Function
- Higher Order Function
- Event Handler
- setTimeout
- Asynchronous
- Callback Hell

---

# Practice Tasks

### Task 1

একটি `calculator()` Function লিখো যেখানে `add()`, `subtract()`, `multiply()` Callback হিসেবে কাজ করবে।

---

### Task 2

একটি `processOrder()` Function লিখো যেখানে `sendSMS()` Callback হবে।

---

### Task 3

`setTimeout()` ব্যবহার করে ৩ সেকেন্ড পরে `"Hello World"` Print করো।

---

### Task 4

`forEach()` ব্যবহার করে একটি Array-এর সব Element Print করো।

---

### Task 5

`map()` ব্যবহার করে একটি Array-এর সব Number Square করো।

---

### Task 6

`filter()` ব্যবহার করে একটি Array থেকে সব Even Number বের করো।

---

# More Callback Examples

## Example 1: Login System

```js
function login(username, callback) {
  console.log(`${username} logged in.`);
  callback(username);
}

function showDashboard(user) {
  console.log(`Welcome ${user}`);
}

login("Rakib", showDashboard);
```

---

## Example 2: Payment System

```js
function makePayment(amount, callback) {
  console.log("Payment Successful");
  callback(amount);
}

makePayment(500, function (amount) {
  console.log(`Invoice Created for ${amount} TK`);
});
```

---

## Example 3: Download File

```js
function downloadFile(callback) {
  console.log("Downloading...");
  callback();
}

downloadFile(() => {
  console.log("Download Complete");
});
```

---

## Example 4: Event Listener

```js
button.addEventListener("click", function () {
  console.log("Button Clicked");
});
```

---

## Example 5: Custom Greeting

```js
function greet(name, callback) {
  callback(name);
}

greet("Rakib", (user) => {
  console.log(`Good Morning ${user}`);
});
```

---

# Mentor Notes

- Callback JavaScript-এর Functional Programming-এর ভিত্তি।
- Callback ভালোভাবে বুঝতে পারলে Promise, Async/Await এবং Fetch API শেখা অনেক সহজ হবে।
- Interview-তে Callback Function, Callback Hell এবং Function Reference বনাম Function Call—এই তিনটি প্রশ্ন খুবই সাধারণ।