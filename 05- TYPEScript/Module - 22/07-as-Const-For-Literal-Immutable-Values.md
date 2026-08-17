# 📚 Module: 22 | 🎓 Class: 07

# `as const` — Literal & Immutable Values

> **Topic:** `as const`, Literal Types & Immutable Values

---

# 📖 What I Learned Today

- What is `as const`
- Literal Types
- Readonly Properties
- Readonly Arrays
- Immutable Values
- `as const` with Objects
- `as const` with Arrays
- `as const` vs `const`
- JavaScript vs TypeScript
- Core Concept Analysis
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What is `as const`?



`as const` tells TypeScript to treat a value as a **readonly literal value** instead of widening it to a general type.

`as const` ব্যবহার করলে TypeScript কোনো value-কে সাধারণ `string`, `number` বা `boolean` হিসেবে না দেখে তার **exact literal value** হিসেবে ধরে এবং properties/elements-কে readonly করে দেয়।

---

# Part 1 — Literal Type with `as const`

### Without `as const`

```ts
let role = "admin";
```

TypeScript সাধারণত এটিকে:

```text
string
```

হিসেবে ধরে।

### With `as const`

```ts
let role = "admin" as const;
```

এখন TypeScript এটিকে:

```text
"admin"
```

literal type হিসেবে ধরে।

---

# Part 2 — `const` vs `as const`

দুটো দেখতে একই ধরনের হলেও কাজ এক নয়।

### `const`

```ts
const role = "admin";
```

এখানে variable-টি reassign করা যাবে না, কিন্তু এটি সাধারণত `"admin"` literal value হিসেবে inferred হতে পারে।

### `as const`

```ts
let role = "admin" as const;
```

এখানে value-এর type explicitly literal `"admin"` এবং value immutable/readonly হিসেবে treated হয়।

### 🔍 Main Difference

```text
const
→ Variable reassign করা যায় না

as const
→ Literal type + readonly behavior
```

---

# Part 3 — `as const` with Object

### Without `as const`

```ts
const user = {
    name: "Rakib",
    age: 22
};
```

Properties সাধারণত:

```text
name → string
age  → number
```

### With `as const`

```ts
const user = {
    name: "Rakib",
    age: 22
} as const;
```

এখন:

```text
name → "Rakib"
age  → 22
```

এবং properties readonly।

---

# Example

```ts
const user = {
    name: "Rakib",
    age: 22
} as const;

user.name = "Karim"; // ❌
user.age = 23;       // ❌
```

কারণ `as const` Object-এর properties-কে readonly করে।

---

# Part 4 — `as const` with Array

### Without `as const`

```ts
const colors = ["red", "green", "blue"];
```

এটি সাধারণত:

```text
string[]
```

হিসেবে inferred হয়।

### With `as const`

```ts
const colors = ["red", "green", "blue"] as const;
```

এখন এটি:

```text
readonly ["red", "green", "blue"]
```

হিসেবে treated হয়।

অর্থাৎ এটি একটি readonly tuple।

---

# Example

```ts
const colors = ["red", "green", "blue"] as const;

colors.push("yellow"); // ❌
colors[0] = "black";   // ❌
```

---

# Part 5 — `as const` and Literal Types

`as const` কোনো value-এর exact literal type preserve করে।

```ts
const status = "success" as const;
```

Type:

```text
"success"
```

Object:

```ts
const user = {
    role: "admin"
} as const;
```

Type:

```text
{
    readonly role: "admin";
}
```

Array:

```ts
const numbers = [10, 20, 30] as const;
```

Type:

```text
readonly [10, 20, 30]
```

---

# Part 6 — JavaScript vs TypeScript

### JavaScript

```js
const user = {
    name: "Rakib",
    age: 22
};
```

JavaScript-এ `as const` syntax নেই।

### TypeScript

```ts
const user = {
    name: "Rakib",
    age: 22
} as const;
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| `as const` নেই | `as const` আছে |
| Runtime value normal থাকে | TypeScript exact literal type infer করে |
| Compile-time readonly checking নেই | Readonly checking আছে |
| Literal type system নেই | Literal types আছে |

---

# Part 7 — Core Concept Analysis

`as const` মূলত TypeScript-এর **compile-time type system-এর feature**।

### TypeScript

```ts
const user = {
    name: "Rakib",
    age: 22
} as const;
```

### Compiled JavaScript

```js
const user = {
    name: "Rakib",
    age: 22
};
```

### 🔍 What Changed?

```text
TypeScript
→ as const
→ Literal Types
→ readonly Type Checking

JavaScript
→ as const থাকে না
→ Runtime Object একই থাকে
```

> `as const` runtime-এ Object বা Array-কে automatically freeze করে না। এটি মূলত TypeScript-এর compile-time readonly এবং literal type behavior দেয়।

---

# Part 8 — `as const` vs `Object.freeze()`

দুটো এক জিনিস নয়।

### `as const`

```ts
const user = {
    name: "Rakib"
} as const;
```

→ TypeScript compile-time-এ readonly করে।

### `Object.freeze()`

```js
const user = Object.freeze({
    name: "Rakib"
});
```

→ JavaScript runtime-এ Object freeze করার জন্য ব্যবহৃত হয়।

### Difference

| `as const` | `Object.freeze()` |
|---|---|
| TypeScript feature | JavaScript runtime feature |
| Compile-time readonly | Runtime freezing |
| Literal types preserve করে | Literal type তৈরি করে না |
| Runtime behavior পরিবর্তন করে না | Object mutation prevent করে |

---

# Part 9 — `as const` with Union Types

`as const` ব্যবহার করে Object থেকে literal values-এর precise type পাওয়া যায়।

```ts
const roles = {
    ADMIN: "admin",
    USER: "user",
    GUEST: "guest"
} as const;
```

এখন:

```text
roles.ADMIN → "admin"
roles.USER  → "user"
roles.GUEST → "guest"
```

Literal values preserve থাকে।

---

# Part 10 — Common Mistakes

## ❌ Mistake 1 — `const` এবং `as const` একই মনে করা

```text
const
→ Variable reassign বন্ধ করে

as const
→ Literal Type + readonly behavior
```

---

## ❌ Mistake 2 — `as const` কে Runtime Freeze মনে করা

```ts
const user = {
    name: "Rakib"
} as const;
```

এটি JavaScript runtime-এ Object-কে `Object.freeze()` করে না।

---

## ❌ Mistake 3 — Readonly Array পরিবর্তন করা

```ts
const numbers = [10, 20, 30] as const;

numbers.push(40); // ❌
```

`as const` Array-কে readonly করে।

---

# ⚡ Quick Revision

```text
as const
→ Exact Literal Type
→ readonly Object Properties
→ readonly Array / Tuple
→ Compile-time Feature
```

### 🧠 Memory Trick

```text
const
→ Cannot Reassign Variable

as const
→ Keep Exact Value
→ Make It Readonly
```

---

# 🎯 Interview Questions

## Q1. What does `as const` do in TypeScript?

**Answer:**

`as const` কোনো value-এর exact literal type preserve করে এবং Object-এর properties ও Array-এর elements-কে readonly হিসেবে treat করে।

---

## Q2. What is the difference between `const` and `as const`?

**Answer:**

`const` variable reassign করা বন্ধ করে। `as const` value-এর literal type preserve করে এবং Object/Array-কে readonly type হিসেবে treat করে।

---

## Q3. Does `as const` freeze an object at runtime?

**Answer:**

না। `as const` TypeScript-এর compile-time feature। Runtime-এ Object freeze করতে `Object.freeze()` ব্যবহার করা হয়।