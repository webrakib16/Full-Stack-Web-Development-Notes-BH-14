Module 21 - Class 04

Non-Primitive Types

«Topic: Array, Object & Tuple»

---

📖 What I Learned Today

- What is Non-Primitive Type
- What is Array
- Array Syntax
- Array Type in TypeScript
- What is Object
- Object Type in TypeScript
- What is Tuple
- Tuple Syntax
- Array vs Object vs Tuple
- JavaScript vs TypeScript
- Common Mistakes
- Quick Revision

---

Part 1 — Non-Primitive Types

📌 Definition

🇺🇸 English

Non-primitive types are used to group multiple values together with structure.

🇧🇩 বাংলা

Primitive types যেমন "number", "string", "boolean" সাধারণত single value represent করে। Non-primitive types ব্যবহার করে একাধিক value-কে structure অনুযায়ী group করা যায়।

Main Types

- Array
- Object
- Tuple

---

Part 2 — Array

📌 Definition

🇺🇸 English

An Array is an ordered list of values that all share the same type.

🇧🇩 বাংলা

Array হলো এমন একটি ordered list যেখানে সাধারণত সব value একই type-এর হয়।

---

Syntax

let numbers: number[] = [10, 20, 30];

let fruits: string[] = ["Apple", "Banana", "Orange"];

---

Important Points

- Array-এর elements সাধারণত একই type-এর হয়।
- Array-এর length flexible।
- Index "0" থেকে শুরু হয়।
- Index ব্যবহার করে value access করা যায়।

numbers[0]; // 10

---

JavaScript vs TypeScript

JavaScript

let numbers = [10, 20, 30];

TypeScript

let numbers: number[] = [10, 20, 30];

«TypeScript-এ "number[]" দিয়ে Array-এর element type নির্দিষ্ট করা যায়।»

---

Part 3 — Object

📌 Definition

🇺🇸 English

An Object is a structure that groups values under named keys.

🇧🇩 বাংলা

Object হলো এমন একটি structure যেখানে বিভিন্ন value-কে named key/property দিয়ে রাখা হয়।

---

Example

let student: {
    name: string;
    age: number;
    isStudent: boolean;
} = {
    name: "Alice",
    age: 22,
    isStudent: true
};

---

Structure

key → property type → value

name      → string  → "Alice"
age       → number  → 22
isStudent → boolean → true

---

JavaScript vs TypeScript

JavaScript

let student = {
    name: "Alice",
    age: 22,
    isStudent: true
};

TypeScript

let student: {
    name: string;
    age: number;
    isStudent: boolean;
} = {
    name: "Alice",
    age: 22,
    isStudent: true
};

«TypeScript-এ Object-এর প্রতিটি property-এর type define করা যায়।»

---

Part 4 — Tuple

📌 Definition

🇺🇸 English

A Tuple is a fixed-length array where each position has its own type.

🇧🇩 বাংলা

Tuple দেখতে Array-এর মতো, কিন্তু প্রতিটি position-এর জন্য নির্দিষ্ট type থাকে এবং order ও length গুরুত্বপূর্ণ।

---

Example

let user: [string, number] = ["Alice", 25];

এখানে:

slot 0 → string → "Alice"
slot 1 → number → 25

---

Important Points

- Fixed order
- Fixed types
- Fixed length
- প্রতিটি position-এর type আলাদা হতে পারে
- ছোট fixed group of related values-এর জন্য useful

---

Part 5 — Array vs Object vs Tuple

Feature| Array| Object| Tuple
Structure| Ordered list| Key-value pairs| Fixed-length list
Data Types| Usually one type| Mixed, per key| Mixed, per position
Order| Flexible| Not guaranteed| Strict, matters
Length| Flexible| Depends on properties| Fixed
Best Use Case| Lists of similar items| Structured records| Small fixed groups

---

Part 6 — Important Syntax

Array

let numbers: number[] = [10, 20, 30];

let fruits: string[] = ["Apple", "Banana", "Orange"];

---

Object

let student: {
    name: string;
    age: number;
} = {
    name: "Alice",
    age: 22
};

---

Tuple

let user: [string, number] = ["Alice", 25];

---

Part 7 — Common Mistakes

❌ Mistake 1 — Wrong Array Type

let numbers: number[] = [10, 20, "30"];

"number[]" হলে সব elements "number" হতে হবে।

---

❌ Mistake 2 — Wrong Object Property Type

let student: {
    name: string;
    age: number;
} = {
    name: "Alice",
    age: "22"
};

"age" অবশ্যই "number" হতে হবে।

---

❌ Mistake 3 — Wrong Tuple Order

let user: [string, number] = [25, "Alice"];

Tuple-এ order এবং type দুটোই match করতে হবে।

---

Part 8 — Quick Revision

Array  → Ordered list → Usually same type → Flexible length

Object → Key-value pairs → Different types allowed per key

Tuple  → Fixed-length array → Fixed order + fixed type per position

Shortcut

Array → Same Type

Object → Named Keys

Tuple → Fixed Order + Fixed Types

---

Part 9 — Interview Questions

Q1. What is the main difference between an Array and a Tuple in TypeScript?

Answer:

Array সাধারণত একই type-এর multiple values রাখে এবং এর length flexible। Tuple-এর length, order এবং প্রতিটি position-এর type নির্দিষ্ট থাকে।

---

Q2. Why is TypeScript Object typing useful?

Answer:

Object-এর প্রতিটি property-এর expected type নির্দিষ্ট করা যায়, ফলে ভুল type-এর value দিলে TypeScript error detect করতে পারে।

---

Q3. When should you use a Tuple instead of an Array?

Answer:

যখন ছোট একটি fixed group of values থাকে এবং প্রতিটি position-এর নির্দিষ্ট type ও order গুরুত্বপূর্ণ, তখন Tuple ব্যবহার করা হয়।