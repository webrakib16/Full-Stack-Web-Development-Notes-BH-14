# 📚 Module: 21 | 🎓 Class: 8

# Special Types in TypeScript

> **Topic:** Nullable, Unknown & Never

---

# 📖 What I Learned Today

- Nullable Types
- `null`
- `undefined`
- `unknown`
- `never`
- TypeScript vs JavaScript
- Core Concept Analysis
- Important Syntax
- Common Mistakes
- Quick Revision
- Interview Questions

---

# Part 1 — Nullable Types

## 📌 Definition


A Nullable Type is a type that allows a value to be `null` or `undefined` in addition to its normal type.

Nullable Type হলো এমন type যেখানে কোনো value তার মূল type-এর পাশাপাশি `null` বা `undefined` হতে পারে।

> TypeScript-এ `strictNullChecks` enabled থাকলে `null` এবং `undefined` আলাদাভাবে handle করতে হয়।

---

# Syntax

```ts
let name: string | null = null;

let age: number | undefined = undefined;
```

এখানে:

```text
string | null
→ string অথবা null

number | undefined
→ number অথবা undefined
```

---

# Example

### JavaScript

```js
let userName = null;

console.log(userName);
```

### TypeScript

```ts
let userName: string | null = null;

console.log(userName);
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| Variable-এর type explicitly define করা হয় না | Type explicitly define করা যায় |
| `null` যেকোনো variable-এ রাখা যায় | Type-এর মধ্যে `null` allow করতে হয় |
| Static type checking নেই | Static type checking আছে |

---

# `null` vs `undefined`

| Type | Meaning |
|---|---|
| `null` | ইচ্ছাকৃতভাবে কোনো value নেই |
| `undefined` | Value দেওয়া হয়নি / value পাওয়া যায়নি |

---

# Part 2 — Unknown

## 📌 Definition


`unknown` represents a value whose type is not known yet, and it must be checked before being used.

`unknown` এমন একটি type যার value-এর type আগে থেকে জানা নেই। ব্যবহার করার আগে **type check** করতে হয়।

---

# Syntax

```ts
let value: unknown;

value = "Hello";
value = 100;
value = true;
```

`unknown` variable-এ যেকোনো type-এর value রাখা যায়।

কিন্তু type check ছাড়া সরাসরি ব্যবহার করা যায় না।

---

# Example

```ts
let value: unknown = "Hello";

if (typeof value === "string") {
    console.log(value.toUpperCase());
}
```

এখানে `typeof` দিয়ে type check করার পর value ব্যবহার করা হয়েছে।

---

# JavaScript vs TypeScript

### JavaScript

```js
let value = "Hello";

console.log(value.toUpperCase());
```

### TypeScript

```ts
let value: unknown = "Hello";

if (typeof value === "string") {
    console.log(value.toUpperCase());
}
```

### 🔍 Difference

```text
JavaScript
→ Runtime-এ type handle করে

TypeScript
→ unknown value ব্যবহারের আগে type check করতে বাধ্য করে
```

> `unknown` ব্যবহার করলে type safety বেশি থাকে।

---

# `unknown` vs `any`

| Feature | `unknown` | `any` |
|---|---|---|
| Any type-এর value রাখা যায় | ✅ | ✅ |
| Directly ব্যবহার করা যায় | ❌ | ✅ |
| Type checking required | ✅ | ❌ |
| Type Safety | বেশি | কম |

> Unknown data-এর ক্ষেত্রে `unknown` সাধারণত `any`-এর চেয়ে safer choice।

---

# Part 3 — Never

## 📌 Definition



`never` represents values that never occur.

It is commonly used for functions that **never successfully complete**.

`never` এমন একটি type বোঝায় যেখানে কোনো value কখনো return করা হবে না।

সাধারণত এমন function-এর ক্ষেত্রে ব্যবহার হয় যা:

- সবসময় error throw করে
- অথবা কখনো function-এর শেষ পর্যন্ত পৌঁছায় না

---

# Example — Error

```ts
function throwError(message: string): never {
    throw new Error(message);
}
```

এই function কোনো value return করে না এবং successfully শেষও হয় না।

---

# Example — Infinite Loop

```ts
function infiniteLoop(): never {
    while (true) {
        console.log("Running...");
    }
}
```

এই function কখনো শেষ হবে না।

---

# JavaScript vs TypeScript

### JavaScript

```js
function throwError(message) {
    throw new Error(message);
}
```

### TypeScript

```ts
function throwError(message: string): never {
    throw new Error(message);
}
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| Return type explicitly define করা হয় না | `never` return type define করা যায় |
| Static type checking নেই | Static type checking আছে |
| Function কখনো return না করলে সেটা type দিয়ে প্রকাশ করা যায় না | `never` দিয়ে প্রকাশ করা যায় |

