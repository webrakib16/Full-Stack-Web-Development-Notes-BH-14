# 📚 Module: 22 | 🎓 Class: 03

# Interface in TypeScript

> **Topic:** Interface & Interface vs Type Alias

---

# 📖 What I Learned Today

- What is Interface
- Interface Syntax
- Interface with Object
- Optional Properties in Interface
- Readonly Properties
- Extending Interface
- Interface vs Type Alias
- JavaScript vs TypeScript
- Core Concept Analysis
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What is an Interface?



An Interface defines the **structure of an object** by specifying its properties and their types.

Interface ব্যবহার করে একটি Object-এর **structure, properties এবং তাদের types** নির্ধারণ করা যায়।

---

# Part 1 — Basic Interface

## Syntax

```ts
interface Student {
    name: string;
    age: number;
}
```

এখন `Student` interface ব্যবহার করে Object তৈরি করা যায়।

```ts
const student: Student = {
    name: "Rakib",
    age: 22
};
```

---

# Part 2 — Interface with Multiple Objects

একই Interface একাধিক Object-এর structure define করতে পারে।

```ts
interface Student {
    name: string;
    age: number;
    department: string;
}

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

> Interface reusable এবং consistent Object structure তৈরি করতে সাহায্য করে।

---

# Part 3 — Optional Properties

Interface-এ `?` ব্যবহার করে কোনো property optional করা যায়।

```ts
interface Student {
    name: string;
    age?: number;
}
```

এখন `age` দেওয়া optional।

```ts
const student: Student = {
    name: "Rakib"
};
```

---

# Part 4 — Readonly Property

`readonly` ব্যবহার করলে property-এর value পরে পরিবর্তন করা যায় না।

```ts
interface User {
    readonly id: number;
    name: string;
}

const user: User = {
    id: 101,
    name: "Rakib"
};
```

```ts
user.name = "Karim"; // ✅
```

কিন্তু:

```ts
user.id = 102; // ❌
```

---

# Part 5 — Extending Interface

একটি Interface অন্য Interface-এর properties inherit করতে পারে।

### Syntax

```ts
interface Person {
    name: string;
    age: number;
}

interface Student extends Person {
    department: string;
}
```

এখন `Student`-এর মধ্যে `Person`-এর properties-ও থাকবে।

```ts
const student: Student = {
    name: "Rakib",
    age: 22,
    department: "Chemistry"
};
```

### Structure

```text
Person
  ↓
Student

Person
→ name
→ age

Student
→ name
→ age
→ department
```

---

# Part 6 — Interface vs Type Alias

## Similar Example

### Interface

```ts
interface Student {
    name: string;
    age: number;
}
```

### Type Alias

```ts
type Student = {
    name: string;
    age: number;
};
```

দুটো দিয়েই একই ধরনের Object structure define করা যায়।

---

# 🔍 Interface vs Type Alias

| Feature | Interface | Type Alias |
|---|---|---|
| Object Structure | ✅ | ✅ |
| Primitive Type Alias | ❌ | ✅ |
| Union Type | ❌ Directly | ✅ |
| Intersection Type | ❌ Directly | ✅ |
| `extends` | ✅ | ❌ |
| Declaration Merging | ✅ | ❌ |
| `implements` | ✅ | ✅ |
| Reusable | ✅ | ✅ |
| Mainly Used For | Object/Class Structure | Any Type |

---

# Part 7 — Union & Intersection

## Type Alias with Union

Type Alias দিয়ে Union Type সহজে তৈরি করা যায়।

```ts
type ID = string | number;
```

Interface দিয়ে এভাবে Union Type define করা যায় না।

---

## Type Alias with Intersection

Type Alias দিয়ে Intersection Type তৈরি করা যায়।

```ts
type Person = {
    name: string;
};

type Student = {
    age: number;
};

type StudentInfo = Person & Student;
```

এখানে `StudentInfo`-তে `name` এবং `age` দুটোই থাকবে।

---

# Part 8 — Extends vs Intersection

### Interface

```ts
interface Person {
    name: string;
}

