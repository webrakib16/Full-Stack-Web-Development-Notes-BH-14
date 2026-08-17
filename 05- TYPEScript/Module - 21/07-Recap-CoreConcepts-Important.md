# 📚 Module: 21 | 🎓 Class: 7

# Core Concepts in TypeScript

> **Topic:** Variable, Conditional, Loops, Array, Function, Array Function, Object, `toFixed()` & `map()`

---

# 📖 What I Learned Today

- Variable
- Conditional
- Loops
- `for...in`
- `for...of`
- Array
- Function
- Array Function
- Object
- `toFixed()`
- `map()`
- JavaScript vs TypeScript Core Concepts

---

# 📌 TypeScript Core Concepts

TypeScript-এর Core Concepts মূলত JavaScript-এর মতোই কাজ করে। প্রধান পার্থক্য হলো TypeScript-এ **Static Typing** ব্যবহার করে variable, parameter, return value, object এবং array-এর type নির্দিষ্ট করা যায়।

> **TypeScript = JavaScript + Static Type System**

---

# Part 1 — Variable

## 📌 Definition


A variable is a named container used to store data.

Variable হলো data রাখার জন্য একটি named container।

---

# JavaScript vs TypeScript

### JavaScript

```js
let age = 25;
let name = "Rakib";
```

### TypeScript

```ts
let age: number = 25;
let name: string = "Rakib";
```

### Difference

| JavaScript | TypeScript |
|---|---|
| Type explicitly define করা হয় না | Type explicitly define করা যায় |
| Dynamic Typing | Static Typing |
| `let age = 25` | `let age: number = 25` |

---

# Part 2 — Conditional

## 📌 Definition



Conditional statements execute different code depending on whether a condition is true or false.

Condition-এর উপর ভিত্তি করে কোন code execute হবে তা নির্ধারণ করতে Conditional ব্যবহার করা হয়।

---

# Example

### JavaScript

```js
let age = 20;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

### TypeScript

```ts
let age: number = 20;

if (age >= 18) {
    console.log("Adult");
} else {
    console.log("Minor");
}
```

> Conditional-এর মূল logic একই। TypeScript-এ variable-এর type define করা যায়।

---

# Part 3 — Loops

Loops ব্যবহার করে একই ধরনের কাজ বারবার করা হয়।

---

# `for...of`

## 📌 What is `for...of`?

`for...of` iterable data-এর **values** access করে।

### JavaScript

```js
const fruits = ["Apple", "Banana", "Mango"];

for (const fruit of fruits) {
    console.log(fruit);
}
```

### TypeScript

```ts
const fruits: string[] = ["Apple", "Banana", "Mango"];

for (const fruit of fruits) {
    console.log(fruit);
}
```

### Remember

```text
for...of → Value
```

---

# `for...in`

## 📌 What is `for...in`?

`for...in` object-এর **keys** অথবা array-এর **indexes** iterate করে।

### JavaScript

```js
const student = {
    name: "Rakib",
    age: 25
};

for (const key in student) {
    console.log(key);
}
```

### TypeScript

```ts
const student: {
    name: string;
    age: number;
} = {
    name: "Rakib",
    age: 25
};

for (const key in student) {
    console.log(key);
}
```

### Remember

```text
for...in → Key / Index

for...of → Value
```

---

# Part 4 — Array

## 📌 Definition



An Array is an ordered collection of values.

Array হলো একাধিক value-কে একটি ordered collection হিসেবে রাখার data structure।

---

# JavaScript vs TypeScript

### JavaScript

```js
const numbers = [10, 20, 30];
```

### TypeScript

```ts
const numbers: number[] = [10, 20, 30];
```

> TypeScript-এ Array-এর element type define করা যায়।

---

# Part 5 — Function

## 📌 Definition



A function is a reusable block of code that performs a specific task.

Function হলো একটি reusable block of code যা নির্দিষ্ট একটি কাজ সম্পন্ন করে।

---

# JavaScript vs TypeScript

### JavaScript

```js
function add(a, b) {
    return a + b;
}
```

### TypeScript

```ts
function add(a: number, b: number): number {
    return a + b;
}
```

### Difference

```text
JavaScript
→ Parameter type নেই
→ Return type নেই

TypeScript
→ Parameter type define করা যায়
→ Return type define করা যায়
```

---

# Part 6 — Array Function

Array-এর উপর কাজ করার জন্য JavaScript-এর built-in array methods ব্যবহার করা হয়। TypeScript-এ এগুলো একইভাবে ব্যবহার করা যায়, তবে TypeScript types check করে।

### Example

```js
const numbers = [10, 20, 30];

const result = numbers.map(number => number * 2);
```

TypeScript:

```ts
const numbers: number[] = [10, 20, 30];

