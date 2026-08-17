# 📚 Module: 22 | 🎓 Class: 08

# TypeScript Summary & 10 Important Problems

> **Topic:** TypeScript Core Concepts, JavaScript vs TypeScript & Problem Solving

---

# 📖 What I Learned

- `tsconfig.json`
- `src` & `dist`
- Primitive Types
- Object Types
- Type Alias
- Interface
- Generics
- Generic Constraints
- Default Generic Types
- Enum
- `as const`
- Nullable
- `unknown`
- `never`
- Destructuring
- Rest & Spread
- Function Input & Output
- JavaScript vs TypeScript

---

# Part 1 — TypeScript Core Concepts Summary

| Concept | Main Purpose | TypeScript Feature |
|---|---|---|
| Primitive Types | Basic values | `string`, `number`, `boolean` |
| Object Type | Object structure | Property Types |
| Type Alias | Reusable types | `type` |
| Interface | Object/Class structure | `interface` |
| Generics | Reusable type logic | `<T>` |
| Constraints | Restrict Generics | `extends` |
| Default Generics | Default type | `T = string` |
| Enum | Named fixed values | `enum` |
| `as const` | Literal + readonly types | `as const` |
| Nullable | Allow no value | `string \| null` |
| Unknown | Unknown but safe type | `unknown` |
| Never | No possible return | `never` |

---

# Part 2 — JavaScript vs TypeScript

## Core Difference

### JavaScript

```js
let age = 22;

age = "twenty two";
```

### TypeScript

```ts
let age: number = 22;

age = "twenty two"; // ❌
```

### 🔍 Main Change

```text
JavaScript
→ Dynamic Typing
→ Runtime Type Checking

TypeScript
→ Static Typing
→ Compile-time Type Checking
→ Type Safety
```

---

# Part 3 — Core Concepts: JS vs TS

| Topic | JavaScript | TypeScript |
|---|---|---|
| Variable Type | Dynamic | Static |
| Type Annotation | ❌ | ✅ |
| Type Alias | ❌ | ✅ |
| Interface | ❌ | ✅ |
| Generics | ❌ | ✅ |
| Enum | ❌ | ✅ |
| Literal Types | ❌ | ✅ |
| `unknown` | ❌ | ✅ |
| `never` | ❌ | ✅ |
| Type Checking | Runtime | Compile-time |
| `.ts` File | ❌ | ✅ |
| `tsconfig.json` | ❌ | ✅ |

---

# Part 4 — Important Syntax Revision

## Primitive Types

```ts
let name: string = "Rakib";
let age: number = 22;
let isStudent: boolean = true;
```

---

## Object Type

```ts
let student: {
    name: string;
    age: number;
} = {
    name: "Rakib",
    age: 22
};
```

---

## Type Alias

```ts
type Student = {
    name: string;
    age: number;
};
```

---

## Interface

```ts
interface Student {
    name: string;
    age: number;
}
```

---

## Generic

```ts
function identity<T>(value: T): T {
    return value;
}
```

---

## Generic Constraint

```ts
function getLength<T extends { length: number }>(value: T): number {
    return value.length;
}
```

---

## Default Generic

```ts
type Response<T = string> = {
    data: T;
};
```

---

## Enum

```ts
enum Role {
    Admin = "ADMIN",
    User = "USER"
}
```

---

## `as const`

```ts
const roles = ["admin", "user", "guest"] as const;
```

---

## Nullable

```ts
let name: string | null = null;
```

---

## Unknown

```ts
let value: unknown = "Hello";

if (typeof value === "string") {
    console.log(value.toUpperCase());
}
```

---

## Never

```ts
function fail(message: string): never {
    throw new Error(message);
}
```

---

# Part 5 — Destructuring, Rest & Spread

## Destructuring

```ts
const student = {
    name: "Rakib",
    age: 22
};

const { name, age } = student;
```

## Rest

```ts
const numbers = [10, 20, 30, 40];

const [first, ...rest] = numbers;
```

## Spread

```ts
const numbers = [10, 20, 30];

const newNumbers = [...numbers, 40];
```

### 🧠 Memory Trick

```text
Destructuring → Take Out

Rest → Collect

Spread → Expand
```

---

# Part 6 — Function Input & Output

```ts
function add(a: number, b: number): number {
    return a + b;
}
```

```text
Input
→ Parameters

Output
→ Return Value
```

---

# Part 7 — 10 Important Problems

## Problem 01 — Primitive Types

Create a TypeScript variable for:

- Your name
- Your age
- Whether you are a student

Use the correct primitive types.

---

## Problem 02 — Object Type

Create a `Student` object with:

```text
name → string
age → number
department → string
isStudent → boolean
```

