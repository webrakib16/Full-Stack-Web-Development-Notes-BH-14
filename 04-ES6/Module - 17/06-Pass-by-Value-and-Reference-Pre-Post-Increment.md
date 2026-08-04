# 📘 Module 17 - Class 06
# Pass by Value vs Pass by Reference | Reassign vs Mutate | Pre & Post Increment

> **Module:** 17 - JavaScript Fundamentals  
> **Class:** 06/10  
> **Topic:** Pass by Value vs Pass by Reference | Reassign vs Mutate | Pre & Post Increment
 


---

# 📚 What I Learned Today

- Pass by Value
- Pass by Reference
- Primitive vs Non-Primitive Memory
- Function Parameter Behavior
- Reassign vs Mutate
- Stack & Heap Memory
- Pre Increment (++x)
- Post Increment (x++)
- Pre Decrement (--x)
- Post Decrement (x--)
- Return Value vs Final Value

---

# What is Pass by Value?

**Definition**

Pass by Value means JavaScript sends a **copy** of the original value to the function.

**বাংলা অর্থ**

(ফাংশনের ভিতরে আসল variable যায় না, তার একটি কপি যায়। তাই ভিতরে পরিবর্তন করলেও বাইরের variable পরিবর্তিত হয় না।)

---

## Example

```javascript
let age = 20;

function change(num) {
  num = 100;
}

change(age);

console.log(age);
```

### Output

```javascript
20
```

---

## Memory View

```
Before Function

age
 │
 ▼
20


Inside Function

num
 │
 ▼
20

↓

num = 100

age
 │
 ▼
20

num
 │
 ▼
100
```

দুইটি আলাদা Memory Box তৈরি হয়।

---

# What is Pass by Reference?

**Definition**

Object, Array এবং Function-এর ক্ষেত্রে Variable-এর মধ্যে পুরো Object থাকে না।

Variable শুধু Memory Address (Reference) ধরে রাখে।

**বাংলা অর্থ**

(Object-এর Value কপি হয় না, Memory Address কপি হয়।)

---

## Example

```javascript
let person = {
    name: "Rakib"
};

function change(obj){
    obj.name = "Hasan";
}

change(person);

console.log(person.name);
```

### Output

```javascript
Hasan
```

---

## Memory View

```
person
   │
   ▼
┌────────────┐
│ name:Rakib │
└────────────┘

obj
 │
 └──────────────► Same Object
```

দুইটা Variable একই Object-কে নির্দেশ করছে।

---

# Important Interview Truth

JavaScript actually **does NOT** use true Pass by Reference.

JavaScript follows

> **Pass by Sharing**
>
> অথবা
>
> **Call by Sharing**

অর্থাৎ Reference-এর Copy পাঠানো হয়।

---

# Primitive vs Non Primitive

| Primitive | Non Primitive |
|-----------|---------------|
| Number | Object |
| String | Array |
| Boolean | Function |
| Undefined | Date |
| Null | Map |
| Symbol | Set |
| BigInt | Object |

---

# Primitive Memory

Primitive Value

```
a = 10

b = a

Memory

a → 10

b → 10
```

দুইটা আলাদা Value তৈরি হয়।

---

# Object Memory

```
let a = {
    name:"Rakib"
}

let b = a;
```

Memory

```
a ─────► Object

b ─────► Same Object
```

---

# Reassign vs Mutate

---

## Mutate

Object-এর ভিতরের Property পরিবর্তন করা।

```javascript
let person = {
    name:"Rakib"
};

person.name = "Hasan";
```

এখানে Object একই আছে।

শুধু Property বদলেছে।

---

## Reassign

পুরো Object পরিবর্তন করা।

```javascript
let person = {
    name:"Rakib"
};

person = {
    name:"Hasan"
};
```

এখানে নতুন Object তৈরি হয়েছে।

---

# Difference

| Mutate | Reassign |
|----------|-----------|
| Property Change | Entire Object Change |
| Same Memory | New Memory |
| Original Object Changes | New Object Created |

---

# Stack vs Heap

## Stack Memory

Primitive Value Stack-এ থাকে।

Examples

- Number
- Boolean
- String

---

## Heap Memory

Object Heap-এ থাকে।

Variable শুধু Address ধরে রাখে।

---

# Why Object Changes?

কারণ Function-এর Parameter-ও একই Object-এর Address ধরে রাখে।

```
person

↓

Object

↑

obj
```

দুজনেই একই Object ব্যবহার করছে।

---

# Common Bug

```javascript
let user = {
    age:20
};

let copy = user;

copy.age = 30;

console.log(user.age);
```

Output

```javascript
30
```

কারণ Copy হয়নি।

একই Object।

---

# Safe Copy

Using Spread Operator

```javascript
let copy = {
    ...user
};
```

এখন Primitive Property নিরাপদ।

---

# Shallow Copy

