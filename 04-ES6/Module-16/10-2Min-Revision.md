# 📘 JavaScript ES6 Essentials (Module 16 Notes)

> **Programming Hero - Module 16**
>
> **Topics Covered:**
> - Default Parameters
> - Template Strings
> - Spread & Rest Operator
> - Arrow Functions
> - Destructuring
> - Object Methods
> - Optional Chaining
> - Object Looping

---

# 1️⃣ Default Parameters

## 📖 What is it?

Default Parameters allow you to assign a default value to a function parameter if no argument is provided.

## ✅ Syntax

```js
function add(a, b = 0) {
  return a + b;
}

console.log(add(10));      // 10
console.log(add(10, 5));   // 15
```

### 🧠 Shortcut

```
No Argument
⬇
Use Default Value
```

**Remember:**
> Default = Backup Value

---

# 2️⃣ Template Strings

## 📖 What is it?

Template Strings make it easy to insert variables and write multiline strings.

## ✅ Syntax

```js
const name = "Rakib";
const age = 22;

console.log(`My name is ${name} and I am ${age} years old.`);
```

## Multiline String

```js
const message = `
Hello
Welcome
Good Morning
`;
```

### 🧠 Shortcut

```
` `  → Template String

${} → Variable
```

**Remember:**
> Backtick = Dynamic String

---

# 3️⃣ Spread Operator (...)

## 📖 What is it?

Spread Operator expands an Array or Object.

## Copy Array

```js
const numbers = [1, 2, 3];

const copy = [...numbers];
```

## Merge Arrays

```js
const a = [1, 2];
const b = [3, 4];

const result = [...a, ...b];
```

## Max Number

```js
Math.max(...numbers);
```

## Copy Object

```js
const user = {
  name: "Rakib"
};

const newUser = {
  ...user
};
```

### 🧠 Shortcut

```
...
↓

Expand Everything
```

**Remember:**
> Spread = Expand

---

# 4️⃣ Rest Operator (...)

## 📖 What is it?

Rest Operator collects multiple values into one array.

## Syntax

```js
function sum(...numbers) {
  console.log(numbers);
}
```

### 🧠 Shortcut

```
...

Collect Values
```

**Remember**

Spread → Expand

Rest → Collect

---

# 5️⃣ Arrow Function

## Normal Function

```js
function add(a, b) {
  return a + b;
}
```

## Arrow Function

```js
const add = (a, b) => {
  return a + b;
};
```

## One Line Return

```js
const add = (a, b) => a + b;
```

## One Parameter

```js
const square = x => x * x;
```

## No Parameter

```js
const hello = () => "Hello";
```

### 🧠 Shortcut

```
=> = Arrow Function
```

**Remember:**
> Arrow = Short Function

---

# 6️⃣ Destructuring

## Object Destructuring

```js
const user = {
  name: "Rakib",
  age: 22
};

const { name, age } = user;
```

## Array Destructuring

```js
const numbers = [10, 20];

const [a, b] = numbers;
```

### 🧠 Shortcut

```
{} → Object

[] → Array
```

**Remember:**
> Destructuring = Extract Values

---

# 7️⃣ Object Methods

## Object.keys()

```js
Object.keys(user);
```

Returns Property Names

---

## Object.values()

```js
Object.values(user);
```

Returns Property Values

---

## Object.entries()

```js
Object.entries(user);
```

Returns Key + Value Pair

---

## Delete Property

```js
delete user.age;
```

---

## Object.seal()

```js
Object.seal(user);
```

Cannot Add or Delete Properties

---

## Object.freeze()

```js
Object.freeze(user);
```

Cannot Add, Delete or Modify

---

### 🧠 Shortcut

| Method | Meaning |
|---------|---------|
| keys() | Property Names |
| values() | Property Values |
| entries() | Both |
| delete | Remove Property |
| seal() | Lock Add/Delete |
| freeze() | Complete Lock |

---

# 8️⃣ Optional Chaining

## Syntax

```js
user?.address?.city;
```

### 🧠 Shortcut

```
?.
↓

Safe Access
```

**Remember:**
> No Error if Property Doesn't Exist

---

# 9️⃣ Object Looping

## Using for...in

```js
for (const key in user) {
  console.log(key);
}
```

## Using Object.entries()

```js
Object.entries(user).forEach(([key, value]) => {
  console.log(key, value);
});
```

### 🧠 Shortcut

```
Object Loop

↓

for...in

OR

Object.entries()
```

---

# 🚀 ES6 Ultimate Revision

| Topic | Remember |
|--------|----------|
| Default Parameter | Backup Value |
| Template String | Backtick + `${}` |
| Spread | Expand |
| Rest | Collect |
| Arrow Function | Short Function |
| Destructuring | Extract |
| Object.keys() | Property Names |
| Object.values() | Property Values |
| Object.entries() | Key + Value |
| delete | Remove Property |
| Object.seal() | No Add/Delete |
| Object.freeze() | Fully Locked |
| Optional Chaining | Safe Access |
| for...in | Object Loop |

---

# 🎯 Interview Cheatsheet

```text
Default     → Backup Value
Template    → Dynamic String
Spread      → Expand
Rest        → Collect
Arrow       → Short Function
Destructure → Extract
Keys        → Property Names
Values      → Property Values
Entries     → Key + Value
Delete      → Remove Property
Seal        → No Add/Delete
Freeze      → Complete Lock
?.          → Safe Access
for...in    → Object Loop
```

---

# 💡 Memory Technique

| Symbol | Meaning |
|---------|----------|
| `...` | Spread / Rest |
| `=>` | Arrow Function |
| `${}` | Template Variable |
| `?.` | Safe Access |
| `{}` | Object Destructuring |
| `[]` | Array Destructuring |

---

## 📌 One Line Summary

> **Default → Backup | Template → Dynamic | Spread → Expand | Rest → Collect | Arrow → Short | Destructure → Extract | Keys → Names | Values → Values | Entries → Both | Delete → Remove | Seal → Lock Add/Delete | Freeze → Fully Lock | Optional Chaining → Safe Access | for...in → Object Loop**