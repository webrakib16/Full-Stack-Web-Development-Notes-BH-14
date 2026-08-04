# JavaScript: Null vs Undefined & Truthy vs Falsy

> **Module:** 17 - JavaScript Fundamentals  
> **Class:** 02/10  
> **Topic:** Null vs Undefined and Truthy vs Falsy Values

---

# 📚 What I Learned Today

- What is `undefined`?
- What is `null`?
- Difference between `null` and `undefined`
- `typeof null` Bug
- Truthy Values
- Falsy Values
- Real-Life Analogy
- Using Truthy/Falsy in `if` Conditions

---

# 📖 What is Undefined?

**Undefined** (যখন কোনো Variable, Function Parameter বা Object Property-এর কোনো Value সেট করা হয়নি, তখন JavaScript স্বয়ংক্রিয়ভাবে `undefined` Assign করে।)

অর্থাৎ—

> **Developer Value দেয়নি → JavaScript নিজে `undefined` দিয়েছে।**

---

## Case 1: Variable Declare করা হয়েছে কিন্তু Value নেই

```javascript
let x;

console.log(x);
```

### Output

```text
undefined
```

---

## Case 2: Function Argument পাঠানো হয়নি

```javascript
function greet(name) {
  console.log(name);
}

greet();
```

### Output

```text
undefined
```

---

## Case 3: Object Property নেই

```javascript
const person = {
  age: 25,
};

console.log(person.city);
```

### Output

```text
undefined
```

---

# 📖 What is Null?

**Null** (Developer ইচ্ছাকৃতভাবে বোঝায় যে এখানে কোনো Value নেই।)

অর্থাৎ—

> **Developer নিজেই Value হিসেবে `null` Assign করেছে।**

---

## Example

```javascript
let user = null;

console.log(user);
```

### Output

```text
null
```

---

# 📝 Simple Meaning

### Undefined

JavaScript বলছে—

> "আমি জানি না এখানে কী থাকবে।"

### Null

Developer বলছে—

> "আমি জানি এখানে কিছুই থাকবে না।"


---

# 🔥 Null vs Undefined

| Feature | Undefined | Null |
|---------|-----------|------|
| কে Assign করে? | JavaScript | Developer |
| Meaning | Value এখনো দেওয়া হয়নি | ইচ্ছাকৃতভাবে Empty রাখা হয়েছে |
| Automatic? | ✅ Yes | ❌ No |
| Type | Primitive | Primitive |
| `typeof` Result | `"undefined"` | `"object"` (Historical Bug) |

---

# ⚠️ Historical Bug

JavaScript-এর শুরুতে একটি Design Bug-এর কারণে—

```javascript
typeof null;
```

### Output

```text
object
```

এটি সঠিক Output নয়।

কিন্তু Backward Compatibility বজায় রাখার জন্য আজও এটি পরিবর্তন করা হয়নি।

---

## Example

```javascript
console.log(typeof undefined);
console.log(typeof null);
```

### Output

```text
undefined
object
```

---

# 🌍 Real Life Analogy

## 📦 Undefined

একটি খালি Box কল্পনা করো।

কেউ এখনো Box-এর ভিতরে কিছু রাখেনি।

```text
📦
Empty
```

Developer এখনও সিদ্ধান্ত নেয়নি কী থাকবে।

---

## 🔒 Null

একটি Box আছে।

কিন্তু Developer ইচ্ছা করে লিখে দিয়েছে—

```text
Nothing Here
```

অর্থাৎ এখানে ইচ্ছাকৃতভাবে কিছু রাখা হবে না।

---

# 📝 Code Example

```javascript
let x;
console.log(x);
```

### Output

```text
undefined
```

---

```javascript
let y = null;

console.log(y);
```

### Output

```text
null
```

---

```javascript
function greet(name) {
  console.log(name);
}

greet();
```

### Output

```text
undefined
```

---

```javascript
const obj = {
  age: 25,
};

console.log(obj.city);
```

### Output

```text
undefined
```

---

# 📖 What are Truthy & Falsy Values?

JavaScript-


---

# ❌ Falsy Values

JavaScript-এ মাত্র **৬টি Value Falsy**।

এগুলো `if` Condition-এ গেলে `false` হিসেবে কাজ করে।

| Value | Description |
|--------|-------------|
| `false` | Boolean False |
| `0` | Zero Number |
| `""` | Empty String |
| `null` | Intentionally Empty |
| `undefined` | Value Not Assigned |
| `NaN` | Not a Number |

---

## Example

```javascript
if (false) {
  console.log("Run");
}

if (0) {
  console.log("Run");
}

if ("") {
  console.log("Run");
}

if (null) {
  console.log("Run");
}

if (undefined) {
  console.log("Run");
}

if (NaN) {
  console.log("Run");
}
```

### Output

```text
Nothing will be printed.
```

কারণ সবগুলোই **Falsy Value**।

---

# ✅ Truthy Values

উপরের ৬টি বাদে **প্রায় সব Value-ই Truthy**।

Examples—

```javascript
true
1
100
-5
"Hello"
"0"
"false"
[]
{}
function () {}
```

সবগুলোই Truthy।

---

# 🤯 Surprising Truthy Values

কিছু Value দেখতে Empty মনে হলেও JavaScript এগুলোকে **Truthy** ধরে।

| Value | Truthy/Falsy |
|--------|--------------|
| `[]` | ✅ Truthy |
| `{}` | ✅ Truthy |
| `"0"` | ✅ Truthy |
| `" "` | ✅ Truthy (Space String) |

---

## Example

```javascript
if ([]) {
  console.log("Truthy");
}

if ({}) {
  console.log("Truthy");
}

if ("0") {
  console.log("Truthy");
}

if (" ") {
  console.log("Truthy");
}
```

