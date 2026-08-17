# 📚 Module: 22 | 🎓 Class: 05

# Advanced Generics

> **Topic:** Constraints & Default Types

---

# 📖 What I Learned Today

- Generic Constraints
- `extends` with Generics
- Keyof Constraint
- Generic Constraints with Objects
- Default Generic Types
- Generic Constraints vs Union Types
- JavaScript vs TypeScript
- Core Concept Analysis
- Common Mistakes
- Quick Revision
- Interview Questions

---

# Part 1 — Generic Constraints

## 📌 Definition



Generic Constraints restrict a generic type to a specific set of types or structures.

Generic Constraint ব্যবহার করে Generic Type-কে নির্দিষ্ট কোনো type বা structure-এর মধ্যে সীমাবদ্ধ করা যায়।

---

# Syntax

```ts
function getLength<T extends { length: number }>(value: T): number {
    return value.length;
}
```

এখানে:

```text
T
→ Any type হতে পারে

T extends { length: number }
→ কিন্তু T-এর মধ্যে অবশ্যই length property থাকতে হবে
```

---

# Example

```ts
function getLength<T extends { length: number }>(value: T): number {
    return value.length;
}

getLength("Hello");
getLength([10, 20, 30]);
```

String এবং Array দুটিরই `length` property আছে, তাই দুটিই valid।

```ts
getLength(100); // ❌
```

`number`-এর `length` property নেই।

---

# Part 2 — `extends` in Generic Constraints

এখানে `extends` inheritance বোঝাচ্ছে না। Generic-এর ক্ষেত্রে এটি **constraint** তৈরি করে।

```ts
function getValue<T extends string | number>(value: T): T {
    return value;
}
```

এখানে `T` শুধু:

```text
string
or
number
```

হতে পারবে।

```ts
getValue("Hello"); // ✅
getValue(100);     // ✅
getValue(true);    // ❌
```

---

# Part 3 — Object Constraints

Generic-এর মধ্যে নির্দিষ্ট Object structure-ও constraint করা যায়।

```ts
function getId<T extends { id: number }>(user: T): number {
    return user.id;
}
```

Example:

```ts
const user = {
    id: 101,
    name: "Rakib"
};

getId(user);
```

এখানে `T` Object-এর মধ্যে অবশ্যই:

```ts
id: number
```

থাকতে হবে।

---

# Part 4 — `keyof` Constraint

## 📌 Definition



`keyof` creates a union of all property keys of a type.

`keyof` কোনো Object Type-এর সব property key-কে একটি Union Type হিসেবে তৈরি করে।

---

# Example

```ts
type Student = {
    name: string;
    age: number;
    department: string;
};

type StudentKeys = keyof Student;
```

এখন:

```text
StudentKeys
→ "name" | "age" | "department"
```

---

# Generic with `keyof`

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}
```

Example:

```ts
const student = {
    name: "Rakib",
    age: 22
};

getProperty(student, "name"); // "Rakib"
getProperty(student, "age");  // 22
```

Invalid key:

```ts
getProperty(student, "salary"); // ❌
```

---

# Part 5 — Default Generic Types

## 📌 Definition



A Default Generic Type provides a default type when no type argument is explicitly provided.

Default Generic Type ব্যবহার করলে Generic-এর জন্য কোনো type explicitly না দিলে একটি **default type** automatically ব্যবহার হয়।

---

# Syntax

```ts
type Response<T = string> = {
    data: T;
};
```

এখানে `T`-এর default type হলো `string`।

---

# Example

```ts
type Response<T = string> = {
    data: T;
};

const response1: Response = {
    data: "Success"
};

const response2: Response<number> = {
    data: 100
};
```

এখানে:

```text
Response
→ T = string

Response<number>
→ T = number
```

---

# Part 6 — Default Type with Generic Function

```ts
function createValue<T = string>(value?: T): T | undefined {
    return value;
}
```

Type explicitly না দিলে default হিসেবে `string` ব্যবহৃত হবে।

```ts
const result = createValue("Hello");
```

এখানে `T` হলো `string`।

---

# Part 7 — Constraints vs Default Types

| Feature | Constraint | Default Type |
|---|---|---|
| Purpose | Type restrict করে | Default type দেয় |
| Syntax | `T extends ...` | `T = ...` |
| Example | `T extends string` | `T = string` |
| Main Goal | Allowed type control | Type argument না দিলে fallback দেওয়া |

### 🧠 Memory Trick

```text
Constraint
→ T কী হতে পারবে?

