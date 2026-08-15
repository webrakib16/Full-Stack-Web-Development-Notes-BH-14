# 📚 Module: 21 | 🎓 Class: 4

# Non-Primitive Types in TypeScript

> **Topic:** Array, Object & Tuple

---

# 📖 What I Learned Today

- Non-Primitive Types
- Array Type
- Object Type
- Tuple Type
- Array vs Object vs Tuple
- JavaScript vs TypeScript
- Important Syntax
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What are Non-Primitive Types?

### 🇺🇸 English

Non-primitive types are used to **group multiple values together with structure**.

### 🇧🇩 বাংলা

Primitive types যেমন `number`, `string`, `boolean` সাধারণত single value represent করে। Non-primitive types ব্যবহার করে একাধিক value-কে structure অনুযায়ী group করা যায়।

### Main Types

- Array
- Object
- Tuple

---

# Part 1 — Array Type

## 📌 Definition

### 🇺🇸 English

An ordered list of values that all share the same type.

### 🇧🇩 বাংলা

Array হলো একটি ordered list যেখানে সাধারণত সব value একই type-এর হয়।

---

# Syntax

```ts
let numbers: number[] = [10, 20, 30];

let fruits: string[] = ["Apple", "Banana", "Orange"];
```

---

# Important Points

- একই type-এর values রাখা হয়।
- Array-এর length flexible।
- Index `0` থেকে শুরু হয়।
- Index ব্যবহার করে value access করা যায়।

```ts
numbers[0]; // 10
```

---

# JavaScript vs TypeScript

### JavaScript

```js
let numbers = [10, 20, 30];
```

### TypeScript

```ts
let numbers: number[] = [10, 20, 30];
```

> TypeScript-এ `number[]` দিয়ে Array-এর element type নির্দিষ্ট করা যায়।

---

# Part 2 — Object Type

## 📌 Definition

### 🇺🇸 English

A structure that groups values under named keys.

### 🇧🇩 বাংলা

Object হলো এমন একটি structure যেখানে বিভিন্ন value-কে named key/property-এর মাধ্যমে রাখা হয়।

---

# Example

```ts
let student: {
    name: string;
    age: number;
    isStudent: boolean;
} = {
    name: "Alice",
    age: 22,
    isStudent: true
};
```

---

# Object Structure

```text
key → property type → value
```

```text
name      → string  → "Alice"
age       → number  → 22
isStudent → boolean → true
```

---

# JavaScript vs TypeScript

### JavaScript

```js
let student = {
    name: "Alice",
    age: 22,
    isStudent: true
};
```

### TypeScript

```ts
let student: {
    name: string;
    age: number;
    isStudent: boolean;
} = {
    name: "Alice",
    age: 22,
    isStudent: true
};
```

> TypeScript-এ Object-এর প্রতিটি property-এর type define করা যায়।

---

# Part 3 — Tuple Type

## 📌 Definition

### 🇺🇸 English

A fixed-length array where each position has its own type.

### 🇧🇩 বাংলা

Tuple দেখতে Array-এর মতো, কিন্তু প্রতিটি position-এর জন্য নির্দিষ্ট type থাকে। এখানে **order এবং length গুরুত্বপূর্ণ**।

---

# Example

```ts
let user: [string, number] = ["Alice", 25];
```

```text
slot 0 → string → "Alice"
slot 1 → number → 25
```

---

# Important Points

- Fixed length
- Fixed order
- Fixed type for each position
- প্রতিটি position-এর type আলাদা হতে পারে
- Small fixed groups of related values-এর জন্য useful

---

# Part 4 — Array vs Object vs Tuple

| Feature | Array | Object | Tuple |
|---|---|---|---|
| Structure | Ordered list | Key-value pairs | Fixed-length list |
| Data Types | Usually one type | Mixed, per key | Mixed, per position |
| Order | Flexible | Not guaranteed | Strict, matters |
| Length | Flexible | Depends on properties | Fixed |
| Best Use Case | Lists of similar items | Structured records | Small fixed groups |

---

# Part 5 — Important Syntax

## Array

```ts
let numbers: number[] = [10, 20, 30];

let fruits: string[] = ["Apple", "Banana", "Orange"];
```

## Object

```ts
let student: {
    name: string;
    age: number;
} = {
    name: "Alice",
    age: 22
};
```

## Tuple

```ts
let user: [string, number] = ["Alice", 25];
```

---

# Part 6 — JavaScript vs TypeScript

| Feature | JavaScript | TypeScript |
|---|---|---|
| Array Type | Type is not explicitly declared | Type can be declared |
| Object Properties | Type is not explicitly declared | Property types can be declared |
| Tuple | No strict tuple type | Fixed types and order can be defined |
| Type Checking | Runtime | Compile-time |

---

# Part 7 — Common Mistakes

## ❌ Array

```ts
let numbers: number[] = [10, 20, "30"];
```

`number[]` হলে সব elements `number` হতে হবে।

---

## ❌ Object

```ts
let student: {
    name: string;
    age: number;
} = {
    name: "Alice",
    age: "22"
};
```

`age` অবশ্যই `number` হতে হবে।

---

## ❌ Tuple

```ts
let user: [string, number] = [25, "Alice"];
```

Tuple-এ **order এবং type দুটোই match করতে হবে।**

---

# ⚡ Quick Revision

```text
Array
→ Ordered List
→ Usually Same Type
→ Flexible Length

Object
→ Key-Value Pairs
→ Different Types per Key

Tuple
→ Fixed-Length Array
→ Fixed Order
→ Fixed Type per Position
```

### 🧠 Memory Trick

```text
Array  → Same Type
Object → Named Keys
Tuple  → Fixed Order + Fixed Types
```

---

# 🎯 Interview Questions

## Q1. What is the main difference between an Array and a Tuple in TypeScript?

**Answer:**  
Array সাধারণত একই type-এর multiple values রাখে এবং এর length flexible। Tuple-এর length, order এবং প্রতিটি position-এর type নির্দিষ্ট থাকে।

---

## Q2. Why is Object typing useful in TypeScript?

**Answer:**  
Object-এর প্রতিটি property-এর expected type নির্দিষ্ট করা যায়। ফলে ভুল type-এর value দিলে TypeScript error detect করতে পারে।

---

## Q3. When should you use a Tuple instead of an Array?

**Answer:**  
যখন ছোট একটি fixed group of values থাকে এবং প্রতিটি position-এর নির্দিষ্ট type ও order গুরুত্বপূর্ণ, তখন Tuple ব্যবহার করা হয়।

---

# 🔑 Keywords

- Non-Primitive Types
- Array
- Object
- Tuple
- Type Annotation
- Index
- Key-Value Pair
- Fixed Length
- Fixed Order
- Type Safety