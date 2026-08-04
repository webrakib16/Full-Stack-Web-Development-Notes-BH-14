📁 Full-Stack-Web-Development-Notes/
└── 05-JavaScript/
    └── 17.08-slice-and-reduce.md

# Module 17 - Class 08
# Slice() and Reduce()

> **Topic:** `slice()` and `reduce()`

---

# 📖 What I Learned Today

- What is `slice()`
- What is `reduce()`
- Parameters of `slice()`
- Parameters of `reduce()`
- `accumulator`
- `currentValue`
- `initialValue`
- Callback Function
- Original Array vs New Array

---

# Part 1 — slice()

## 📌 Definition

### 🇺🇸 English

`slice()` is an array method that returns a portion (copy) of an array.

### 🇧🇩 বাংলা

`slice()` একটি Array Method যা Array-এর নির্দিষ্ট অংশ কেটে **নতুন Array** হিসেবে Return করে।

> ✅ Original Array পরিবর্তন করে না।

---

# Syntax

```js
array.slice(start, end)
```

---

# Parameters

| Parameter | Meaning |
|-----------|----------|
| start | Starting Index (Included) |
| end | Ending Index (Not Included) |

---

# Important Rule

```
Start Index ✅ Included

End Index ❌ Excluded
```

---

# Example 1

```js
const fruits = [
    "apple",
    "banana",
    "mango",
    "orange",
    "grape"
];

const result = fruits.slice(1,3);

console.log(result);
```

Output

```js
["banana","mango"]
```

---

# Visualization

```
Index

0   1      2      3       4

apple banana mango orange grape

slice(1,3)

Starts from 1 ✅

Stops before 3 ❌

Result

banana
mango
```

---

# Example 2

```js
const numbers=[10,20,30,40,50];

console.log(numbers.slice(2));
```

Output

```js
[30,40,50]
```

👉 End না দিলে শেষ পর্যন্ত কেটে নেয়।

---

# Example 3

```js
const numbers=[10,20,30,40];

console.log(numbers.slice());
```

Output

```js
[10,20,30,40]
```

👉 কোনো Argument না দিলে পুরো Array-এর Copy Return করে।

---

# Example 4

```js
const numbers=[10,20,30,40,50];

console.log(numbers.slice(-2));
```

Output

```js
[40,50]
```

👉 Negative Index শেষ থেকে গণনা শুরু করে।

---

# Original Array

```js
const numbers=[10,20,30];

const newArray=numbers.slice(1);

console.log(numbers);
```

Output

```js
[10,20,30]
```

Original Array অপরিবর্তিত থাকে।

---

# slice() Summary

| Feature | Value |
|---------|--------|
| Returns New Array | ✅ |
| Original Array Changes | ❌ |
| End Included | ❌ |
| End Optional | ✅ |
| Copy Whole Array | `slice()` |

---

# Part 2 — reduce()

## 📌 Definition

### 🇺🇸 English

`reduce()` reduces an array into a single value.

### 🇧🇩 বাংলা

`reduce()` পুরো Array-এর সব Value নিয়ে কাজ করে শেষে **একটি মাত্র Value** Return করে।

---

# Syntax

```js
array.reduce((accumulator,currentValue,index,array)=>{
    return updatedAccumulator;
}, initialValue);
```

---

# Parameters

| Parameter | Meaning |
|-----------|----------|
| accumulator | আগের Result |
| currentValue | বর্তমান Element |
| index | Current Index |
| array | Original Array |
| initialValue | শুরুর Value |

---

# Example 1 — Sum

```js
const numbers=[10,20,30];

const sum=numbers.reduce((accumulator,currentValue)=>{
    return accumulator+currentValue;
},0);

console.log(sum);
```

Output

```js
60
```

---

# Dry Run

```
Initial Value = 0

0 + 10 = 10

10 + 20 = 30

30 + 30 = 60
```

Final Answer

```
60
```

---

# Example 2 — Maximum Number

