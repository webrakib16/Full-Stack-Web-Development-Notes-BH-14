# 📚 Module: 21 | 🎓 Class: 7

# Destructuring, Rest & Spread

> **Topic:** Destructuring, Rest Operator & Spread Operator in TypeScript

---

# 📖 What I Learned Today

- Destructuring
- Object Destructuring
- Array Destructuring
- Rest Operator
- Spread Operator
- Core JavaScript Concepts in TypeScript
- JavaScript vs TypeScript
- Type Annotation in Destructuring
- Type Annotation with Rest
- TypeScript Syntax Changes
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 TypeScript and JavaScript


TypeScript uses the same core concepts of JavaScript, but adds **static typing** on top of them.

TypeScript-এর core concepts যেমন **Destructuring, Rest এবং Spread** JavaScript-এর মতোই কাজ করে।

মূল difference হলো TypeScript-এ আমরা values-এর **type explicitly define** করতে পারি।

> **JavaScript → Behavior & Syntax**  
> **TypeScript → JavaScript + Type System**

---

# Part 1 — Destructuring

## 📌 Definition



Destructuring is a syntax that allows us to extract values from arrays or properties from objects into separate variables.

Destructuring ব্যবহার করে Array বা Object-এর value/property সরাসরি আলাদা variable-এর মধ্যে নেওয়া যায়।

---

# 1. Object Destructuring

### JavaScript

```js
const student = {
    name: "Rakib",
    age: 22
};

const { name, age } = student;

console.log(name);
console.log(age);
```

### TypeScript

```ts
const student: {
    name: string;
    age: number;
} = {
    name: "Rakib",
    age: 22
};

const { name, age } = student;

console.log(name);
console.log(age);
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| Object structure-এর type define করা হয় না | Object structure-এর type define করা যায় |
| Destructuring syntax একই | Destructuring syntax একই |
| Runtime type checking নেই | Static type checking আছে |

> মূল destructuring syntax পরিবর্তন হয় না। TypeScript মূলত **type information** যোগ করে।

---

# 2. Array Destructuring

### JavaScript

```js
const numbers = [10, 20, 30];

const [first, second, third] = numbers;

console.log(first);
console.log(second);
console.log(third);
```

### TypeScript

```ts
const numbers: number[] = [10, 20, 30];

const [first, second, third] = numbers;

console.log(first);
console.log(second);
console.log(third);
```

### 🔍 Difference

Array destructuring-এর মূল syntax JavaScript ও TypeScript-এ একই।

TypeScript-এ `number[]` দিয়ে Array-এর type নির্দিষ্ট করা হয়েছে।

---

# Part 2 — Rest Operator

## 📌 Definition



The Rest Operator collects multiple values into a single array or object.

Rest Operator একাধিক value-কে একসাথে একটি Array বা Object-এর মধ্যে collect করে।

Rest Operator-এর symbol:

```text
...
```

---

# Rest with Array

### JavaScript

```js
const numbers = [10, 20, 30, 40];

const [first, ...rest] = numbers;

console.log(first);
console.log(rest);
```

Output:

```text
10
[20, 30, 40]
```

### TypeScript

```ts
const numbers: number[] = [10, 20, 30, 40];

const [first, ...rest]: [number, ...number[]] = numbers;

console.log(first);
console.log(rest);
```

### 🔍 Difference

JavaScript:

```js
const [first, ...rest] = numbers;
```

TypeScript:

```ts
const [first, ...rest]: [number, ...number[]] = numbers;
```

TypeScript-এ Rest-এর type-ও define করা যায়।

---

# Rest with Function Parameters

### JavaScript

```js
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}
```

### TypeScript

```ts
function sum(...numbers: number[]): number {
    return numbers.reduce((total, num) => total + num, 0);
}
```

### 🔍 Difference

```text
JavaScript
→ ...numbers

TypeScript
→ ...numbers: number[]
→ : number
```

অর্থাৎ TypeScript-এ:

- Rest parameters-এর type define করা যায়।
- Function-এর return type define করা যায়।

---

# Part 3 — Spread Operator

## 📌 Definition



The Spread Operator expands the elements of an array or the properties of an object.

Spread Operator একটি Array-এর elements অথবা Object-এর properties-কে আলাদা করে spread করে।

Spread Operator-এর symbol:

```text
...
```

> Rest এবং Spread-এর symbol একই, কিন্তু কাজ আলাদা।

---

# Spread with Array

### JavaScript

```js
const numbers = [10, 20, 30];

const newNumbers = [...numbers, 40];

