
# Module 17 - Class 07
# Array Power Methods (map, forEach, filter, find)

> **Module:** 17 - JavaScript Fundamentals  
> **Class:** 07/10  
> **Topic:** Array Power Methods (`map()`, `forEach()`, `filter()`, `find()`)

---

# 📖 What I Learned Today

- Why Array Methods are better than traditional `for` loop
- `map()`
- `forEach()`
- `filter()`
- `find()`
- Callback Function
- Real-life analogy
- Return value differences
- Common interview questions
- Common mistakes

---

# Why Use Array Methods?

### Definition

Array Methods are built-in JavaScript methods that automatically iterate through every element of an array.

> **বাংলা:** Array Method-এর ভিতরেই loop চলে। তাই আলাদা করে `for` loop লিখতে হয় না।

Instead of telling JavaScript **how** to loop, we only tell it **what** we want to do.

---

# for Loop vs Array Methods

## Using for Loop

```js
const numbers = [1, 2, 3, 4];

const doubled = [];

for (let i = 0; i < numbers.length; i++) {
    doubled.push(numbers[i] * 2);
}

console.log(doubled);
```

### Problems

- More code
- Need index
- Need push()
- More chance of mistakes

---

## Using map()

```js
const numbers = [1,2,3,4];

const doubled = numbers.map(num => num * 2);

console.log(doubled);
```

### Advantages

- Cleaner
- Shorter
- Easier to read
- More professional

---

# Callback Function

## Definition

A callback function is a function passed as an argument into another function.

> **বাংলা:** যে function-কে অন্য একটি function-এর parameter হিসেবে পাঠানো হয় তাকে Callback Function বলে।

Example

```js
numbers.map(num => num * 2);
```

Here

```js
num => num * 2
```

is the callback function.

---

# 1️⃣ map()

## Definition

Creates a new array by transforming every element.

> **বাংলা:** Array-এর প্রতিটি element পরিবর্তন করে নতুন array তৈরি করে।

---

## Syntax

```js
array.map((element, index, array) => {
    return something;
});
```

---

## Parameters

| Parameter | Meaning |
|-----------|----------|
| element | Current value |
| index | Current index |
| array | Original array |

---

## Example 1

```js
const numbers = [1,2,3,4,5];

const doubled = numbers.map(num => num * 2);

console.log(doubled);
```

Output

```js
[2,4,6,8,10]
```

---

## Example 2

```js
const prices = [100,200,300];

const vat = prices.map(price => price + 50);

console.log(vat);
```

Output

```js
[150,250,350]
```

---

## Important Points

- Returns new array ✅
- Original array unchanged ✅
- Length remains same ✅
- Must return value ✅

---

# 2️⃣ forEach()

## Definition

Runs a function for every element but returns nothing.

> **বাংলা:** প্রতিটি element-এর জন্য কাজ করে কিন্তু নতুন array তৈরি করে না।

---

## Syntax

```js
array.forEach((element,index,array)=>{
});
```

---

## Example

```js
const students = ["Rakib","Habib","Rony"];

students.forEach(student=>{
    console.log(student);
});
```

Output

```text
Rakib
Habib
Rony
```

---

## Another Example

```js
const numbers=[10,20,30];

numbers.forEach((num,index)=>{
    console.log(index,num);
});
```

Output

```text
0 10
1 20
2 30
```

---

## Important Points

- No return value
- Returns undefined
- Mostly used for printing
- Mainly used for side effects

---

# 3️⃣ filter()

## Definition

Returns only those elements that satisfy a condition.

> **বাংলা:** যেসব element condition পূরণ করে শুধু সেগুলো নিয়ে নতুন array তৈরি করে।

---

## Syntax

```js
array.filter((element)=>{
    return condition;
});
```

---

## Example 1

```js
const prices=[100,200,300,400,500];

const expensive=prices.filter(price=>price>=400);

console.log(expensive);
```

Output

```js
[400,500]
```

---

## Example 2

```js
const ages=[10,18,20,15,30];

const adults=ages.filter(age=>age>=18);

console.log(adults);
```

