# 📚 Module: 22 | 🎓 Class: 04

# Generics in TypeScript

> **Topic:** Generics, Reusable & Scalable Types

---

# 📖 What I Learned Today

- What are Generics
- Generic Type
- Generic Function
- Generic Array
- Generic Interface
- Generic Type Alias
- Reusable Types
- Scalable Types
- JavaScript vs TypeScript
- Core Concept Analysis
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What are Generics?



Generics allow us to create **reusable and flexible types** that can work with different data types while maintaining type safety.

Generics ব্যবহার করে এমন reusable type বা function তৈরি করা যায় যা বিভিন্ন data type-এর সাথে কাজ করতে পারে, কিন্তু type safety বজায় রাখে।

### 🧠 Basic Idea

```text
One Logic
   ↓
Different Types
   ↓
Type Safety
```

---

# Part 1 — Generic Function

## 📌 Definition

একটি function-কে এমনভাবে তৈরি করা যায় যাতে এটি বিভিন্ন type-এর value নিয়ে কাজ করতে পারে।

### Syntax

```ts
function identity<T>(value: T): T {
    return value;
}
```

এখানে `T` হলো একটি **type parameter**।

---

# Example

```ts
const numberValue = identity<number>(100);

const stringValue = identity<string>("Hello");
```

এখানে একই function:

```text
number → number
string → string
```

দুই ধরনের data-এর সাথে কাজ করছে।

---

# Part 2 — JavaScript vs TypeScript

### JavaScript

```js
function identity(value) {
    return value;
}

const result = identity(100);
```

### TypeScript

```ts
function identity<T>(value: T): T {
    return value;
}

const result = identity<number>(100);
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| Type parameter নেই | Generic Type Parameter আছে |
| Input type explicitly define করা হয় না | `T` দিয়ে type define করা যায় |
| Return type explicitly define করা হয় না | `: T` দিয়ে return type define করা যায় |
| Static type safety নেই | Type safety বজায় থাকে |

> Function-এর মূল logic একই থাকে। TypeScript-এ generic type information যোগ হয়।

---

# Part 3 — Generic Type Inference

অনেক সময় `<number>` বা `<string>` manually লিখতে হয় না। TypeScript argument দেখে type বুঝে নিতে পারে।

```ts
function identity<T>(value: T): T {
    return value;
}

const numberValue = identity(100);
const stringValue = identity("Hello");
```

TypeScript automatically বুঝবে:

```text
numberValue → number

stringValue → string
```

---

# Part 4 — Generic Array

একটি generic type ব্যবহার করে বিভিন্ন type-এর Array তৈরি করা যায়।

```ts
function getFirst<T>(items: T[]): T {
    return items[0];
}
```

Example:

```ts
const firstNumber = getFirst([10, 20, 30]);

const firstName = getFirst(["Rakib", "Karim", "Hasan"]);
```

এখানে একই function `number[]` এবং `string[]` দুটির সাথেই কাজ করছে।

---

# Part 5 — Generic Interface

Interface-এর সাথেও Generic ব্যবহার করা যায়।

```ts
interface Box<T> {
    value: T;
}
```

এখন:

```ts
const numberBox: Box<number> = {
    value: 100
};

const stringBox: Box<string> = {
    value: "Hello"
};
```

একই Interface বিভিন্ন type-এর জন্য reuse করা যাচ্ছে।

---

# Part 6 — Generic Type Alias

Type Alias-এর সাথেও Generic ব্যবহার করা যায়।

```ts
type Response<T> = {
    data: T;
    success: boolean;
};
```

এখন:

```ts
const userResponse: Response<string> = {
    data: "Rakib",
    success: true
};

const numberResponse: Response<number> = {
    data: 100,
    success: true
};
```

---

# Part 7 — Reusable Types

## 📌 Why are Generics Reusable?

একই type বা function-এর জন্য আলাদা আলাদা type তৈরি করার প্রয়োজন হয় না।

### Without Generics

```ts
function getNumber(value: number): number {
    return value;
}

function getString(value: string): string {
    return value;
}
```

### With Generics

```ts
function getValue<T>(value: T): T {
    return value;
}
```

একটি generic function বিভিন্ন type-এর সাথে কাজ করতে পারে।

---

# Part 8 — Scalable Types

## 📌 What does Scalable mean?



Scalable types can be extended and reused as an application grows without unnecessary duplication.

Application বড় হওয়ার সাথে সাথে একই type logic বারবার না লিখে reuse এবং extend করা যায়। এটাই scalable type-এর মূল সুবিধা।

```text
Generic Type
      ↓