```js
const numbers=[10,80,20,100,40];

const max=numbers.reduce((accumulator,currentValue)=>{

    return Math.max(accumulator,currentValue);

});

console.log(max);
```

Output

```js
100
```

---

# Example 3 — Product

```js
const numbers=[2,3,4];

const result=numbers.reduce((accumulator,currentValue)=>{

    return accumulator*currentValue;

},1);

console.log(result);
```

Output

```js
24
```

---

# Example 4 — Total Price

```js
const cart=[
    {name:"Laptop",price:50000},
    {name:"Mouse",price:1000},
    {name:"Keyboard",price:3000}
];

const total=cart.reduce((sum,item)=>{

    return sum+item.price;

},0);

console.log(total);
```

Output

```js
54000
```

---

# reduce() Visualization

```
Array

10
20
30
40

↓

Accumulator

0

↓

10

↓

30

↓

60

↓

100

↓

Final Value
```

---

# reduce() Summary

| Feature | Value |
|---------|--------|
| Returns | Single Value |
| Original Array Changes | ❌ |
| Mostly Used For | Sum, Total, Count, Max, Min |

---

# slice() vs reduce()

| slice() | reduce() |
|-----------|-----------|
| Returns Array | Returns One Value |
| Cuts Array | Combines Values |
| Original Array Safe | Original Array Safe |

---

# Common Mistakes

## ❌ Mistake 1

```js
slice(1,3)
```

Expecting

```
banana mango orange
```

Wrong ❌

Correct

```
banana mango
```

 কারণ End Index Include হয় না।

---

## ❌ Mistake 2

Forgetting Initial Value

```js
reduce((acc,curr)=>acc+curr)
```

এটা কাজ করবে, কিন্তু Initial Value দেওয়া Best Practice।

---

## ❌ Mistake 3

Thinking slice() changes original array.

না।

Original Array একই থাকে।

---

# Interview Questions

## Q1

What does slice() return?

**Answer**

A new array.

---

## Q2

Does slice() change original array?

**Answer**

No.

---

## Q3

Is end index included in slice()?

**Answer**

No.

---

## Q4

What does reduce() return?

**Answer**

A single value.

---

## Q5

What is accumulator?

**Answer**

The accumulated result from previous iterations.

---

## Q6

Why use initialValue in reduce()?

**Answer**

To define the starting value and avoid unexpected behavior.

---

# One Minute Revision

✅ `slice()` → Cut Array

✅ Returns New Array

✅ Original Array Safe

✅ End Index Excluded

✅ `slice()` → Copy Whole Array

---

✅ `reduce()` → One Final Value

✅ Sum

✅ Maximum

✅ Product

✅ Total Price

✅ Count

---

# Memory Trick

```
slice()

✂️ Cut Array

↓

New Array



reduce()

📦 Merge Everything

↓

One Value
```

---

# Keywords

- slice()
- reduce()
- accumulator
- currentValue
- initialValue
- callback
- start index
- end index
- array copy
- single value

---

# Practice Tasks

### Task 1

```js
const numbers=[10,20,30,40,50];
```

Get

```js
[20,30]
```

using `slice()`.

---

### Task 2

```js
const fruits=["Apple","Banana","Orange","Mango"];
```

Copy the entire array using `slice()`.

---

### Task 3

```js
const marks=[70,80,90,60];
```

Find the total marks using `reduce()`.

---

### Task 4

```js
const prices=[100,300,200,500];
```

Find the highest price using `reduce()`.

---

### Task 5 ⭐ Assignment Level

```js
const cart=[
{title:"Laptop",price:65000},
{title:"Mouse",price:900},
{title:"Keyboard",price:2500},
{title:"Monitor",price:18000}
];
```

1. Use `slice()` to get the first **2 products**.
2. Use `slice()` to get the last **2 products**.
3. Use `reduce()` to calculate the **total cart price**.
4. Use `reduce()` to find the **highest priced product**.