Output

```js
[18,20,30]
```

---

## ❗If No Condition Matches

```js
const numbers=[1,2,3];

const result=numbers.filter(num=>num>10);

console.log(result);
```

Output

```js
[]
```

### Important Note

- ❌ No Error
- Returns Empty Array (`[]`)

---

# 4️⃣ find()

## Definition

Returns the first element that matches a condition.

> **বাংলা:** Condition পূরণ করা প্রথম element return করে।

---

## Syntax

```js
array.find((element)=>{
    return condition;
});
```

---

## Example

```js
const students=[
    {name:"Rakib",roll:29},
    {name:"Habib",roll:30},
    {name:"Rony",roll:31}
];

const student=students.find(s=>s.name==="Habib");

console.log(student);
```

Output

```js
{
 name:"Habib",
 roll:30
}
```

---

## Another Example

```js
const numbers=[10,20,30,40];

const result=numbers.find(num=>num>25);

console.log(result);
```

Output

```js
30
```

---

## ❗If No Condition Matches

```js
const numbers=[10,20,30];

const result=numbers.find(num=>num>100);

console.log(result);
```

Output

```js
undefined
```

### Important Note

- ❌ No Error
- Returns `undefined`

---

# Return Value Comparison

| Method | Returns |
|---------|----------|
| map() | New Array |
| forEach() | undefined |
| filter() | New Array |
| find() | First Matching Element অথবা undefined |

---

# Real-Life Analogy

| Method | Example |
|---------|----------|
| map() | সব বইয়ের নতুন Edition তৈরি করা |
| forEach() | উপস্থিতির খাতায় সবাইকে Tick দেওয়া |
| filter() | শুধু পাশ করা ছাত্রদের আলাদা করা |
| find() | প্রথম A+ পাওয়া ছাত্রকে খুঁজে বের করা |

---

# Comparison Table

| Feature | map | forEach | filter | find |
|----------|------|----------|----------|---------|
| Returns New Array | ✅ | ❌ | ✅ | ❌ |
| Returns One Value | ❌ | ❌ | ❌ | ✅ |
| Length Same | ✅ | ❌ | ❌ | ❌ |
| Uses Condition | ❌ | ❌ | ✅ | ✅ |
| Original Array Changes | ❌ | ❌ | ❌ | ❌ |

---

# Interview Questions

## Q1. Difference between map() and forEach()?

**Answer**

- map() returns a new array.
- forEach() returns undefined.

---

## Q2. Difference between filter() and find()?

**Answer**

- filter() returns all matched elements.
- find() returns only the first matched element.

---

## Q3. Which method returns undefined?

**Answer**

`forEach()` এবং `find()` (যখন কিছুই match না করে)

---

## Q4. Which method returns empty array?

**Answer**

`filter()` (যখন কোনো element condition match না করে)

---

## Q5. Which method keeps original array unchanged?

**Answer**

All four methods.

---

# Common Mistakes

### ❌ Forgetting return in map()

Wrong

```js
numbers.map(num=>{
    num*2;
});
```

Correct

```js
numbers.map(num=>{
    return num*2;
});
```

---

### ❌ Expecting forEach() to return array

Wrong

```js
const result=numbers.forEach(num=>num*2);

console.log(result);
```

Output

```js
undefined
```

---

### ❌ Confusing filter() with find()

Wrong

```js
find()
```

when multiple results are needed.

Correct

```js
filter()
```

---

# Memory Trick

```
map()
➡️ Modify Everything

forEach()
➡️ Do Something

filter()
➡️ Keep Matching

find()
➡️ Find First
```

---

# One Minute Revision

- `map()` → Transform every element → New Array
- `forEach()` → Loop only → Returns undefined
- `filter()` → Keep matched elements → New Array
- `find()` → Return first matched element
- `filter()` no match → `[]`
- `find()` no match → `undefined`
- Original array never changes.

---

# Keywords

- Array Method
- Callback Function
- Iteration
- Higher Order Function
- map()
- forEach()
- filter()
- find()
- Return
- Condition
- Undefined
- Empty Array

