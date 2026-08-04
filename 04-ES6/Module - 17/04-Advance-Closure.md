# Advanced Closure

> **Module:** 17 - JavaScript Fundamentals  
> **Class:** 04/10  
> **Topic:** Advance Closure

---

# 📚 What I Learned Today

- What is Closure?
- Lexical Scope
- How Closure Works
- Counter Example
- Private Variables
- Cash Register Example
- Real-life Analogy
- Practical Uses of Closure
- Memory & Garbage Collection
- Interview Questions

---

# What is Closure?

## Definition

**Closure is a feature in JavaScript where an inner function remembers and can access variables from its outer function even after the outer function has finished executing.**

> **বাংলা:** Closure হলো JavaScript-এর এমন একটি Feature যেখানে একটি Inner Function তার Outer Function-এর Variable মনে রাখতে পারে এবং Outer Function শেষ হয়ে যাওয়ার পরেও সেই Variable ব্যবহার করতে পারে।

---

# Why Do We Need Closure?

Closure আমাদের সাহায্য করে—

- Private Variable তৈরি করতে
- Data Hide করতে
- State সংরক্ষণ করতে
- Counter বানাতে
- Event Handler লিখতে
- Callback Function ব্যবহার করতে
- Module Pattern তৈরি করতে

---

# How Closure Works

```js
function outer() {
  let message = "Hello";

  return function inner() {
    console.log(message);
  };
}

const greet = outer();
greet();
```

### Output

```text
Hello
```

### Explanation

1. `outer()` Call হলো।
2. `message` Variable তৈরি হলো।
3. `inner()` Return হলো।
4. `outer()` Execute শেষ হলো।
5. কিন্তু `message` Delete হলো না।
6. কারণ `inner()` এখনও `message`-এর Reference ধরে রেখেছে।

---

# Counter Example

```js
function createCounter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();

console.log(counter());
console.log(counter());
console.log(counter());
```

### Output

```text
1
2
3
```

### Explanation

প্রতিবার Function Call করার পরও `count` Reset হয় না।

কারণ Closure `count` Variable-কে Memory-তে ধরে রাখে।

---

# Private Variable

Closure ব্যবহার করে Variable Private রাখা যায়।

```js
function createCounter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();

console.log(count);
```

### Output

```text
ReferenceError
```

### কেন?

কারণ `count` শুধুমাত্র `createCounter()` Function-এর ভিতরে আছে।

---

# Cash Register Example

```js
function cashRegister() {
  let amount = 0;

  return function (payableAmount) {
    amount += payableAmount;
    return amount;
  };
}

const coffeeShop = cashRegister();

console.log(coffeeShop(200));
console.log(coffeeShop(100));
console.log(coffeeShop(300));
```

### Output

```text
200
300
600
```

---

# Multiple Closures

```js
const shopA = cashRegister();
const shopB = cashRegister();

shopA(100);
shopA(200);

shopB(500);
```

### Explanation

- `shopA` নিজের Memory ব্যবহার করবে।
- `shopB` নিজের Memory ব্যবহার করবে।
- একজনের Data আরেকজনের সাথে Share হবে না।

---

# Lexical Scope

Lexical Scope নির্ধারণ করে—

**কোন Function কোন Variable Access করতে পারবে।**

```js
function outer() {
  let x = 10;

  function inner() {
    console.log(x);
  }

  inner();
}
```

### Output

```text
10
```

কারণ `inner()` তার Outer Scope দেখতে পারে।

---

# Scope Rule

✅ Inner Function Outer Variable Access করতে পারে।

```text
Outer
   │
   ▼
Inner
```

❌ Outer Function Inner Variable Access করতে পারে না।

---

# Real-Life Analogy (Locker Example)

| Real Life | JavaScript |
|-----------|------------|
| Locker | Outer Function |
| Locker-এর টাকা | Private Variable |
| চাবি | Inner Function |
| দরজা বন্ধ | Outer Function শেষ |
| চাবি দিয়ে আবার খোলা | Closure |

---

# Closure = 3 Things

```text
Closure
=
Function
+
Lexical Scope
+
Remembered Variables
```