interface Student extends Person {
    age: number;
}
```

### Type Alias

```ts
type Person = {
    name: string;
};

type Student = Person & {
    age: number;
};
```

### 🔍 Main Difference

```text
Interface
→ extends

Type Alias
→ &
```

দুটোই একাধিক structure combine করতে পারে, কিন্তু syntax আলাদা।

---

# Part 9 — Declaration Merging

Interface একই name দিয়ে একাধিকবার declare করলে properties merge হতে পারে।

```ts
interface User {
    name: string;
}

interface User {
    age: number;
}
```

TypeScript এটিকে এমনভাবে treat করবে:

```ts
interface User {
    name: string;
    age: number;
}
```

> Type Alias একই name দিয়ে আবার declare করা যায় না।

```ts
type User = {
    name: string;
};

type User = {
    age: number;
}; // ❌
```

---

# Part 10 — JavaScript vs TypeScript

### JavaScript

```js
const student = {
    name: "Rakib",
    age: 22
};
```

### TypeScript

```ts
interface Student {
    name: string;
    age: number;
}

const student: Student = {
    name: "Rakib",
    age: 22
};
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| Interface নেই | Interface আছে |
| Object structure explicitly define করা যায় না | Object structure define করা যায় |
| Static type checking নেই | Static type checking আছে |
| Type system নেই | Type system আছে |

---

# Part 11 — Core Concept Analysis

Interface JavaScript-এর runtime feature নয়।

TypeScript code:

```ts
interface Student {
    name: string;
    age: number;
}

const student: Student = {
    name: "Rakib",
    age: 22
};
```

Compiled JavaScript:

```js
const student = {
    name: "Rakib",
    age: 22
};
```

> `interface Student` runtime JavaScript-এ থাকে না। এটি compile-time type checking-এর জন্য ব্যবহৃত হয়।

---

# Part 12 — Common Mistakes

## ❌ Mistake 1 — Required Property Missing

```ts
interface Student {
    name: string;
    age: number;
}

const student: Student = {
    name: "Rakib"
};
```

`age` required property হওয়ায় error হবে।

---

## ❌ Mistake 2 — Wrong Property Type

```ts
interface Student {
    name: string;
    age: number;
}

const student: Student = {
    name: "Rakib",
    age: "22"
};
```

`age` অবশ্যই `number` হতে হবে।

---

## ❌ Mistake 3 — Readonly Property পরিবর্তন করা

```ts
interface User {
    readonly id: number;
}

const user: User = {
    id: 101
};

user.id = 102; // ❌
```

`readonly` property পরে পরিবর্তন করা যায় না।

---

# ⚡ Quick Revision

```text
Interface
→ Object Structure Define করে

?
→ Optional Property

readonly
→ Property পরিবর্তন করা যায় না

extends
→ Interface থেকে অন্য Interface তৈরি/extend করা

interface
→ Mainly Object/Class Structure

type
→ Any Type Define করা যায়

Interface
→ Declaration Merging support করে

Type Alias
→ Union & Intersection সহজে support করে
```

### 🧠 Memory Trick

```text
Interface
→ Object Structure
→ extends
→ Declaration Merging

Type Alias
→ Any Type
→ Union
→ Intersection
```

---

# 🎯 Interview Questions

## Q1. What is the difference between Interface and Type Alias?

**Answer:**

দুটো দিয়েই Object structure define করা যায়। তবে Type Alias primitive, union এবং intersection type-ও define করতে পারে। Interface মূলত Object/Class structure-এর জন্য বেশি ব্যবহৃত হয় এবং `extends` ও declaration merging support করে।

---

## Q2. Can an Interface extend another Interface?

**Answer:**

হ্যাঁ। `extends` keyword ব্যবহার করে একটি Interface অন্য Interface-এর properties inherit করতে পারে।

```ts
interface Person {
    name: string;
}

interface Student extends Person {
    age: number;
}
```

---

## Q3. What is Declaration Merging in Interface?

**Answer:**

একই name-এর একাধিক Interface declaration TypeScript automatically merge করতে পারে। Type Alias একই name দিয়ে পুনরায় declare করা যায় না।