---

# Practice Tasks

### Task 1

```js
const numbers=[2,4,6,8];
```

Use `map()` to make every number three times bigger.

---

### Task 2

```js
const names=["Rakib","Habib","Rony"];
```

Use `forEach()` to print each name.

---

### Task 3

```js
const ages=[12,15,18,22,25];
```

Use `filter()` to get only adults.

---

### Task 4

```js
const students=[
{name:"Rakib",roll:10},
{name:"Habib",roll:20},
{name:"Rony",roll:30}
];
```

Use `find()` to find the student whose roll is `20`.

---

### Task 5 (Interview Level)

```js
const products=[
{name:"Laptop",price:70000},
{name:"Mouse",price:800},
{name:"Keyboard",price:2500},
{name:"Phone",price:35000}
];
```

1. Create a new array with prices after adding 1000 using `map()`.
2. Print all product names using `forEach()`.
3. Get products costing more than 5000 using `filter()`.
4. Find the first product costing more than 30000 using `find()`.

---

# Mentor Notes 💡

- **`map()`** → Use when you need a transformed array.
- **`forEach()`** → Use when you only need to perform an action (e.g., logging, updating UI).
- **`filter()`** → Use when you need multiple matching elements.
- **`find()`** → Use when you need only the first matching element.
- Prefer these methods over traditional `for` loops for cleaner, more readable, and modern JavaScript.




# 🚀 10 Most Important Practice Examples
## Module 17 - Class 07
### Topic: map(), forEach(), filter(), find()

> এগুলো Programming Hero Assignment, Interview এবং Real Project-এর মতো করে তৈরি করা হয়েছে।

---

# Example 1 — Double Every Number (map)

```js
const numbers = [2, 4, 6, 8, 10];

const doubled = numbers.map(num => num * 2);

console.log(doubled);
```

Output

```js
[4, 8, 12, 16, 20]
```

---

# Example 2 — Student Full Name (map)

```js
const students = [
    { first: "Rakib", last: "Hasan" },
    { first: "Habib", last: "Rahman" },
    { first: "Rony", last: "Islam" }
];

const fullNames = students.map(student => {
    return `${student.first} ${student.last}`;
});

console.log(fullNames);
```

Output

```js
[
"Rakib Hasan",
"Habib Rahman",
"Rony Islam"
]
```

---

# Example 3 — Print Product Information (forEach)

```js
const products = [
    "Laptop",
    "Phone",
    "Mouse"
];

products.forEach(product => {
    console.log(product);
});
```

Output

```text
Laptop
Phone
Mouse
```

---

# Example 4 — Print Index + Value (forEach)

```js
const fruits = ["Apple", "Orange", "Mango"];

fruits.forEach((fruit, index) => {
    console.log(index, fruit);
});
```

Output

```text
0 Apple
1 Orange
2 Mango
```

---

# Example 5 — Expensive Products (filter)

```js
const prices = [100, 500, 800, 200, 900];

const expensive = prices.filter(price => price >= 500);

console.log(expensive);
```

Output

```js
[500,800,900]
```

---

# Example 6 — Adult Students (filter)

```js
const ages = [12,18,25,15,30];

const adults = ages.filter(age => age >= 18);

console.log(adults);
```

Output

```js
[18,25,30]
```

---

# Example 7 — Find User (find)

```js
const users = [
    {id:1,name:"Rakib"},
    {id:2,name:"Habib"},
    {id:3,name:"Rony"}
];

const user = users.find(user => user.id === 2);

console.log(user);
```

Output

```js
{
 id:2,
 name:"Habib"
}
```

---

# Example 8 — Find First Even Number (find)

```js
const numbers = [3,5,7,10,12];

const even = numbers.find(num => num % 2 === 0);

console.log(even);
```

Output

```js
10
```

---

# Example 9 — Validation Task (filter)

## Problem

Return only valid emails.