Default
→ T না দিলে কী হবে?
```

---

# Part 8 — Constraint vs Union Type

### Union Type

```ts
function getValue(value: string | number): string | number {
    return value;
}
```

এখানে শুধু `string` অথবা `number` allowed।

### Generic Constraint

```ts
function getValue<T extends string | number>(value: T): T {
    return value;
}
```

এখানে input-এর exact type `T` হিসেবে preserve হয়।

```text
Union
→ Allowed Types

Generic Constraint
→ Allowed Types + Type Relationship
```

---

# Part 9 — JavaScript vs TypeScript

### JavaScript

```js
function getProperty(obj, key) {
    return obj[key];
}

const student = {
    name: "Rakib",
    age: 22
};

getProperty(student, "name");
```

### TypeScript

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}

const student = {
    name: "Rakib",
    age: 22
};

getProperty(student, "name");
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| Generic নেই | Generic আছে |
| Key-এর type checking নেই | `keyof` দিয়ে key check করা যায় |
| Invalid key runtime-এ সমস্যা করতে পারে | Invalid key compile-time-এ detect করা যায় |
| Static type safety নেই | Static type safety আছে |

---

# Part 10 — Core Concept Analysis

Advanced Generics JavaScript-এর runtime feature নয়।

### TypeScript

```ts
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}
```

### Compiled JavaScript

```js
function getProperty(obj, key) {
    return obj[key];
}
```

### 🔍 What Changed?

```text
TypeScript
→ Generic Parameters
→ Constraints
→ keyof
→ Type Safety

JavaScript
→ শুধু Runtime Logic
```

> Generics, Constraints এবং `keyof` compile-time type checking-এর জন্য ব্যবহৃত হয়। এগুলো JavaScript runtime-এ থাকে না।

---

# Part 11 — Common Mistakes

## ❌ Mistake 1 — Constraint না মেনে Type ব্যবহার করা

```ts
function getLength<T extends { length: number }>(value: T): number {
    return value.length;
}

getLength(100); // ❌
```

`number`-এর `length` property নেই।

---

## ❌ Mistake 2 — Invalid Key ব্যবহার করা

```ts
const student = {
    name: "Rakib",
    age: 22
};

getProperty(student, "salary"); // ❌
```

`salary` Student Object-এর valid key নয়।

---

## ❌ Mistake 3 — Default Type এবং Constraint গুলিয়ে ফেলা

```text
T extends string
→ T must be string-compatible

T = string
→ T না দিলে string হবে
```

---

# ⚡ Quick Revision

```text
Generic Constraint
→ T extends ...

keyof
→ Object-এর valid keys বের করে

Default Generic
→ T = ...

Constraint
→ Type Restrict করে

Default
→ Fallback Type দেয়

Advanced Generics
→ Reusable + Flexible + Type Safe
```

### 🧠 Memory Trick

```text
extends
→ Restrict

keyof
→ Keys

=
→ Default
```

---

# 🎯 Interview Questions

## Q1. What is a Generic Constraint?

**Answer:**

Generic Constraint ব্যবহার করে Generic Type-কে নির্দিষ্ট type বা structure-এর মধ্যে সীমাবদ্ধ করা হয়। সাধারণত `extends` keyword ব্যবহার করা হয়।

---

## Q2. What does `keyof` do in TypeScript?

**Answer:**

`keyof` কোনো Object Type-এর সব valid property key-কে একটি Union Type হিসেবে তৈরি করে।

```ts
type User = {
    name: string;
    age: number;
};

type Keys = keyof User;

// "name" | "age"
```

---

## Q3. What is a Default Generic Type?

**Answer:**

Generic Type-এর জন্য কোনো type argument দেওয়া না হলে যে type automatically ব্যবহৃত হয়, সেটিই Default Generic Type।

```ts
type Response<T = string> = {
    data: T;
};
```