console.log(newNumbers);
```

Output:

```text
[10, 20, 30, 40]
```

### TypeScript

```ts
const numbers: number[] = [10, 20, 30];

const newNumbers: number[] = [...numbers, 40];

console.log(newNumbers);
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| `const newNumbers = [...numbers, 40]` | `const newNumbers: number[] = [...numbers, 40]` |
| Type explicitly define করা হয় না | Type explicitly define করা যায় |
| Spread behavior একই | Spread behavior একই |

---

# Spread with Object

### JavaScript

```js
const student = {
    name: "Rakib",
    age: 22
};

const updatedStudent = {
    ...student,
    department: "Chemistry"
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

const updatedStudent: Student & {
    department: string;
} = {
    ...student,
    department: "Chemistry"
};
```

### 🔍 Difference

Object spread-এর মূল syntax একই থাকে।

TypeScript-এ Object-এর structure এবং নতুন property-এর type define করা যায়।

---

# Part 4 — Rest vs Spread

| Feature | Rest | Spread |
|---|---|---|
| Main Purpose | Values collect করে | Values expand করে |
| Symbol | `...` | `...` |
| Used With | Function parameters / Destructuring | Array / Object |
| Result | Grouped values | Expanded values |
| Example | `...rest` | `...numbers` |

### 🧠 Memory Trick

```text
Rest
→ Collect 📦

Spread
→ Expand ↔️
```

---

# Part 5 — Core Concepts: JavaScript vs TypeScript

| Core Concept | JavaScript | TypeScript |
|---|---|---|
| Destructuring | Supported | Supported |
| Rest | Supported | Supported |
| Spread | Supported | Supported |
| Type Annotation | ❌ | ✅ |
| Static Type Checking | ❌ | ✅ |
| Function Parameter Type | ❌ | ✅ |
| Function Return Type | ❌ | ✅ |
| Object Property Types | ❌ | ✅ |
| Array Element Types | ❌ | ✅ |

---

# Part 6 — What Actually Changes in TypeScript?

### JavaScript

```js
const numbers = [10, 20, 30];

const [first, ...rest] = numbers;
```

### TypeScript

```ts
const numbers: number[] = [10, 20, 30];

const [first, ...rest]: [number, ...number[]] = numbers;
```

### মূল পরিবর্তন

```text
JavaScript
→ Core syntax

TypeScript
→ Same core syntax
→ + Type Annotation
→ + Static Type Checking
```

> TypeScript সাধারণত JavaScript-এর core concept পরিবর্তন করে না; এর উপর **type system** যোগ করে।

---

# Part 7 — Common Mistakes

## ❌ Mistake 1 — Rest এবং Spread-এর কাজ গুলিয়ে ফেলা

```text
Rest   → Collect
Spread → Expand
```

---

## ❌ Mistake 2 — Rest Parameter-এর পরে অন্য Parameter দেওয়া

```ts
function test(...numbers: number[], name: string) {
}
```

Rest parameter সবসময় parameter list-এর **শেষে** থাকতে হবে।

---

## ❌ Mistake 3 — Wrong Rest Type

```ts
function sum(...numbers: number[]): number {
    return numbers.reduce((total, num) => total + num, 0);
}
```

এখানে `numbers` একটি `number[]`।

তাই string value পাঠানো যাবে না।

```ts
sum(10, 20, "30"); // ❌
```

---

# ⚡ Quick Revision

```text
Destructuring
→ Array/Object থেকে values বের করা

Rest
→ Multiple values collect করা

Spread
→ Array/Object-এর values expand করা

TypeScript
→ JavaScript Core Concepts
→ + Type System
```

### 🧠 One-Line Memory

```text
Destructuring → Take Out
Rest          → Collect
Spread        → Expand
```

---

# 🎯 Interview Questions

## Q1. What is the difference between Rest and Spread?

**Answer:**

Rest multiple values-কে একটি collection-এর মধ্যে collect করে। Spread একটি collection-এর values-কে expand করে।

---

## Q2. Does TypeScript change the core behavior of Destructuring, Rest and Spread?

**Answer:**

না। এগুলোর মূল behavior JavaScript-এর মতোই থাকে। TypeScript মূলত type annotation এবং static type checking যোগ করে।

---

## Q3. Where can a Rest Parameter be used?

**Answer:**

Rest Parameter function-এর parameters এবং destructuring-এর ক্ষেত্রে ব্যবহার করা যায়। Function-এ Rest Parameter অবশ্যই শেষ parameter হতে হবে।