```js
const emails = [
    "rakib@gmail.com",
    "",
    "habib@yahoo.com",
    null,
    "rony@gmail.com"
];

const validEmails = emails.filter(email => email);

console.log(validEmails);
```

Output

```js
[
"rakib@gmail.com",
"habib@yahoo.com",
"rony@gmail.com"
]
```

📌 **Validation:** Empty string (`""`) এবং `null` বাদ যাবে।

---

# Example 10 — Assignment Level Validation (filter + map + find)

## Problem

একটি Student Array থেকে—

- শুধু পাশ করা Student বের করো
- তাদের Name-এর Array বানাও
- প্রথম GPA 5 Student খুঁজে বের করো

```js
const students = [
    { name: "Rakib", marks: 80, gpa: 5 },
    { name: "Habib", marks: 45, gpa: 3.5 },
    { name: "Rony", marks: 60, gpa: 4 },
    { name: "Sakib", marks: 30, gpa: 2.5 }
];

const passedStudents = students.filter(student => student.marks >= 50);

const names = passedStudents.map(student => student.name);

const topper = students.find(student => student.gpa === 5);

console.log(passedStudents);
console.log(names);
console.log(topper);
```

Output

```js
Passed Students

[
 {name:"Rakib",marks:80,gpa:5},
 {name:"Rony",marks:60,gpa:4}
]

Names

[
"Rakib",
"Rony"
]

Topper

{
name:"Rakib",
marks:80,
gpa:5
}
```

---

# 🔥 Bonus Validation Questions (Assignment Style)

### Task 1

```js
const passwords = [
"abc123",
"",
"hello123",
null,
"123456"
];
```

👉 শুধু valid password রাখো।

---

### Task 2

```js
const products = [
{ name:"Laptop", stock:10 },
{ name:"Mouse", stock:0 },
{ name:"Phone", stock:5 },
{ name:"Keyboard", stock:0 }
];
```

👉 শুধু Available Product বের করো।

---

### Task 3

```js
const users = [
{ name:"Rakib", active:true },
{ name:"Habib", active:false },
{ name:"Rony", active:true }
];
```

👉 শুধু Active User বের করো।

---

### Task 4

```js
const students = [
{ name:"Rakib", marks:80 },
{ name:"Habib", marks:30 },
{ name:"Rony", marks:95 }
];
```

👉 Passed Student-এর Name-এর Array বানাও।

---

### Task 5 ⭐ (Interview Level)

```js
const employees = [
{ name:"Rakib", salary:40000 },
{ name:"Habib", salary:60000 },
{ name:"Rony", salary:80000 },
{ name:"Sakib", salary:30000 }
];
```

একই কোডে—

- Salary ≥ 50000 এমন Employee বের করো (`filter`)
- তাদের Name-এর Array বানাও (`map`)
- প্রথম Salary ≥ 70000 Employee বের করো (`find`)
- `forEach()` ব্যবহার করে প্রতিটি Employee-এর Name print করো।

> 💡 এই শেষ Task-টি Programming Hero assignment, interview এবং real-world project-এর জন্য খুবই গুরুত্বপূর্ণ।



# 🎯 Interview Questions (Module 17 - Class 07)
## Topic: map(), forEach(), filter(), find()

---

# Q1. What is the difference between `map()` and `forEach()`?
## Q1. `map()` আর `forEach()` এর পার্থক্য কী?

### 🇺🇸 English Answer

| map() | forEach() |
|--------|-----------|
| Returns a **new array**. | Returns **undefined**. |
| Used when data needs to be transformed. | Used when you only need to perform an action. |
| Can be chained with other array methods. | Usually not chained because it returns nothing. |

### 🇧🇩 বাংলা উত্তর

| map() | forEach() |
|--------|-----------|
| নতুন Array তৈরি করে। | নতুন Array তৈরি করে না। |
| Data পরিবর্তনের জন্য ব্যবহার করা হয়। | শুধু কোনো কাজ (Print, API Call, DOM Update) করার জন্য ব্যবহার করা হয়। |
| Return করে নতুন Array। | Return করে `undefined`। |

### Example