const result: number[] = numbers.map(number => number * 2);
```

> মূল array method একই, TypeScript-এ data type জানা থাকে।

---

# Part 7 — Object

## 📌 Definition


An Object stores data in key-value pairs.

Object key-value pair-এর মাধ্যমে structured data সংরক্ষণ করে।

---

# JavaScript vs TypeScript

### JavaScript

```js
const student = {
    name: "Rakib",
    age: 25
};
```

### TypeScript

```ts
const student: {
    name: string;
    age: number;
} = {
    name: "Rakib",
    age: 25
};
```

> TypeScript-এ Object-এর property এবং property type define করা যায়।

---

# Part 8 — `toFixed()`

## 📌 What is `toFixed()`?



`toFixed()` formats a number to a specified number of decimal places.

`toFixed()` কোনো number-এর decimal places নির্দিষ্ট সংখ্যায় দেখানোর জন্য ব্যবহার করা হয়।

---

# Syntax

```js
number.toFixed(decimalPlaces)
```

### Example

```ts
const price: number = 99.4567;

const result: string = price.toFixed(2);

console.log(result);
```

Output:

```text
99.46
```

---

# ⚠️ Important

`toFixed()` **string return করে**, number নয়।

```ts
const price: number = 99.4567;

const result = price.toFixed(2);

console.log(typeof result);
```

Output:

```text
string
```

### Remember

```text
toFixed(2)
→ 2 decimal places
→ Returns string
```

---

# Part 9 — `map()`

## 📌 What is `map()`?


`map()` creates a new array by applying a function to every element of an array.

`map()` Array-এর প্রতিটি element-এর উপর একটি function চালিয়ে **নতুন Array** তৈরি করে।

---

# Syntax

```ts
array.map((element) => {
    return newValue;
});
```

---

# Example

### JavaScript

```js
const numbers = [10, 20, 30];

const result = numbers.map(number => number * 2);

console.log(result);
```

Output:

```text
[20, 40, 60]
```

### TypeScript

```ts
const numbers: number[] = [10, 20, 30];

const result: number[] = numbers.map((number: number): number => {
    return number * 2;
});
```

---

# Important Rules of `map()`

- প্রতিটি element-এর উপর কাজ করে।
- একটি **new array** return করে।
- Original array পরিবর্তন করে না।
- সাধারণত প্রতিটি element-এর জন্য একটি transformed value return করা হয়।

---

# JavaScript vs TypeScript — Core Concepts

| Concept | JavaScript | TypeScript |
|---|---|---|
| Variable | Dynamic type | Type define করা যায় |
| Conditional | Same syntax | Same syntax + type checking |
| `for...in` | Keys / indexes | Same |
| `for...of` | Values | Same |
| Array | Dynamic type | Array type define করা যায় |
| Function | Parameters untyped | Parameters + return type define করা যায় |
| Object | Dynamic structure | Property types define করা যায় |
| `toFixed()` | Same method | Same method + return type known |
| `map()` | Same method | Same method + element/return types checked |

---

# 🔍 Core Concept: JavaScript vs TypeScript

### JavaScript

```js
const numbers = [10, 20, 30];

function double(number) {
    return number * 2;
}

const result = numbers.map(double);
```

### TypeScript

```ts
const numbers: number[] = [10, 20, 30];

function double(number: number): number {
    return number * 2;
}

const result: number[] = numbers.map(double);
```

### Main Change

```text
JavaScript
→ Logic + Syntax

TypeScript
→ Logic + Syntax + Type Information
```

> TypeScript-এর বেশিরভাগ Core Concept JavaScript-এর উপর ভিত্তি করে তৈরি। প্রধান পার্থক্য হলো TypeScript code-এর type information এবং static type checking যোগ করে।

---

# ⚠️ Common Mistakes

## ❌ Mistake 1 — `for...in` এবং `for...of` গুলিয়ে ফেলা

```text
for...in → Key / Index

for...of → Value
```

---

## ❌ Mistake 2 — `toFixed()` কে Number মনে করা

```ts
const result = (10.456).toFixed(2);
```

`result` হলো `string`।

---

## ❌ Mistake 3 — `map()` Original Array পরিবর্তন করে মনে করা

```ts
const numbers = [10, 20, 30];

const result = numbers.map(number => number * 2);
```

`numbers` এবং `result` আলাদা Array।

---

## ❌ Mistake 4 — TypeScript-এ শুধু variable type দিয়ে থেমে যাওয়া

```ts
function add(a, b) {
    return a + b;
}
```

TypeScript-এ প্রয়োজন অনুযায়ী parameter এবং return type define করা ভালো:

```ts
function add(a: number, b: number): number {
    return a + b;
}
```

---

# ⚡ Quick Revision

```text
Variable
→ Data store করে

Conditional
→ Condition অনুযায়ী code execute করে

for...in
→ Key / Index

for...of
→ Value

Array
→ Ordered collection

Function
→ Reusable block of code

Object
→ Key-value pairs

toFixed()
→ Decimal places format করে
→ Returns string

map()
→ প্রতিটি element-এর উপর কাজ করে
→ New Array return করে
```

---

# 🧠 Memory Trick

```text
for...in  → INdex
for...of  → OF values

toFixed() → Fixed decimal places

map()     → Modify each item → New Array
```

---

# 🎯 Interview Questions

## Q1. What is the main difference between `for...in` and `for...of`?

**Answer:**

`for...in` keys বা indexes iterate করে, আর `for...of` iterable-এর values iterate করে।

---

## Q2. Does `toFixed()` return a number?

**Answer:**

না। `toFixed()` একটি `string` return করে।

---

## Q3. Does `map()` modify the original array?

**Answer:**

না। `map()` একটি নতুন Array return করে এবং original Array পরিবর্তন করে না।