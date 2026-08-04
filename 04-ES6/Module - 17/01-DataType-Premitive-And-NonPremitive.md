# JavaScript Data Types (Primitive vs Non-Primitive)

> **Module:** 17 - JavaScript Fundamentals  
> **Class:** 1/10  
> **Topic:** Data Types (Primitive & Non-Primitive)

---

# 📚 What I Learned Today

- What is Data Type?
- Primitive Data Types
- Non-Primitive (Reference) Data Types
- `typeof` Operator
- Memory Storage
- Value Copy vs Reference Copy
- Mutable vs Immutable
- Spread Operator for Copying

---

# 📖 What is a Data Type?

**Data Type** (কোনো Variable-এর মধ্যে কী ধরনের Data সংরক্ষিত আছে তা বোঝায়।)

JavaScript-এ Data প্রধানত দুই ধরনের।

1. Primitive Data Type
2. Non-Primitive (Reference) Data Type

---

# Primitive Data Type

**Primitive Data Type** (যে Data সরাসরি নিজের Value Variable-এর মধ্যে সংরক্ষণ করে।)

Primitive Data Types হলো—

- String
- Number
- Boolean
- Undefined
- Null
- Symbol
- BigInt

---

## Example

```javascript
let name = "Rakib";
let age = 22;
let isStudent = true;
let salary = null;
let result = undefined;
```

---

## typeof Example

```javascript
console.log(typeof name);
console.log(typeof age);
console.log(typeof isStudent);
console.log(typeof result);
console.log(typeof salary);
```

### Output

```text
string
number
boolean
undefined
object
```

> **Important:** `typeof null` → `"object"`  
> এটি JavaScript-এর একটি পুরোনো (Historical) Bug।

---

# Non-Primitive (Reference) Data Type

**Non-Primitive Data Type** (যে Data সরাসরি Value সংরক্ষণ না করে Memory Address বা Reference সংরক্ষণ করে।)

Non-Primitive Data Types হলো—

- Object
- Array
- Function

---

## Example

```javascript
const student = {
  name: "Rakib",
};

const numbers = [10, 20, 30];

function greet() {
  console.log("Hello");
}
```

---

## typeof

```javascript
console.log(typeof student);
console.log(typeof numbers);
console.log(typeof greet);
```

### Output

```text
object
object
function
```

---

# 🧠 Memory Storage

JavaScript-এ Primitive এবং Non-Primitive Data আলাদা উপায়ে Memory-তে Store হয়।

## Primitive Memory

Primitive Variable-এর ভিতরে সরাসরি Value Store হয়।

```text
name
 │
 ▼
"Rakib"
```

Variable নিজেই Value ধরে রাখে।

---

## Non-Primitive Memory

Object, Array এবং Function সরাসরি Variable-এর ভিতরে থাকে না।

Variable শুধুমাত্র Memory Address (Reference) ধরে রাখে।

```text
student
   │
   ▼
Memory Address
      │
      ▼
{
   name: "Rakib"
}
```

---

# 📋 Primitive Copy

Primitive Data Copy করলে নতুন Value তৈরি হয়।

```javascript
let a = 10;
let b = a;

a = 20;

console.log(a);
console.log(b);
```

### Output

```text
20
10
```

### Explanation

- `b` একটি নতুন Value পেয়েছে।
- `a` পরিবর্তন করলেও `b` পরিবর্তন হবে না।

---

# 📋 Object Copy (Reference Copy)

```javascript
const student = {
  name: "Rakib",
};

const student2 = student;

student.age = 22;

console.log(student2);
```

### Output

```javascript
{
  name: "Rakib",
  age: 22
}
```

### Explanation

`student2 = student` করার সময় নতুন Object তৈরি হয়নি।

দুইটি Variable একই Object-এর Reference ধরে রেখেছে।

তাই একটিতে পরিবর্তন করলে অন্যটিতেও সেই পরিবর্তন দেখা যায়।

---

# 📋 Array Copy

```javascript
let arr = [100, 200, 300];

let arr2 = arr;

arr.push(400);

console.log(arr2);
```

### Output

```text
[100, 200, 300, 400]
```

কারণ `arr2` এবং `arr` একই Array-এর Reference ধরে রেখেছে।

---

# 📋 Array Clone Using Spread Operator

```javascript
let arr = [100, 200, 300];

let arr2 = [...arr];

arr.push(400);

console.log(arr2);
```

### Output

```text
[100, 200, 300]
```

এখানে `arr2` একটি নতুন Array।

তাই Original Array পরিবর্তন হলেও Clone পরিবর্তন হয় না।


---

# 🔥 Primitive vs Non-Primitive

| Feature | Primitive | Non-Primitive |
|---------|-----------|---------------|
| Store করে | Value | Reference (Memory Address) |
| Memory | Variable-এর ভিতরে | আলাদা Memory Location |
| Copy | New Value তৈরি হয় | Same Reference Copy হয় |
| Mutable | ❌ Immutable | ✅ Mutable |
| Performance | Fast | তুলনামূলক Slow |
| Examples | String, Number, Boolean | Object, Array, Function |

---

# 🔄 Mutable vs Immutable

## Immutable (পরিবর্তন করা যায় না)

Primitive Data Immutable।

```javascript
let name = "Rakib";

name = "Sakib";

console.log(name);
```

এখানে `"Rakib"` পরিবর্তন হয়নি।

নতুন String `"Sakib"` তৈরি হয়েছে।

---

## Mutable (পরিবর্তন করা যায়)

