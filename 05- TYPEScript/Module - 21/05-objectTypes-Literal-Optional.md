# 📚 Module: 21 | 🎓 Class: 5

# Object Types, Literal & Optional Properties

> **Topic:** Object Types, Literal Types & Optional Properties

---

# 📖 What I Learned Today

- Object Types
- Object Type Syntax
- Type Alias for Objects
- Literal Types
- Optional Properties
- `?` Operator
- JavaScript vs TypeScript
- Common Mistakes
- Quick Revision
- Interview Questions

---

# Part 1 — Object Types

## 📌 Definition


An Object Type defines the **structure and types of properties** that an object should have.

Object Type দিয়ে একটি object-এর **কোন কোন property থাকবে এবং প্রতিটি property-এর type কী হবে** তা নির্দিষ্ট করে দেওয়া যায়।

---

# Syntax

```ts
let student: {
    name: string;
    age: number;
} = {
    name: "Alice",
    age: 22
};
```

> TypeScript object-এর structure এবং property types check করে।

---

# Type Alias

একই Object Type বারবার ব্যবহার করতে `type` দিয়ে একটি reusable type তৈরি করা যায়।

```ts
type Student = {
    name: string;
    age: number;
};

let student: Student = {
    name: "Alice",
    age: 22
};
```

---

# Part 2 — Literal Types

## 📌 Definition


A Literal Type allows a variable or property to have **only a specific value**.

Literal Type-এ কোনো variable বা property-এর জন্য শুধু **নির্দিষ্ট কিছু value** allow করা যায়।

---

# Example

```ts
let direction: "left" | "right";

direction = "left";  // ✅
direction = "right"; // ✅

direction = "up";    // ❌
```

এখানে `direction` শুধু `"left"` অথবা `"right"` হতে পারবে।

---

# Object with Literal Type

```ts
type User = {
    name: string;
    role: "admin" | "user";
};

let user: User = {
    name: "Alice",
    role: "admin"
};
```

`role` শুধু `"admin"` অথবা `"user"` হতে পারবে।

---

# Part 3 — Optional Properties

## 📌 Definition


An Optional Property is a property that **may or may not exist** in an object.

Optional Property হলো এমন property যা object-এ **থাকতেও পারে, নাও থাকতে পারে**।

---

# Syntax

```ts
type Student = {
    name: string;
    age?: number;
};
```

এখানে `age?` মানে `age` property optional।

---

# Example

```ts
type Student = {
    name: string;
    age?: number;
};

let student1: Student = {
    name: "Alice",
    age: 22
};

let student2: Student = {
    name: "Bob"
};
```

দুটিই valid, কারণ `age` optional।

---

# Important Rule

```text
property: type
→ Required Property

property?: type
→ Optional Property
```

> `?` শুধু property-এর আগে বসে এবং property-টিকে optional করে।

---

# Part 4 — Literal vs Optional Property

| Feature | Literal Property | Optional Property |
|---|---|---|
| Main Purpose | Specific value restrict করা | Property থাকা optional করা |
| Symbol | `"admin" \| "user"` | `?` |
| Example | `role: "admin" \| "user"` | `age?: number` |
| Value | নির্দিষ্ট value(s) | Property থাকলে defined type |
| Can be Missing? | সাধারণত না | হ্যাঁ |

---

# Part 5 — JavaScript vs TypeScript

| Feature | JavaScript | TypeScript |
|---|---|---|
| Object Structure | Explicitly defined নয় | Define করা যায় |
| Property Type | Type checking নেই | Type checking আছে |
| Literal Type | নেই | আছে |
| Optional Property | শুধু object-এ property না দিলেই হয় | `?` দিয়ে explicitly define করা যায় |

---

# Part 6 — Common Mistakes

## ❌ Mistake 1 — Wrong Literal Value

```ts
type User = {
    role: "admin" | "user";
};

let user: User = {
    role: "manager"
};
```

`role` শুধু `"admin"` অথবা `"user"` হতে পারবে।

---

## ❌ Mistake 2 — Forgetting `?`

```ts
type Student = {
    name: string;
    age: number;
};
```

এখানে `age` required। তাই `age` না দিলে error হবে।

Optional করতে:

```ts
type Student = {
    name: string;
    age?: number;
};
```

---

## ❌ Mistake 3 — Wrong Optional Type

```ts
type Student = {
    age?: number;
};

let student: Student = {
    age: "22"
};
```

`age` optional হলেও, property থাকলে তার value অবশ্যই `number` হতে হবে।

---

# ⚡ Quick Revision

```text
Object Type
→ Defines object structure and property types

Literal Type
→ Allows only specific values

Optional Property
→ Property may or may not exist

?
→ Makes an object property optional
```

### 🧠 Memory Trick

```text
Literal  → Which values are allowed?

Optional → Is the property required?
```

---

# 🎯 Interview Questions

## Q1. What is a Literal Type in TypeScript?

**Answer:**

Literal Type কোনো variable বা property-এর value-কে নির্দিষ্ট কিছু value-এর মধ্যে সীমাবদ্ধ করে।

---

## Q2. What does `?` mean in an Object Type?

**Answer:**

`?` property-টিকে optional করে। অর্থাৎ property-টি object-এ থাকতে পারে, আবার নাও থাকতে পারে।

---

## Q3. What is the difference between a Literal Type and an Optional Property?

**Answer:**

Literal Type নির্দিষ্ট কোন value allowed হবে তা control করে, আর Optional Property নির্ধারণ করে property-টি object-এ থাকা বাধ্যতামূলক কি না।