---

# Part 4 — Core Concepts: JavaScript vs TypeScript

| Concept | JavaScript | TypeScript |
|---|---|---|
| `null` | Supported | Supported + Type checking |
| `undefined` | Supported | Supported + Type checking |
| Nullable Type | Explicit type system নেই | `string \| null` |
| Unknown Type | Built-in `unknown` নেই | `unknown` |
| Never Type | Built-in `never` নেই | `never` |
| Static Type Checking | ❌ | ✅ |
| Type Safety | তুলনামূলক কম | বেশি |

---

# Part 5 — Core Syntax Analysis

## Nullable

### JavaScript

```js
let name = null;
```

### TypeScript

```ts
let name: string | null = null;
```

### Change

```text
JavaScript → null

TypeScript → string | null
```

---

## Unknown

### JavaScript

```js
let value = getData();
```

### TypeScript

```ts
let value: unknown = getData();

if (typeof value === "string") {
    console.log(value.toUpperCase());
}
```

### Change

```text
JavaScript → Directly use করা যায়

TypeScript → Type check করে use করতে হয়
```

---

## Never

### JavaScript

```js
function fail(message) {
    throw new Error(message);
}
```

### TypeScript

```ts
function fail(message: string): never {
    throw new Error(message);
}
```

### Change

```text
JavaScript → No explicit return type

TypeScript → : never
```

---

# Part 6 — Important Syntax

```ts
// Nullable
let name: string | null = null;

// Undefined
let age: number | undefined = undefined;

// Unknown
let value: unknown = "Hello";

// Never
function fail(message: string): never {
    throw new Error(message);
}
```

---

# Part 7 — Common Mistakes

## ❌ Mistake 1 — Nullable Type না দেওয়া

```ts
let name: string = null;
```

`strictNullChecks` enabled থাকলে এটি error হবে।

Correct:

```ts
let name: string | null = null;
```

---

## ❌ Mistake 2 — `unknown` Directly ব্যবহার করা

```ts
let value: unknown = "Hello";

console.log(value.toUpperCase());
```

এটি error হবে, কারণ `value`-এর type নিশ্চিত নয়।

Correct:

```ts
if (typeof value === "string") {
    console.log(value.toUpperCase());
}
```

---

## ❌ Mistake 3 — `never` কে `void` মনে করা

```text
void
→ Function কোনো value return করে না
→ কিন্তু function শেষ হতে পারে

never
→ Function successfully শেষই হয় না
```

---

# ⚡ Quick Revision

```text
Nullable
→ Type + null / undefined

unknown
→ Type unknown
→ Use করার আগে type check করতে হয়

never
→ কোনো value return করে না
→ Function successfully complete হয় না
```

### 🧠 Memory Trick

```text
Nullable → Maybe No Value

unknown  → Type Not Known Yet

never    → Value Never Exists
```

---

# 🎯 Interview Questions

## Q1. What is the difference between `unknown` and `any`?

**Answer:**

দুটোতেই যেকোনো type-এর value রাখা যায়। কিন্তু `unknown` value ব্যবহার করার আগে type check করতে হয়, যেখানে `any` সরাসরি ব্যবহার করা যায়। তাই `unknown` বেশি type-safe।

---

## Q2. What is the difference between `void` and `never`?

**Answer:**

`void` সাধারণত এমন function-এর return type যা কোনো value return করে না, কিন্তু function শেষ হতে পারে। `never` এমন function-এর জন্য যা successfully কখনো complete হয় না।

---

## Q3. How do you create a nullable type in TypeScript?

**Answer:**

Union type ব্যবহার করে:

```ts
let name: string | null = null;
```

এখানে variable-এর value `string` অথবা `null` হতে পারে।