Object এবং Array Mutable।

```javascript
const student = {
  name: "Rakib",
};

student.age = 22;

console.log(student);
```

### Output

```javascript
{
  name: "Rakib",
  age: 22
}
```

Object-এর ভিতরের Data পরিবর্তন করা গেছে।

---

# 🌍 Real Life Analogy

## Primitive

তুমি বন্ধুকে একটি কাগজে লেখা ফোন নম্বর দিলে।

সে নিজের একটি কপি পেল।

তুমি পরে তোমার কাগজ পরিবর্তন করলেও তার কপিতে কোনো পরিবর্তন হবে না।

➡️ এটা হলো **Value Copy**।

---

## Non-Primitive

তুমি বন্ধুকে তোমার বাসার ঠিকানা দিলে।

তোমরা দুজন একই বাসার Location জানো।

বাসায় কোনো পরিবর্তন হলে দুজনই সেই পরিবর্তন দেখতে পাবে।

➡️ এটা হলো **Reference Copy**।

---

# ⚠️ Common Mistakes

## ❌ Mistake 1

```javascript
let arr2 = arr;
```

অনেকে মনে করে এটি নতুন Copy।

আসলে এটি একই Reference।

---

## ❌ Mistake 2

```javascript
typeof null;
```

অনেকে Output `"null"` আশা করে।

আসল Output

```text
object
```

---

## ❌ Mistake 3

```javascript
typeof [];
```

অনেকে ভাবে Output হবে `"array"`।

আসল Output

```text
object
```

---

## ❌ Mistake 4

Object Copy করার সময় Spread Operator ব্যবহার না করা।

```javascript
const copy = original;
```

এটি Clone নয়।

এটি শুধু Reference Copy।

Clone করতে হবে—

```javascript
const copy = {
  ...original,
};
```

---

# 💡 Best Practice

✅ Primitive Copy করতে সমস্যা নেই।

✅ Object বা Array Copy করার সময় যত সম্ভব Spread Operator (`...`) ব্যবহার করো।

```javascript
const newArray = [...oldArray];

const newObject = {
  ...oldObject,
};
```

---

# 🎯 Interview Questions

### 1. What is a Primitive Data Type?

A Primitive Data Type stores its value directly inside the variable.

---

### 2. What is a Non-Primitive Data Type?

A Non-Primitive Data Type stores a reference (memory address) instead of the actual value.

---

### 3. Name all Primitive Data Types in JavaScript.

- String
- Number
- Boolean
- Undefined
- Null
- Symbol
- BigInt

---

### 4. Name the Non-Primitive Data Types.

- Object
- Array
- Function

---

### 5. What is the output of `typeof null`?

```text
object
```

---

### 6. What is the output of `typeof []`?

```text
object
```

---

### 7. What is the output of `typeof function(){}`?

```text
function
```

---

### 8. Why does changing one object also change another object copied with `=`?

Because both variables point to the same memory reference.

---

### 9. How can you create a copy of an Array?

```javascript
const newArray = [...oldArray];
```

---

### 10. How can you create a copy of an Object?

```javascript
const newObject = {
  ...oldObject,
};
```

---

# 🧠 Memory Trick

```text
Primitive
↓
Value Copy
↓
Independent Copy

Non-Primitive
↓
Reference Copy
↓
Same Memory
```

মনে রাখো—

> **Primitive = নিজের Value**  
> **Non-Primitive = Memory Address (Reference)**

---

# ⚡ One Minute Revision

- Primitive → Value Store করে
- Non-Primitive → Reference Store করে
- Primitive → Immutable
- Non-Primitive → Mutable
- `typeof null` → `"object"`
- `typeof []` → `"object"`
- `typeof function(){}` → `"function"`
- `=` দিয়ে Object Copy করলে Reference Copy হয়
- Spread Operator (`...`) দিয়ে Object/Array Clone করা যায়

---

# 🔑 Keywords

- Data Type
- Primitive
- Non-Primitive
- Reference
- Memory Address
- Value Copy
- Reference Copy
- Mutable
- Immutable
- typeof
- Object
- Array
- Function
- Spread Operator
- Clone

---

# 💪 Practice Tasks

### Task 1

`typeof` ব্যবহার করে নিচের Data Types-এর Output বের করো।

```javascript
"Hello"
100
true
undefined
null
[]
{}
function(){}
```

---

### Task 2

একটি Primitive Variable Copy করে একটি Value পরিবর্তন করো এবং Output দেখো।

---

### Task 3

একটি Object Copy করে Property পরিবর্তন করো এবং Output দেখো।

---

### Task 4

একটি Array Copy করে `push()` ব্যবহার করো এবং Output Observe করো।

---

### Task 5

Spread Operator ব্যবহার করে একটি Object Clone করো এবং প্রমাণ করো যে Original Object পরিবর্তন হলেও Clone পরিবর্তন হয় না।

---

# 💎 Mentor Note

এই ক্লাসটি JavaScript-এর সবচেয়ে গুরুত্বপূর্ণ Foundation ক্লাসগুলোর একটি।

যদি তুমি **Primitive vs Non-Primitive**, **Value Copy vs Reference Copy**, এবং **Memory Reference** ভালোভাবে বুঝে ফেলো, তাহলে ভবিষ্যতে—

- DOM
- API
- React State
- Redux
- Object Manipulation
- Array Methods

শেখা অনেক সহজ হয়ে যাবে।

এই Concept ইন্টারভিউতেও খুবই গুরুত্বপূর্ণ।