```javascript
const copy = {
    ...user
};
```

Nested Object থাকলে এখনও Shared থাকবে।

---

# Deep Copy

```javascript
structuredClone(user);
```

অথবা

```javascript
JSON.parse(
JSON.stringify(user)
)
```

---

# Pre Increment

```javascript
let x = 5;

console.log(++x);
```

Output

```
6
```

আগে Increment

তারপর Return

---

# Post Increment

```javascript
let x = 5;

console.log(x++);
```

Output

```
5
```

পরে Increment

---

# Memory

```
x=5

console.log(x++)

Return =5

x becomes 6
```

---

# Example

```javascript
let a = 5;

console.log(a++);
console.log(a);
```

Output

```
5
6
```

---

```javascript
let a = 5;

console.log(++a);

console.log(a);
```

Output

```
6
6
```

---

# Decrement

Post

```javascript
x--
```

আগে ব্যবহার

পরে কমে

---

Pre

```javascript
--x
```

আগে কমে

তারপর ব্যবহার

---

# Where Difference Exists?

Difference থাকে

```javascript
let a = x++;

let b = ++x;

return x++;

console.log(++x);

arr[x++];

foo(++x);
```

---

Difference থাকে না

```javascript
x++;

++x;

for(let i=0;i<5;i++)

while(++i<10)
```

শুধু Increment করার জন্য ব্যবহার করলে সাধারণত তেমন পার্থক্য থাকে না।

---

# Real Life Example

## Pass by Value

তোমার National ID-এর ফটোকপি কাউকে দিলে,

সে ফটোকপিতে লিখলে তোমার Original ID পরিবর্তন হবে না।

---

## Pass by Reference

Google Docs-এর একই Link দুইজনকে দিলে,

যে Edit করবে,

সবার Document-এ পরিবর্তন দেখা যাবে।

---

## Reassign

পুরো নতুন খাতা কিনে ফেলা।

---

## Mutate

একই খাতার ভিতরের লেখা পরিবর্তন করা।

---

# Common Mistakes

❌ Object Copy না করে Assignment করা

```javascript
let b = a;
```

---

❌ ভাবা JavaScript Pure Pass by Reference

আসলে নয়।

---

❌ Nested Object Spread দিয়ে পুরো Copy হয় মনে করা

---

❌ x++ আর ++x সব জায়গায় একই ভাবা

---

# Interview Questions

### 1. Pass by Value কী?

Primitive-এর Copy Function-এ যায়।

---

### 2. Pass by Reference কী?

Reference Address Copy হয়।

---

### 3. JavaScript কি সত্যিই Pass by Reference?

না।

এটি **Pass by Sharing** ব্যবহার করে।

---

### 4. Mutate এবং Reassign-এর পার্থক্য কী?

Mutate Property পরিবর্তন করে।

Reassign নতুন Object তৈরি করে।

---

### 5. Stack এবং Heap কী?

Primitive → Stack

Object → Heap

---

### 6. `x++` এবং `++x` এর পার্থক্য কী?

`x++` → আগে বর্তমান Value Return, পরে Increment।

`++x` → আগে Increment, পরে নতুন Value Return।

---

# Memory Trick

🟢 Primitive = Photo Copy

🔵 Object = Google Docs Link

🟡 Mutate = একই খাতায় লেখা বদলানো

🔴 Reassign = নতুন খাতা কেনা

🟣 `x++` = আগে ব্যবহার → পরে +1

🟠 `++x` = আগে +1 → পরে ব্যবহার

---

# One Minute Revision

- Primitive → Copy যায়
- Object → Address Copy যায়
- Object Property Change → Mutate
- New Object → Reassign
- Primitive → Stack
- Object → Heap
- JS → Pass by Sharing
- `x++` → Use → Increment
- `++x` → Increment → Use
- Spread → Shallow Copy
- `structuredClone()` → Deep Copy

---

# Keywords

- Pass by Value
- Pass by Reference
- Pass by Sharing
- Primitive
- Non Primitive
- Stack
- Heap
- Memory Address
- Reference
- Reassign
- Mutate
- Shallow Copy
- Deep Copy
- Increment
- Decrement

---

# Practice Tasks

### Task 1

Pass by Value-এর একটি Example তৈরি করো।

---

### Task 2

Pass by Reference-এর একটি Example লিখো।

---

### Task 3

Mutate এবং Reassign-এর পার্থক্য Code দিয়ে দেখাও।

---

### Task 4

`x++` ও `++x` ব্যবহার করে Output Predict করো।

```javascript
let x = 5;

console.log(x++);
console.log(++x);
console.log(x);
```

---

### Task 5

Spread Operator ব্যবহার করে Object Copy করো।

---

## 🎯 Mentor Notes

> JavaScript শেখার সময় সবচেয়ে বেশি Bug হয় **Object Reference** এবং **Pre/Post Increment** থেকে। তাই সবসময় Memory কল্পনা করে Code Trace করার অভ্যাস করো। এতে Debugging অনেক সহজ হয়ে যাবে।