Define the Object Type explicitly.

---

## Problem 03 — Type Alias

Create a reusable `Product` type with:

```text
name → string
price → number
available → boolean
```

Then create two different products using the same Type Alias.

---

## Problem 04 — Interface

Create a `User` Interface with:

```text
id → number
name → string
email → string
age → optional number
```

Create an object using the Interface.

---

## Problem 05 — Generic Function

Create a generic function named `identity` that:

- Accepts any type
- Returns the same type
- Maintains type safety

Test it with a `number` and a `string`.

---

## Problem 06 — Generic Constraint

Create a generic function named `getLength` that accepts only values having a `length` property.

Test it with:

```ts
"TypeScript"
```

and:

```ts
[10, 20, 30]
```

Do not allow a `number`.

---

## Problem 07 — `keyof` + Generics

Create:

```ts
const student = {
    name: "Rakib",
    age: 22,
    department: "Chemistry"
};
```

Create a generic function that receives:

```text
Object
+
Valid Object Key
```

and returns the corresponding property value.

---

## Problem 08 — Enum

Create an `OrderStatus` enum with:

```text
Pending
Shipped
Delivered
Cancelled
```

Use string values for the enum members.

Then create a variable that can only contain an `OrderStatus`.

---

## Problem 09 — `as const`

Create an object:

```text
ADMIN → "admin"
USER → "user"
GUEST → "guest"
```

Use `as const` so that:

- Exact literal values are preserved.
- Properties become readonly.

---

## Problem 10 ⭐ — Combined Problem

Create a TypeScript function that receives a list of users.

Each user should contain:

```text
id → number
name → string
role → "admin" | "user"
age → optional number
```

Requirements:

1. Create the user structure using either `type` or `interface`.
2. Use a generic function to return the users.
3. Use `role` as a Literal Type.
4. Use destructuring to extract `name` and `role`.
5. Use `map()` with the users.
6. Maintain complete type safety.

---

# ⚡ One-Minute Revision

```text
Primitive
→ string, number, boolean, null, undefined, symbol, bigint

Object
→ Key-value structure

Type Alias
→ Reusable Custom Type

Interface
→ Object/Class Structure

Generics
→ Reusable + Type Safe

Constraint
→ Restrict Generic

Default Generic
→ Fallback Type

Enum
→ Named Fixed Values

as const
→ Literal + Readonly

Nullable
→ Type + null / undefined

unknown
→ Unknown but Type Safe

never
→ Never Successfully Returns

Destructuring
→ Take Out

Rest
→ Collect

Spread
→ Expand

Function
→ Input + Output
```

---

# 🧠 Final Memory Map

```text
                    TypeScript
                         │
        ┌────────────────┼────────────────┐
        │                │                │
     Basic Types     Custom Types      Advanced
        │                │                │
 Primitive          Type Alias        Generics
 Object             Interface         Constraints
 Tuple                               Default Types
                                      keyof
                                      Enum
                                      as const
        │
        └────────────── Functions ──────────────┐
                                                │
                                      Input → Parameter
                                      Output → Return
```

---

# 🎯 Important Interview Questions

## Q1. What is the main difference between JavaScript and TypeScript?

**Answer:**

JavaScript is dynamically typed, while TypeScript adds a static type system that checks types during compile time.

---

## Q2. What is the difference between Interface and Type Alias?

**Answer:**

দুটো দিয়েই Object structure define করা যায়। Type Alias primitive, union এবং intersection type-ও define করতে পারে। Interface মূলত Object/Class structure-এর জন্য বেশি ব্যবহৃত হয় এবং `extends` ও declaration merging support করে।

---

## Q3. Why are Generics useful?

**Answer:**

Generics একই logic বিভিন্ন data type-এর সাথে ব্যবহার করার সুযোগ দেয় এবং একই সাথে type safety বজায় রাখে।

---

## Q4. What is the difference between `unknown` and `any`?

**Answer:**

`unknown` value ব্যবহার করার আগে type check করতে হয়, কিন্তু `any` সরাসরি ব্যবহার করা যায়। তাই `unknown` বেশি type-safe।

---

## Q5. What does `as const` do?

**Answer:**

`as const` exact literal type preserve করে এবং Object properties বা Array elements-কে readonly হিসেবে treat করে।

---

# 🔑 Keywords

- TypeScript
- Static Typing
- Type Annotation
- Type Inference
- Primitive Types
- Object Types
- Type Alias
- Interface
- Generics
- Generic Constraints
- `keyof`
- Default Generic
- Enum
- `as const`
- Nullable
- `unknown`
- `never`
- Destructuring
- Rest
- Spread
- Function
- Type Safety
```