Reusable
      ↓
Less Duplication
      ↓
Easier to Scale
```

---

# Part 9 — Generic vs Union Type

### Union Type

```ts
function getValue(value: string | number): string | number {
    return value;
}
```

এখানে input `string` অথবা `number` হতে পারে।

কিন্তু return type-এর সাথে input-এর relationship স্পষ্টভাবে preserve হয় না।

---

### Generic Type

```ts
function getValue<T>(value: T): T {
    return value;
}
```

এখানে:

```text
Input Type = T
       ↓
Output Type = T
```

অর্থাৎ input এবং output-এর type relationship বজায় থাকে।

---

# Part 10 — JavaScript vs TypeScript Core Concept

| Concept | JavaScript | TypeScript |
|---|---|---|
| Generic Types | ❌ | ✅ |
| Type Parameters | ❌ | ✅ |
| Reusable Type Logic | সাধারণভাবে runtime logic দিয়ে | Generic Type দিয়ে |
| Static Type Safety | ❌ | ✅ |
| Type Relationship | Explicitly enforce করা যায় না | Generics দিয়ে preserve করা যায় |
| Runtime Generic | ❌ | ❌ |
| Compile-time Type System | ❌ | ✅ |

> Generics মূলত TypeScript-এর **compile-time feature**। এগুলো JavaScript runtime-এ থাকে না।

---

# Part 11 — Core Concept Analysis

### TypeScript

```ts
function identity<T>(value: T): T {
    return value;
}

const result = identity<number>(100);
```

### Compiled JavaScript

```js
function identity(value) {
    return value;
}

const result = identity(100);
```

### 🔍 What Changed?

```text
TypeScript
→ <T>
→ : T
→ Type Safety

JavaScript
→ Generic Type Information নেই
→ শুধু Function Logic থাকে
```

> Generics JavaScript-এর runtime behavior পরিবর্তন করে না; TypeScript compile-time-এ type safety দেয়।

---

# Part 12 — Common Mistakes

## ❌ Mistake 1 — Generic Type ভুলভাবে ব্যবহার করা

```ts
function identity<T>(value: T): T {
    return "Hello";
}
```

এখানে `T` যেকোনো type হতে পারে। তাই সবসময় `string` return করা যাবে না।

Correct:

```ts
function identity<T>(value: T): T {
    return value;
}
```

---

## ❌ Mistake 2 — Generic-এর বদলে অতিরিক্ত Union ব্যবহার

```ts
function getValue(value: string | number): string | number {
    return value;
}
```

যদি input এবং output-এর type relationship ধরে রাখতে হয়, Generic বেশি appropriate।

```ts
function getValue<T>(value: T): T {
    return value;
}
```

---

## ❌ Mistake 3 — Generic Type-এর অর্থ না বুঝে `T` ব্যবহার করা

`T` কোনো fixed type নয়।

```text
T → Type Parameter

T হতে পারে:
number
string
boolean
object
array
```

---

# ⚡ Quick Revision

```text
Generics
→ Reusable + Flexible + Type Safe

<T>
→ Type Parameter

Generic Function
→ function identity<T>(value: T): T

Generic Interface
→ interface Box<T>

Generic Type Alias
→ type Response<T>

T
→ Input এবং Output-এর type relationship ধরে রাখতে পারে
```

### 🧠 Memory Trick

```text
Generics

One Logic
   ↓
Many Types
   ↓
Type Safe
   ↓
Reusable
   ↓
Scalable
```

---

# 🎯 Interview Questions

## Q1. What are Generics in TypeScript?

**Answer:**

Generics এমন reusable এবং flexible type তৈরি করতে সাহায্য করে যা বিভিন্ন data type-এর সাথে কাজ করতে পারে এবং type safety বজায় রাখে।

---

## Q2. Why are Generics better than `any`?

**Answer:**

`any` type checking অনেকটাই বন্ধ করে দেয়। Generics বিভিন্ন type-এর সাথে কাজ করেও type information এবং type safety বজায় রাখে।

---

## Q3. What is the purpose of `<T>` in Generics?

**Answer:**

`<T>` একটি type parameter হিসেবে কাজ করে। এটি function, interface বা type-এর মধ্যে কোন type ব্যবহার হবে তা dynamically determine করতে সাহায্য করে।