### Output

```text
Truthy
Truthy
Truthy
Truthy
```

---

# 📊 Truthy vs Falsy

| Truthy | Falsy |
|---------|--------|
| `true` | `false` |
| `1` | `0` |
| `"Hello"` | `""` |
| `"0"` | `null` |
| `[]` | `undefined` |
| `{}` | `NaN` |
| Function | - |

---

# 🌍 Real-Life Analogy

একটি **Switch** কল্পনা করো।

## 🟢 ON = Truthy

যখন Switch ON থাকে—

- Non-empty String
- Non-zero Number
- Object
- Array

সবকিছু ON হিসেবে কাজ করে।

---

## 🔴 OFF = Falsy

যখন Switch OFF থাকে—

- `false`
- `0`
- `""`
- `null`
- `undefined`
- `NaN`

এগুলো OFF হিসেবে কাজ করে।

---

# 💡 Common Mistakes

## ❌ Mistake 1

```javascript
if ([])
```

অনেকে মনে করে Empty Array Falsy।

✅ আসলে এটি **Truthy**।

---

## ❌ Mistake 2

```javascript
if ({})
```

Empty Object-ও **Truthy**।

---

## ❌ Mistake 3

```javascript
if ("0")
```

অনেকে মনে করে `"0"` মানে Zero, তাই Falsy।

✅ কিন্তু এটি একটি **String**, তাই Truthy।

---

## ❌ Mistake 4

```javascript
if (" ")
```

Space String Empty String নয়।

তাই এটিও **Truthy**।



---

# 🎯 Interview Questions

### 1. What is `undefined`?

`undefined` is a primitive value automatically assigned by JavaScript when a variable has no value, a function argument is missing, or a property does not exist.

---

### 2. What is `null`?

`null` is a primitive value intentionally assigned by the developer to represent an empty value.

---

### 3. What is the difference between `null` and `undefined`?

- `undefined` → Assigned automatically by JavaScript.
- `null` → Assigned intentionally by the developer.

---

### 4. Why does `typeof null` return `"object"`?

Because of a historical bug in JavaScript that remains for backward compatibility.

---

### 5. How many Falsy values are there in JavaScript?

There are **6 Falsy values**:

- `false`
- `0`
- `""`
- `null`
- `undefined`
- `NaN`

---

### 6. Is an Empty Array (`[]`) Truthy or Falsy?

✅ Truthy

---

### 7. Is an Empty Object (`{}`) Truthy or Falsy?

✅ Truthy

---

### 8. Is `"0"` Truthy or Falsy?

✅ Truthy (because it is a non-empty string)

---

### 9. Is `" "` (Space String) Truthy or Falsy?

✅ Truthy

---

### 10. Why are Truthy and Falsy values important?

They are widely used in:

- `if...else`
- Loops
- Ternary Operator
- Logical Operators (`&&`, `||`, `!`)
- Default Values
- Input Validation

---

# 🧠 Memory Trick

## Undefined

> **JavaScript didn't get a value.**

Think:
> "Not Assigned Yet."

---

## Null

> **Developer intentionally made it empty.**

Think:
> "Empty On Purpose."

---

## Falsy

Remember this sentence:

```text
F-0-""-N-U-N
```

Meaning:

- False
- 0
- ""
- Null
- Undefined
- NaN

Only these **6 values** are Falsy.

Everything else is Truthy.

---

# ⚡ One Minute Revision

- `undefined` → JavaScript assigns automatically.
- `null` → Developer assigns intentionally.
- `typeof undefined` → `"undefined"`
- `typeof null` → `"object"` (Historical Bug)
- Only **6 values are Falsy**.
- Empty Array (`[]`) → Truthy
- Empty Object (`{}`) → Truthy
- `"0"` → Truthy
- `" "` → Truthy
- Truthy/Falsy are mainly used in Conditions and Logical Operations.

---

# 🔑 Keywords

- Undefined
- Null
- Primitive
- typeof
- Historical Bug
- Truthy
- Falsy
- Boolean Conversion
- Empty String
- NaN
- Object
- Array
- if Statement
- Logical Operators

---

# 💪 Practice Tasks

### Task 1

Predict the output:

```javascript
let x;
console.log(x);
console.log(typeof x);
```

---

### Task 2

Predict the output:

```javascript
let y = null;

console.log(y);
console.log(typeof y);
```

---

### Task 3

Which of the following are Truthy and which are Falsy?

```javascript
0
1
""
"Hello"
[]
{}
null
undefined
NaN
" "
"0"
false
```

---

### Task 4

Write an `if` statement that checks whether a variable is Truthy.

Example:

```javascript
let userName = "Rakib";

if (userName) {
  console.log("Valid User");
}
```

---

### Task 5

Use the Logical OR (`||`) operator to provide a default value.

Example:

```javascript
let name = "";

let result = name || "Guest";

console.log(result);
```

Output:

```text
Guest
```

---

# 💎 Mentor Notes

এই ক্লাসটি ছোট মনে হলেও JavaScript-এর অন্যতম গুরুত্বপূর্ণ Foundation Topic।

`null`, `undefined`, `truthy`, এবং `falsy` সম্পর্কে পরিষ্কার ধারণা থাকলে ভবিষ্যতে—

- DOM Manipulation
- Form Validation
- API Response Handling
- React Conditional Rendering
- Optional Chaining
- Default Parameters
- Logical Operators (`&&`, `||`, `??`)

বোঝা অনেক সহজ হবে।

> **মনে রাখবে:** JavaScript-এ শুধু ৬টি Value Falsy। বাকি সবকিছুই Truthy।