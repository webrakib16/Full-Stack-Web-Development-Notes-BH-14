# ES6 Destructuring

## 📖 What I Learned Today

- Array Destructuring
- Object Destructuring
- Skip Values
- Rename Variable (Alias)
- Nested Object Destructuring

---

# Definition

**Destructuring** (Array বা Object-এর ভিতরের Value গুলোকে সহজে আলাদা Variable-এ Store করার ES6 Feature।)

---

# Why Destructuring?

### Without Destructuring

```js
const numbers = [10, 20];

const first = numbers[0];
const second = numbers[1];
```

### With Destructuring

```js
const numbers = [10, 20];

const [first, second] = numbers;
```

---

# 1. Array Destructuring

## Syntax

```js
const [value1, value2] = array;
```

### Example

```js
const numbers = [10, 20, 30];

const [first, second] = numbers;

console.log(first, second);
```

**Output**

```text
10 20
```

---

# 2. Skip Values

যে Value দরকার নেই সেখানে শুধু কমা (`,`) ব্যবহার করো।

```js
const numbers = [10, 20, 30, 40, 50];

const [ten, twenty, , , fifty] = numbers;

console.log(ten, twenty, fifty);
```

**Output**

```text
10 20 50
```

---

# 3. Object Destructuring

## Syntax

```js
const { property } = object;
```

### Example

```js
const student = {
  name: "Utsho",
  age: 26
};

const { name, age } = student;

console.log(name, age);
```

**Output**

```text
Utsho 26
```

---

# 4. Rename Variable (Alias)

```js
const student = {
  name: "Utsho",
  age: 26
};

const {
  name: fullName,
  age
} = student;

console.log(fullName, age);
```

**Output**

```text
Utsho 26
```

---

# 5. Nested Object Destructuring

```js
const student = {
  name: "Utsho",
  marks: {
    physics: 95,
    philosophy: 91,
    math: 44
  }
};

const {
  marks: { philosophy }
} = student;

console.log(philosophy);
```

**Output**

```text
91
```

---

# Screenshot Analysis

তুমি লিখেছিলে—

```js
const {
  age,
  name: fullName,
  marks: { philosophy }
} = student;

console.log(age, fullName, marks, philosophy);
```

**Error**

```text
ReferenceError: marks is not defined
```

### কেন?

কারণ

```js
marks: { philosophy }
```

এখানে শুধুমাত্র `philosophy` Variable তৈরি হয়েছে।

`marks` নামে কোনো Variable তৈরি হয়নি।

তাই

```js
console.log(marks);
```

Error দিবে।

---

# Array vs Object Destructuring

| Array | Object |
|-------|--------|
| `[]` ব্যবহার হয় | `{}` ব্যবহার হয় |
| Position অনুযায়ী Value নেয় | Property Name অনুযায়ী Value নেয় |
| Order গুরুত্বপূর্ণ | Property Name গুরুত্বপূর্ণ |

---

# Common Mistakes

❌ ভুল

```js
const { first } = numbers;
```

✅ সঠিক

```js
const [first] = numbers;
```

---

❌ ভুল

```js
const [name] = student;
```

✅ সঠিক

```js
const { name } = student;
```

---

# Interview Questions

### What is Destructuring?

Array বা Object থেকে সহজে Value বের করার ES6 Feature।

### Can we skip values in Array Destructuring?

Yes.

```js
const [a, , c] = arr;
```

### Can we rename properties?

Yes.

```js
const { name: fullName } = student;
```

### What is Nested Object Destructuring?

Object-এর ভিতরের Object থেকে সরাসরি Value বের করা।

---

# Memory Trick

- `[]` → Array
- `{}` → Object
- `,` → Skip Value
- `:` → Rename Variable
- Nested `{}` → Nested Object

---

# One Minute Revision

- ✅ Array → `[]`
- ✅ Object → `{}`
- ✅ Skip → `,`
- ✅ Rename → `property: newName`
- ✅ Nested Object Destructuring সম্ভব

---

# Practice Tasks

### Task 1

```js
const fruits = ["Apple", "Banana", "Orange"];
```

Apple এবং Orange Destructure করে Print করো।

---

### Task 2

```js
const user = {
  name: "Rakib",
  age: 23,
  country: "Bangladesh"
};
```

`name` এবং `country` Destructure করে Print করো।

---

### Task 3

```js
const employee = {
  id: 101,
  info: {
    department: "IT",
    salary: 50000
  }
};
```

Nested Destructuring ব্যবহার করে `salary` Print করো।