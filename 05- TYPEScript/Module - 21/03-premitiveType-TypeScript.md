# 📚 Module: 21 | 🎓 Class: 03

# Primitive Types in TypeScript

> **Topic:** String, Number, Boolean, Null, Undefined, Symbol & BigInt

---

# 📖 What I Learned Today

- What are Primitive Types
- String
- Number
- Boolean
- Null
- Undefined
- Symbol
- BigInt
- Type Annotation
- Type Inference
- JavaScript vs TypeScript
- Core Concept Analysis
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What are Primitive Types?



Primitive types represent **single, simple values** and are the basic building blocks of data in JavaScript and TypeScript.

Primitive Type হলো এমন data type যা সাধারণত একটি **single এবং simple value** represent করে।

### Main Primitive Types

| Type | Example |
|---|---|
| `string` | `"Hello"` |
| `number` | `100` |
| `boolean` | `true` |
| `null` | `null` |
| `undefined` | `undefined` |
| `symbol` | `Symbol()` |
| `bigint` | `100n` |

> TypeScript JavaScript-এর এই primitive types-গুলোর উপর static type system যোগ করে।

---

# Part 1 — String

## 📌 Definition


`string` is used to represent text or a sequence of characters.

`string` text বা characters-এর sequence represent করতে ব্যবহার করা হয়।

---

# Syntax

### JavaScript

```js
let name = "Rakib";
```

### TypeScript

```ts
let name: string = "Rakib";
```

### 🔍 Difference

```text
JavaScript → Type explicitly declared নয়

TypeScript → : string দিয়ে type declare করা যায়
```

---

# Part 2 — Number

## 📌 Definition



`number` is used for integer and floating-point numeric values.

`number` integer এবং decimal/floating-point number represent করতে ব্যবহার করা হয়।

---

# Syntax

### JavaScript

```js
let age = 22;
let price = 99.99;
```

### TypeScript

```ts
let age: number = 22;
let price: number = 99.99;
```

### 🔍 Difference

TypeScript-এ `number` দিয়ে variable-এর expected data type নির্দিষ্ট করা যায়।

> JavaScript-এ integer এবং decimal-এর জন্য আলাদা type নেই। দুটিই `number`।

---

# Part 3 — Boolean

## 📌 Definition



`boolean` represents one of two values: `true` or `false`.

`boolean` শুধু দুইটি value represent করে:

- `true`
- `false`

---

# Syntax

### JavaScript

```js
let isStudent = true;
```

### TypeScript

```ts
let isStudent: boolean = true;
```

### 🔍 Difference

TypeScript-এ `boolean` দিয়ে নিশ্চিত করা যায় যে variable-এ শুধু `true` অথবা `false` থাকবে।

---

# Part 4 — Null

## 📌 Definition



`null` represents the intentional absence of a value.

`null` ব্যবহার করা হয় যখন ইচ্ছাকৃতভাবে কোনো value নেই বোঝাতে।

---

# Syntax

### JavaScript

```js
let value = null;
```

### TypeScript

```ts
let value: null = null;
```

Nullable value-এর ক্ষেত্রে:

```ts
let name: string | null = null;
```

### 🔍 Difference

TypeScript-এ `strictNullChecks` enabled থাকলে `null` আলাদাভাবে type system-এর মধ্যে handle করতে হয়।

---

# Part 5 — Undefined

## 📌 Definition



`undefined` indicates that a value has not been assigned.

`undefined` সাধারণত বোঝায় যে কোনো variable-এ এখনো value assign করা হয়নি।

---

# Syntax

### JavaScript

```js
let value;
```

### TypeScript

```ts
let value: undefined = undefined;
```

অথবা:

```ts
let value: string | undefined;
```

### 🔍 Difference

TypeScript-এ variable-এর type-এর মধ্যে `undefined` explicitly allow করা যায়।

---

# Part 6 — Symbol

## 📌 Definition



`symbol` creates a unique primitive value.

`symbol` একটি unique primitive value তৈরি করে। প্রতিটি Symbol আলাদা এবং unique।

---

# Syntax

### JavaScript

```js
const id = Symbol("id");
```

### TypeScript

```ts
const id: symbol = Symbol("id");
```

### 🔍 Difference

JavaScript এবং TypeScript-এ Symbol-এর core behavior একই। TypeScript-এ শুধু `symbol` type annotation যোগ করা যায়।

---

# Part 7 — BigInt

## 📌 Definition



`bigint` is used to represent integers larger than the safe limit of the `number` type.

`bigint` খুব বড় integer value represent করতে ব্যবহার করা হয়, যেগুলো `number` type-এর safe integer limit-এর বাইরে যেতে পারে।