```js
const numbers = [1, 2, 3];

// map()
const result = numbers.map(num => num * 2);

console.log(result);
// [2,4,6]

// forEach()
const output = numbers.forEach(num => console.log(num));

console.log(output);
// undefined
```

---

# Q2. What is the difference between `filter()` and `find()`?
## Q2. `filter()` আর `find()` এর পার্থক্য কী?

### 🇺🇸 English Answer

| filter() | find() |
|-----------|---------|
| Returns **all matching elements**. | Returns **only the first matching element**. |
| Always returns an array. | Returns a single value or `undefined`. |

### 🇧🇩 বাংলা উত্তর

| filter() | find() |
|-----------|---------|
| Condition অনুযায়ী সব Match করা Element Return করে। | শুধুমাত্র প্রথম Match করা Element Return করে। |
| Return Type → Array | Return Type → Object/Value অথবা `undefined` |

### Example

```js
const numbers = [10, 20, 30, 40, 50];

console.log(numbers.filter(num => num > 20));
// [30,40,50]

console.log(numbers.find(num => num > 20));
// 30
```

---

# Q3. What does `find()` return if nothing is found?
## Q3. `find()` কিছু না পেলে কী ফেরত দেয়?

### 🇺🇸 English Answer

If `find()` cannot find any matching element, it returns **`undefined`**.

### 🇧🇩 বাংলা উত্তর

যদি কোনো Element Condition পূরণ না করে, তাহলে `find()` **Error দেয় না**, বরং **`undefined`** Return করে।

### Example

```js
const numbers = [10, 20, 30];

const result = numbers.find(num => num > 100);

console.log(result);
```

Output

```js
undefined
```

---

# Q4. Do these methods change the original array?
## Q4. এই Method গুলো কি Original Array পরিবর্তন করে?

### 🇺🇸 English Answer

No.

`map()`, `forEach()`, `filter()`, and `find()` do **not** modify the original array.

### 🇧🇩 বাংলা উত্তর

না।

`map()`, `forEach()`, `filter()` এবং `find()` — কোনোটিই Original Array পরিবর্তন করে না।

এগুলো Original Array থেকে Data পড়ে কাজ করে।

### Example

```js
const numbers = [1,2,3];

const doubled = numbers.map(num => num * 2);

console.log(numbers);
// [1,2,3]

console.log(doubled);
// [2,4,6]
```

---

# Q5. What happens if you don't write `return` inside `map()`?
## Q5. `map()` এর ভিতরে `return` না লিখলে কী হয়?

### 🇺🇸 English Answer

If you don't return a value from the callback function, every element becomes **`undefined`**.

### 🇧🇩 বাংলা উত্তর

যদি `map()` Callback Function-এর ভিতরে `return` না লেখো, তাহলে প্রতিটি Element-এর জন্য `undefined` Return হবে।

ফলাফল হিসেবে নতুন Array-এর প্রতিটি Value হবে `undefined`।

### ❌ Wrong Example

```js
const numbers = [1,2,3];

const result = numbers.map(num => {
    num * 2;
});

console.log(result);
```

Output

```js
[undefined, undefined, undefined]
```

### ✅ Correct Example

```js
const numbers = [1,2,3];

const result = numbers.map(num => {
    return num * 2;
});

console.log(result);
```

Output

```js
[2,4,6]
```

---

# 🚀 Interview Quick Revision

| Question | One-Line Answer |
|----------|------------------|
| `map()` vs `forEach()` | `map()` returns a new array, `forEach()` returns `undefined`. |
| `filter()` vs `find()` | `filter()` returns all matches, `find()` returns the first match. |
| `find()` no match? | Returns `undefined`. |
| Do these methods change the original array? | ❌ No. |
| No `return` inside `map()`? | Returns an array filled with `undefined`. |

---

# 🧠 Memory Trick

- ✅ **map() → Make a New Array**
- ✅ **forEach() → Do Something**
- ✅ **filter() → Keep All Matching**
- ✅ **find() → Find the First Match**
- ✅ **No `return` in `map()` → `undefined`**