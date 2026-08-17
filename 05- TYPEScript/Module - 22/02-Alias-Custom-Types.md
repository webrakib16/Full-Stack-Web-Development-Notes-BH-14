# 📚 Module: 22 | 🎓 Class: 02

# Type Alias & Custom Types

> **Topic:** Type Alias, Custom Types & Reusable Type Definitions

---

# 📖 What I Learned Today

- What is Type Alias
- Creating Custom Types
- Reusable Types
- Type Alias with Primitive Types
- Type Alias with Object Types
- Type Alias with Union Types
- Type Alias with Array
- Type Alias with Function
- JavaScript vs TypeScript
- Core Concept Analysis
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What is a Type Alias?



A Type Alias gives a custom name to a type so that it can be reused throughout the TypeScript code. 

Type Alias ব্যবহার করে কোনো type-এর জন্য একটি **custom name** তৈরি করা যায়। পরে সেই নামটি বারবার ব্যবহার করা যায়।

---

# Part 1 — Basic Type Alias

## Syntax

```ts
type UserName = string;
```

এখন `UserName` একটি custom type।

```ts
let name: UserName = "Rakib";
```

---

# Example

```ts
type Age = number;

let userAge: Age = 22;
```

এখানে `Age` হলো `number` type-এর একটি custom name।

---

# Part 2 — Object Type Alias

Type Alias সবচেয়ে বেশি Object-এর structure define করার জন্য ব্যবহার করা হয়।

## Syntax

```ts
type Student = {
    name: string;
    age: number;
    department: string;
};
```

এখন একই type multiple object-এ ব্যবহার করা যায়।

```ts
const student1: Student = {
    name: "Rakib",
    age: 22,
    department: "Chemistry"
};

const student2: Student = {
    name: "Karim",
    age: 23,
    department: "Physics"
};
```

---

# Why Use Type Alias?

Type Alias ব্যবহার করলে একই Object structure বারবার লিখতে হয় না।

### Without Type Alias

```ts
const student1: {
    name: string;
    age: number;
} = {
    name: "Rakib",
    age: 22
};

const student2: {
    name: string;
    age: number;
} = {
    name: "Karim",
    age: 23
};
```

### With Type Alias

```ts
type Student = {
    name: string;
    age: number;
};

const student1: Student = {
    name: "Rakib",
    age: 22
};

const student2: Student = {
    name: "Karim",
    age: 23
};
```

> Type Alias code-কে reusable এবং organized করে।

---

# Part 3 — Type Alias with Union Type

Type Alias-এর সাথে Union Type ব্যবহার করা যায়।

```ts
type ID = string | number;

let userId: ID = 101;

userId = "user-101";
```

এখানে `ID` হিসেবে `string` অথবা `number` ব্যবহার করা যাবে।

---

# Part 4 — Type Alias with Array

Array-এর type-এর জন্যও Type Alias তৈরি করা যায়।

```ts
type Numbers = number[];

const marks: Numbers = [80, 90, 85];
```

Object array:

```ts
type Student = {
    name: string;
    age: number;
};

type Students = Student[];

const students: Students = [
    {
        name: "Rakib",
        age: 22
    },
    {
        name: "Karim",
        age: 23
    }
];
```

---

# Part 5 — Type Alias with Function

Function-এর structure-এর জন্যও Type Alias ব্যবহার করা যায়।

```ts
type Add = (a: number, b: number) => number;

const add: Add = (a, b) => {
    return a + b;
};
```

এখানে:

```text
Add
→ Function Type

a → number
b → number
return → number
```

---

# Part 6 — JavaScript vs TypeScript

### JavaScript

JavaScript-এ Type Alias-এর concept নেই।

```js
const student = {
    name: "Rakib",
    age: 22
};
```

### TypeScript

```ts
type Student = {
    name: string;
    age: number;
};

const student: Student = {
    name: "Rakib",
    age: 22
};
```

### 🔍 Difference

| Feature | JavaScript | TypeScript |
|---|---|---|
| Type Alias | ❌ | ✅ |
| Custom Types | ❌ | ✅ |
| Reusable Type Definition | ❌ | ✅ |
| Static Type Checking | ❌ | ✅ |
| Object Structure Definition | ❌ | ✅ |

---

# Part 7 — Core Concept Analysis

Type Alias JavaScript-এর runtime feature নয়। এটি TypeScript-এর **type system-এর অংশ**।

```text
JavaScript
→ Runtime-focused

TypeScript
→ JavaScript
→ + Static Type System
→ + Custom Type Definitions
```

Type Alias compile হওয়ার পর JavaScript output-এ থাকে না।

### TypeScript

```ts
type User = {
    name: string;
    age: number;
};

const user: User = {
    name: "Rakib",
    age: 22
};
```

### Compiled JavaScript

```js
const user = {
    name: "Rakib",
    age: 22
};
```

> `type User` runtime JavaScript-এর অংশ নয়। এটি compile-time type checking-এর জন্য ব্যবহৃত হয়।

---

# Part 8 — Type Alias vs Direct Type

| Direct Type | Type Alias |
|---|---|
| Type সরাসরি লেখা হয় | Type-এর একটি নাম দেওয়া হয় |
| Reuse করা কঠিন | সহজে reuse করা যায় |
| ছোট structure-এর জন্য useful | বড়/reusable structure-এর জন্য useful |
| `name: string` | `type UserName = string` |

---

# Part 9 — Common Mistakes

## ❌ Mistake 1 — Wrong Property Type

```ts
type Student = {
    name: string;
    age: number;
};

const student: Student = {
    name: "Rakib",
    age: "22"
};
```

`age` অবশ্যই `number` হতে হবে।

---

## ❌ Mistake 2 — Missing Required Property

```ts
type Student = {
    name: string;
    age: number;
};

const student: Student = {
    name: "Rakib"
};
```

`age` required property হওয়ায় error হবে।

---

## ❌ Mistake 3 — Wrong Union Value

```ts
type ID = string | number;

let userId: ID = true;
```

`ID` শুধু `string` অথবা `number` গ্রহণ করবে।

---

# ⚡ Quick Revision

```text
Type Alias
→ Custom name for a type

type UserName = string;

Object Type
→ Reusable Object Structure

type Student = {
    name: string;
    age: number;
};

Union Type
→ Multiple allowed types

type ID = string | number;

Array Type
→ Custom name for Array type

type Numbers = number[];

Function Type
→ Custom name for Function structure

type Add = (a: number, b: number) => number;
```

### 🧠 Memory Trick

```text
Type Alias
→ Create Once
→ Reuse Many Times
```

---

# 🎯 Interview Questions

## Q1. What is a Type Alias in TypeScript?

**Answer:**

Type Alias হলো কোনো type-এর জন্য একটি custom name তৈরি করার পদ্ধতি, যাতে সেই type পরে বারবার reuse করা যায়।

---

## Q2. Why do we use Type Alias?

**Answer:**

Repeated type definition কমানো, reusable custom types তৈরি করা এবং code-এর structure ও readability improve করার জন্য Type Alias ব্যবহার করা হয়।

---

## Q3. Does Type Alias exist in JavaScript at runtime?

**Answer:**

না। Type Alias TypeScript-এর compile-time feature। JavaScript-এ compile করার সময় Type Alias-এর অংশটি remove হয়ে যায়।