# ⭐ Extra Important Examples

---

# Example 1: Primitive Doesn't Change

```javascript
let money = 100;

function spend(balance) {
    balance = balance - 20;
}

spend(money);

console.log(money);
```

### Output

```javascript
100
```

✅ কারণ Function শুধু Value-এর Copy পেয়েছে।

---

# Example 2: Object Changes

```javascript
let user = {
    balance: 100
};

function spend(account) {
    account.balance -= 20;
}

spend(user);

console.log(user.balance);
```

### Output

```javascript
80
```

✅ কারণ Function একই Object-এ কাজ করছে।

---

# Example 3: Array Reference

```javascript
let fruits = ["Apple", "Banana"];

function addFruit(arr) {
    arr.push("Orange");
}

addFruit(fruits);

console.log(fruits);
```

### Output

```javascript
["Apple", "Banana", "Orange"]
```

---

# Example 4: Array Safe Copy

```javascript
let fruits = ["Apple", "Banana"];

let copy = [...fruits];

copy.push("Orange");

console.log(fruits);
console.log(copy);
```

### Output

```javascript
["Apple", "Banana"]

["Apple", "Banana", "Orange"]
```

---

# Example 5: Reassign Doesn't Affect Original Object

```javascript
let student = {
    name: "Rakib"
};

function replace(obj) {
    obj = {
        name: "Hasan"
    };
}

replace(student);

console.log(student.name);
```

### Output

```javascript
Rakib
```

✅ কারণ Parameter নতুন Object-কে Point করছে।

---

# Example 6: Mutate Affects Original Object

```javascript
let student = {
    name: "Rakib"
};

function edit(obj) {
    obj.name = "Hasan";
}

edit(student);

console.log(student.name);
```

### Output

```javascript
Hasan
```

---

# Example 7: Nested Object Problem

```javascript
const user = {
    profile: {
        age: 20
    }
};

const copy = {
    ...user
};

copy.profile.age = 30;

console.log(user.profile.age);
```

### Output

```javascript
30
```

⚠️ Spread Operator Deep Copy করে না।

---

# Example 8: Deep Copy

```javascript
const user = {
    profile: {
        age: 20
    }
};

const copy = structuredClone(user);

copy.profile.age = 30;

console.log(user.profile.age);
```

### Output

```javascript
20
```

---

# Example 9: x++

```javascript
let x = 10;

let a = x++;

console.log(a);
console.log(x);
```

### Output

```javascript
10
11
```

---

# Example 10: ++x

```javascript
let x = 10;

let a = ++x;

console.log(a);
console.log(x);
```

### Output

```javascript
11
11
```

---

# Example 11: Loop

```javascript
for (let i = 0; i < 3; i++) {
    console.log(i);
}
```

Output

```text
0
1
2
```

এখানে `i++` এবং `++i`—দুটোই একই Result দেবে।

---

# Example 12: Expression Difference

```javascript
let x = 5;

console.log(10 + x++);
```

Output

```javascript
15
```

Final x

```javascript
6
```

---

```javascript
let x = 5;

console.log(10 + ++x);
```

Output

```javascript
16
```

Final x

```javascript
6
```

---

# Example 13: Function Argument

```javascript
let count = 5;

function print(value) {
    console.log(value);
}

print(count++);
console.log(count);
```

Output

```javascript
5
6
```

---

```javascript
let count = 5;

function print(value) {
    console.log(value);
}

print(++count);
console.log(count);
```

Output

```javascript
6
6
```

---

# Example 14: Reference Equality

```javascript
let a = {
    name: "Rakib"
};

let b = a;

console.log(a === b);
```

Output

```javascript
true
```

---

# Example 15: Different Objects

```javascript
let a = {
    name: "Rakib"
};

let b = {
    name: "Rakib"
};

console.log(a === b);
```

### Output

```javascript
false
```

✅ Value একই হলেও Memory Address আলাদা।

---

# 🧠 Interview Trick Question

```javascript
const obj = {
    name: "Rakib"
};

obj.name = "Hasan";

console.log(obj.name);
```

Output

```javascript
Hasan
```

প্রশ্ন: `const` হওয়া সত্ত্বেও কেন পরিবর্তন হলো?

**Answer:**

`const` Variable-এর Reference পরিবর্তন করতে দেয় না, কিন্তু Object-এর Property পরিবর্তন (Mutate) করতে দেয়।

---

# 🚀 Senior Developer Tip

মনে রাখো—

- Primitive ⇒ Copy
- Object ⇒ Reference Copy
- Spread (`...`) ⇒ Shallow Copy
- `structuredClone()` ⇒ Deep Copy
- `x++` ⇒ আগে Use, পরে Increment
- `++x` ⇒ আগে Increment, পরে Use