---

# Syntax

### JavaScript

```js
const bigNumber = 12345678901234567890n;
```

### TypeScript

```ts
const bigNumber: bigint = 12345678901234567890n;
```

### 🔍 Difference

Core behavior একই। TypeScript-এ `bigint` type explicitly define করা যায়।

> `BigInt` এবং `Number` একসাথে সরাসরি arithmetic operation করা যায় না।

---

# Part 8 — Type Annotation

## 📌 Definition



Type Annotation explicitly tells TypeScript what type a variable should have.

Type Annotation ব্যবহার করে আমরা TypeScript-কে explicitly বলে দিই যে variable-এ কোন type-এর value থাকবে।

---

# Syntax

```ts
let name: string = "Rakib";

let age: number = 22;

let isStudent: boolean = true;
```

### Structure

```text
variableName: type = value
```

---

# Part 9 — Type Inference

## 📌 Definition



Type Inference means TypeScript automatically determines the type from the assigned value.

Type Inference-এর মাধ্যমে TypeScript variable-এর value দেখে নিজে থেকেই তার type বুঝে নেয়।

---

# Example

```ts
let name = "Rakib";
let age = 22;
let isStudent = true;
```

TypeScript automatically understands:

```text
name       → string
age        → number
isStudent  → boolean
```

### 🔍 Important

```text
Type Annotation
→ Developer explicitly defines the type

Type Inference
→ TypeScript automatically detects the type
```

---

# Part 10 — JavaScript vs TypeScript

| Core Concept | JavaScript | TypeScript |
|---|---|---|
| String | Supported | Supported + Type Checking |
| Number | Supported | Supported + Type Checking |
| Boolean | Supported | Supported + Type Checking |
| Null | Supported | Supported + Strict Type Checking |
| Undefined | Supported | Supported + Type Checking |
| Symbol | Supported | Supported + Type Checking |
| BigInt | Supported | Supported + Type Checking |
| Type Annotation | ❌ | ✅ |
| Type Inference | Runtime behavior | Compile-time type inference |
| Static Type Checking | ❌ | ✅ |

---

# Part 11 — Core Concept Analysis

## JavaScript

```js
let age = 22;

age = "Twenty Two";
```

JavaScript-এ variable-এর type runtime-এ পরিবর্তিত হতে পারে।

---

## TypeScript

```ts
let age: number = 22;

age = "Twenty Two";
```

এখানে TypeScript error দেখাবে কারণ `age`-এর type `number`।

### মূল পার্থক্য

```text
JavaScript
→ Dynamic Typing

TypeScript
→ Static Typing
→ Type Annotation
→ Compile-time Type Checking
```

---

# Part 12 — Common Mistakes

## ❌ Mistake 1 — Wrong Type

```ts
let age: number = "22";
```

`age` এর type `number`, কিন্তু value দেওয়া হয়েছে `string`।

---

## ❌ Mistake 2 — Boolean-এ String ব্যবহার

```ts
let isStudent: boolean = "true";
```

`"true"` একটি `string`, `true` একটি `boolean`।

Correct:

```ts
let isStudent: boolean = true;
```

---

## ❌ Mistake 3 — Number ও BigInt Mix করা

```ts
let result = 10 + 20n;
```

`number` এবং `bigint` সরাসরি একসাথে arithmetic করা যায় না।

---

# ⚡ Quick Revision

```text
string    → Text
number    → Numeric Values
boolean   → true / false
null      → Intentional absence of value
undefined → Value not assigned
symbol    → Unique primitive value
bigint    → Very large integers
```

### 🧠 Memory Trick

```text
String   → Text
Number   → Number
Boolean  → Yes / No
Null     → No Value
Undefined→ Not Assigned
Symbol   → Unique
BigInt   → Very Large Integer
```

---

# 🎯 Interview Questions

## Q1. What is the difference between Type Annotation and Type Inference?

**Answer:**

Type Annotation-এ developer explicitly type define করে। Type Inference-এ TypeScript assigned value দেখে automatically type determine করে।

---

## Q2. What is the main difference between JavaScript and TypeScript regarding primitive types?

**Answer:**

Primitive types দুটিতেই একই core concept follow করে। মূল difference হলো TypeScript-এর static type system, যার মাধ্যমে variable-এর type explicitly define এবং compile-time-এ check করা যায়।

---

## Q3. What is the difference between `null` and `undefined`?

**Answer:**

`null` সাধারণত ইচ্ছাকৃতভাবে কোনো value নেই বোঝায়, আর `undefined` সাধারণত বোঝায় যে value assign করা হয়নি।