---

# Memory Behavior

Normally—

Function শেষ হলে Variable Garbage Collector Remove করে।

কিন্তু—

যদি কোনো Closure সেই Variable ব্যবহার করে,

তাহলে Variable Memory-তে থেকে যায়।

---

# Real-Life Uses of Closure

## 1. Counter

```js
let counter = createCounter();
```

---

## 2. Data Privacy

Private Variable তৈরি করা।

---

## 3. Function Factory

একই Logic থেকে অনেক Function তৈরি করা।

---

## 4. Event Handler

```js
button.addEventListener("click", function () {});
```

---

## 5. Callback

```js
setTimeout(() => {
  console.log("Done");
}, 1000);
```

---

## 6. Module Pattern

একটি File-এর Private State সংরক্ষণ করতে।

---

# Advantages of Closure

- Data Hide করা যায়।
- Private Variable তৈরি করা যায়।
- State সংরক্ষণ করা যায়।
- Memory Efficient Code লেখা যায়।
- Reusable Function তৈরি করা যায়।

---

# Disadvantages of Closure

- বেশি ব্যবহার করলে Memory বেশি দখল করতে পারে।
- ভুলভাবে Reference ধরে রাখলে Memory Leak হতে পারে।
- নতুনদের জন্য বুঝতে কঠিন।

---

# Comparison

| Normal Function | Closure |
|-----------------|----------|
| Variable Delete হয়ে যায় | Variable Memory-তে থাকে |
| State মনে রাখে না | State মনে রাখে |
| Private Data নেই | Private Data থাকে |
| Simple Function | Stateful Function |

---

# Common Mistakes

## ❌ Mistake 1

```js
console.log(count);
```

Private Variable বাইরে Access করা।

---

## ❌ Mistake 2

ধারণা করা—

Function শেষ মানেই সব Variable Delete।

---

## ❌ Mistake 3

Closure মানে শুধু Nested Function ভাবা।

আসলে—

```text
Nested Function
+
Lexical Scope
+
Reference
=
Closure
```

---

# Interview Questions

## Q1. What is Closure?

Closure হলো এমন একটি Function যা Outer Function শেষ হওয়ার পরেও তার Variable Access করতে পারে।

---

## Q2. Why is Closure useful?

- Private Variable
- State Management
- Callback
- Event Handler
- Module Pattern

---

## Q3. What is the relationship between Closure and Lexical Scope?

Closure, Lexical Scope-এর উপর ভিত্তি করে কাজ করে।

---

## Q4. Can Closure cause Memory Leak?

হ্যাঁ।

যদি অপ্রয়োজনীয় Object বা DOM Reference দীর্ঘ সময় ধরে Closure ধরে রাখে, তাহলে Memory Leak হতে পারে।

---

## Q5. How can you create a Private Variable using Closure?

Outer Function-এর ভিতরে Variable রেখে Inner Function Return করলে Variable Private থাকে।

---

# Memory Trick

```text
Closure

=

Function

+

Lexical Scope

+

Remembered Variables
```

অথবা

```text
Function Ends

≠

Memory Ends
```

যদি Closure থাকে,

Memory বেঁচে থাকে।

---

# One Minute Revision

- Closure Variable মনে রাখে।
- Outer Function শেষ হলেও Variable Delete হয় না।
- Inner Function Outer Variable Access করতে পারে।
- Closure দিয়ে Private Variable তৈরি করা যায়।
- Counter, Event Handler, Callback, Module Pattern-এ Closure ব্যবহৃত হয়।

---

# Keywords

- Closure
- Lexical Scope
- Scope Chain
- Outer Function
- Inner Function
- Counter
- Private Variable
- Callback
- Event Handler
- Module Pattern
- Garbage Collection
- Memory
- Reference

---

# Practice Tasks

### Task 1

`createCounter()` Function লিখো যা প্রতিবার Call করলে সংখ্যা ১ করে বাড়াবে।

---

### Task 2

`createBankAccount()` Function লিখো যেখানে—

- `deposit()`
- `withdraw()`
- `getBalance()`

থাকবে এবং `balance` Private থাকবে।

---

### Task 3

`createGreeting(name)` Function লিখো যা Return করা Function Call করলে `"Hello, <name>"` Print করবে।

---

### Task 4

`createMultiplier(x)` Function লিখো যা Return করা Function-এর Number-কে `x` দিয়ে Multiply করবে।

---

### Task 5

একই Factory Function থেকে দুটি আলাদা Counter তৈরি করে দেখাও যে তারা আলাদা Memory ব্যবহার করে।

---

# Mentor Notes

- Closure JavaScript-এর সবচেয়ে গুরুত্বপূর্ণ Core Concepts-এর একটি।
- React-এর `useState`, `useEffect`, Event Handler এবং Callback বুঝতে Closure জানা বাধ্যতামূলক।
- `createCounter()` এবং `cashRegister()` উদাহরণ অন্তত ৫–১০ বার নিজে লিখে Practice করো।
- যদি Closure পরিষ্কারভাবে বুঝতে পারো, তাহলে React, Node.js এবং Async JavaScript শেখা অনেক সহজ হয়ে যাবে।



---

# More Closure Examples

## Example 1: Simple Counter

```js
function createCounter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();

console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

### Explanation

- `count` Private Variable।
- বাইরে থেকে Access করা যায় না।
- প্রতিবার Call করলে আগের Value মনে রাখে।

---

## Example 2: Greeting Function

```js
function createGreeting(name) {
  return function () {
    console.log(`Hello ${name}`);
  };
}

const greetRakib = createGreeting("Rakib");

greetRakib();
```

### Output

```text
Hello Rakib
```

---

## Example 3: Bank Account

```js
function createBankAccount() {
  let balance = 0;

  return {
    deposit(amount) {
      balance += amount;
    },

    withdraw(amount) {
      balance -= amount;
    },

    getBalance() {
      return balance;
    },
  };
}

const account = createBankAccount();

account.deposit(1000);
account.withdraw(300);

console.log(account.getBalance());
```

### Output

```text
700
```

### Why Closure?

`balance` Variable বাইরে থেকে Access করা যায় না।

---

## Example 4: Multiplier Factory

```js
function createMultiplier(number) {
  return function (value) {
    return value * number;
  };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

console.log(double(10));
console.log(triple(10));
```

### Output

```text
20
30
```

---

## Example 5: ID Generator

```js
function createIdGenerator() {
  let id = 0;

  return function () {
    id++;
    return id;
  };
}

const generateId = createIdGenerator();

console.log(generateId());
console.log(generateId());
console.log(generateId());
```

### Output

```text
1
2
3
```

---

## Example 6: setTimeout

```js
function delayedMessage(message) {
  setTimeout(function () {
    console.log(message);
  }, 2000);
}

delayedMessage("Hello JavaScript");
```

### Output (After 2 Seconds)

```text
Hello JavaScript
```

### Why?

`setTimeout()` Callback পরে Execute হলেও `message` Variable মনে রাখে।

---

## Example 7: Button Click Counter

```js
function clickCounter() {
  let clicks = 0;

  return function () {
    clicks++;
    console.log(clicks);
  };
}

const countClick = clickCounter();

countClick();
countClick();
countClick();
```

### Output

```text
1
2
3
```

---

## Example 8: Password Checker

```js
function createPassword(password) {
  return function (input) {
    return input === password;
  };
}

const checkPassword = createPassword("12345");

console.log(checkPassword("12345"));
console.log(checkPassword("abc"));
```

### Output

```text
true
false
```

---

## Example 9: Shopping Cart

```js
function createCart() {
  let total = 0;

  return function (price) {
    total += price;
    return total;
  };
}

const cart = createCart();

console.log(cart(200));
console.log(cart(500));
console.log(cart(300));
```

### Output

```text
200
700
1000
```

---

## Example 10: Function Factory

```js
function makePower(power) {
  return function (number) {
    return number ** power;
  };
}

const square = makePower(2);
const cube = makePower(3);

console.log(square(5));
console.log(cube(5));
```

### Output

```text
25
125
```