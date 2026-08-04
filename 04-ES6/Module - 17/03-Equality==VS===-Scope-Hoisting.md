# JavaScript Equality, Scope & Hoisting

> **Module:** 17 - JavaScript Fundamentals  
> **Class:** 03/10  
> **Topic:** `==` vs `===`, Scope and Hoisting

---

# 📚 What I Learned Today

- Loose Equality (`==`)
- Strict Equality (`===`)
- Type Coercion
- Global Scope
- Function Scope
- Block Scope
- Hoisting
- Temporal Dead Zone (TDZ)

---

# 📖 Equality Operators

JavaScript-এ দুই ধরনের Equality Operator আছে।

- `==` (Loose Equality)
- `===` (Strict Equality)

---

# 🔹 Loose Equality (`==`)

**Loose Equality (`==`)** (Compare করার আগে JavaScript প্রয়োজনে Type Convert করে তারপর Compare করে।)

এটিকে **Implicit Type Conversion** বা **Type Coercion** বলা হয়।

---

## Syntax

```javascript
value1 == value2;
```

---

## Example 1

```javascript
console.log(5 == "5");
```

### Output

```text
true
```

কারণ JavaScript `"5"` কে Number `5`-এ Convert করে।

---

## Example 2

```javascript
console.log(0 == false);
```

### Output

```text
true
```

কারণ

```javascript
false
```

Compare করার আগে

```javascript
0
```

হয়ে যায়।

---

## Example 3

```javascript
console.log(null == undefined);
```

### Output

```text
true
```

Loose Equality-তে JavaScript এই দুইটিকে সমান ধরে।

---

# 🔹 Strict Equality (`===`)

**Strict Equality (`===`)** (Type এবং Value—দুটিই একই হলে তবেই `true` Return করে।)

এখানে কোনো Type Conversion হয় না।

---

## Syntax

```javascript
value1 === value2;
```

---

## Example 1

```javascript
console.log(5 === "5");
```

### Output

```text
false
```

কারণ—

- Number ≠ String

Type আলাদা।

---

## Example 2

```javascript
console.log(0 === false);
```

### Output

```text
false
```

কারণ—

Number এবং Boolean একই Type নয়।

---

## Example 3

```javascript
console.log(null === undefined);
```

### Output

```text
false
```

কারণ—

দুইটির Type-ও আলাদা, Value-ও আলাদা।

---

# 💡 Best Practice

সবসময় `===` ব্যবহার করার চেষ্টা করো।

কারণ—

- More Predictable
- More Secure
- Less Bug
- No Unexpected Type Conversion

---

# 📊 `==` vs `===`

| Feature | `==` (Loose Equality) | `===` (Strict Equality) |
|---------|------------------------|--------------------------|
| Type Check | ❌ No | ✅ Yes |
| Value Check | ✅ Yes | ✅ Yes |
| Type Conversion | ✅ Yes | ❌ No |
| Predictable | ❌ Less | ✅ More |
| Recommended | ❌ No | ✅ Yes |

---

# 🌍 Real-Life Analogy

## 🤝 `==` (Loose Equality)

একজন শিক্ষক বললেন—

> "বাংলা বা English—যেভাবেই লিখো, উত্তর মিললে ঠিক।"

অর্থাৎ Format আলাদা হলেও Accept করা হবে।

এটি Flexible, কিন্তু মাঝে মাঝে Confusing হতে পারে।

---

## 📏 `===` (Strict Equality)

একজন শিক্ষক বললেন—

> "ঠিক একই ভাষা, একই Format এবং একই উত্তর হলে তবেই Marks।"

অর্থাৎ—

- Type একই
- Value একই

হলেই `true`।

---

# 📖 What is Scope?

**Scope** (কোন Variable কোথা থেকে Access করা যাবে, সেই সীমাকে Scope বলে।)

JavaScript-এ প্রধানত ৩ ধরনের Scope আছে।

1. Global Scope
2. Function Scope
3. Block Scope

---

# 🌍 Global Scope

**Global Scope** (যে Variable পুরো Program-এর যেকোনো জায়গা থেকে Access করা যায়।)

---

## Example

```javascript
let name = "Rakib";

function greet() {
  console.log(name);
}

greet();

console.log(name);
```

### Output

```text
Rakib
Rakib
```

কারণ `name` Global Scope-এ Declare করা হয়েছে।

---

# 🔹 Function Scope

**Function Scope** (Function-এর ভিতরে Declare করা Variable শুধুমাত্র সেই Function-এর ভিতরেই ব্যবহার করা যায়।)

---

## Example

```javascript
function test() {
  let age = 22;

  console.log(age);
}

test();

console.log(age);
```

### Output

```text
22
ReferenceError
```

কারণ `age` Function-এর বাইরে নেই।

---

# 🔹 Block Scope

**Block Scope** ( `{}` এর ভিতরে Declare করা `let` এবং `const` Variable শুধুমাত্র সেই Block-এর ভিতরেই Access করা যায়।)

---

## Example

```javascript
if (true) {
  let city = "Dhaka";

  console.log(city);
}

console.log(city);
```

### Output

```text
Dhaka
ReferenceError
```

---

# 📝 Important Note

- `let` → Block Scoped ✅
- `const` → Block Scoped ✅
- `var` → Function Scoped ✅

তাই আধুনিক JavaScript-এ `let` এবং `const` ব্যবহার করাই Best Practice।


---

# 📖 What is Hoisting?

**Hoisting** (JavaScript Code Execute হওয়ার আগে Variable এবং Function Declaration-কে Memory-তে উপরে তুলে রাখার Process-কে Hoisting বলে।)

> **মনে রাখো:** Hoisting শুধুমাত্র Declaration-এর ক্ষেত্রে কাজ করে, Initialization-এর ক্ষেত্রে নয়।

---

# 🔹 Hoisting with `var`

`var` Hoist হয় এবং শুরুতে `undefined` দিয়ে Initialize হয়।

## Example

```javascript
console.log(a);

var a = 10;
```

### JavaScript Internally Thinks

```javascript
var a;

console.log(a);

a = 10;
```

### Output

```text
undefined
```

---

# 🔹 Hoisting with `let`

`let`-ও Hoist হয়, কিন্তু **Temporal Dead Zone (TDZ)**-এ থাকে।

Declare করার আগে Access করলে Error দেয়।

## Example

```javascript
console.log(age);

let age = 22;
```

### Output

```text
ReferenceError
```

---

# 🔹 Hoisting with `const`

`const`-এর Behavior `let`-এর মতোই।

## Example

```javascript
console.log(PI);

const PI = 3.1416;
```

### Output

```text
ReferenceError
```

---

# ⚠️ Temporal Dead Zone (TDZ)

**Temporal Dead Zone (TDZ)** (Variable Hoist হওয়ার পর থেকে Declare হওয়া পর্যন্ত যে সময়ে Variable Access করা যায় না, সেই অংশকে TDZ বলে।)

```
Hoisted
   │
   ▼
───────────────
TDZ
───────────────
let age = 22;
```

TDZ-এর ভিতরে Variable ব্যবহার করলে—

```text
ReferenceError
```

পাওয়া যায়।

---

# 🔹 Function Hoisting

Function Declaration সম্পূর্ণ Body-সহ Hoist হয়।

তাই Declare করার আগেও Function Call করা যায়।

## Example

```javascript
greet();

function greet() {
  console.log("Hello");
}
```

### Output

```text
Hello
```

---

# 📊 Hoisting Comparison

| Keyword | Hoisted | Before Declaration |
|---------|----------|--------------------|
| `var` | ✅ Yes | `undefined` |
| `let` | ✅ Yes | `ReferenceError` |
| `const` | ✅ Yes | `ReferenceError` |
| Function Declaration | ✅ Yes | Works Normally |

---

# 💡 Common Mistakes

## ❌ Mistake 1

```javascript
console.log(user);

let user = "Rakib";
```

অনেকে মনে করে Output হবে `undefined`।

✅ আসলে হবে—

```text
ReferenceError
```

---

## ❌ Mistake 2

```javascript
if (true) {
    let city = "Dhaka";
}

console.log(city);
```

`city` Block-এর বাইরে Access করা যাবে না।

---

## ❌ Mistake 3

```javascript
console.log(5 == "5");
```

`==` ব্যবহার করলে Type Conversion হয়।

Production Code-এ `===` ব্যবহার করাই ভালো।

---

# 💎 Best Practice

- ✅ সবসময় `===` ব্যবহার করো।
- ✅ `let` এবং `const` ব্যবহার করো।
- ✅ `var` এড়িয়ে চলো।
- ✅ Variable ব্যবহার করার আগে Declare করো।
- ✅ Scope সম্পর্কে পরিষ্কার ধারণা রাখো।

---

# 🎯 Interview Questions

### 1. What is the difference between `==` and `===`?

- `==` compares values after type conversion (Loose Equality).
- `===` compares both value and type without type conversion (Strict Equality).

---

### 2. Which equality operator is recommended in JavaScript?

✅ `===` (Strict Equality)

Reason:
- More predictable
- No implicit type conversion
- Fewer bugs

---

### 3. What is Scope?

Scope is the area where a variable can be accessed.

---

### 4. Name the three types of Scope in JavaScript.

- Global Scope
- Function Scope
- Block Scope

---

### 5. Which keywords are Block Scoped?

- `let`
- `const`

---

### 6. Which keyword is Function Scoped?

- `var`

---

### 7. What is Hoisting?

Hoisting is JavaScript's behavior of moving declarations to memory before code execution.

---

### 8. What is TDZ (Temporal Dead Zone)?

The period between hoisting and declaration where a `let` or `const` variable cannot be accessed.

---

### 9. Why does `var` print `undefined` before declaration?

Because `var` is hoisted and initialized with `undefined`.

---

### 10. Can a Function Declaration be called before it is declared?

✅ Yes.

Because Function Declarations are fully hoisted.

---

# 🧠 Memory Trick

## Equality

```text
==
↓

Type Conversion
↓

Loose
```

```text
===
↓

No Conversion
↓

Strict
```

Remember:

> **Double = Flexible**
>
> **Triple = Exact**

---

## Scope

```text
Global
↓
Everywhere

Function
↓
Inside Function

Block
↓
Inside {}
```

---

## Hoisting

```text
var
↓
undefined

let
↓
TDZ

const
↓
TDZ

function
↓
Ready to Call
```

---

# ⚡ One Minute Revision

- `==` → Loose Equality (Type Conversion করে)
- `===` → Strict Equality (Type Conversion করে না)
- Always prefer `===`.
- Global Scope → পুরো Program থেকে Access করা যায়।
- Function Scope → শুধু Function-এর ভিতরে।
- Block Scope → শুধু `{}`-এর ভিতরে।
- `let` এবং `const` → Block Scoped।
- `var` → Function Scoped।
- `var` → Hoisted + `undefined`
- `let` / `const` → Hoisted কিন্তু TDZ-এ থাকে।
- Function Declaration → পুরো Body-সহ Hoisted হয়।

---

# 🔑 Keywords

- Loose Equality
- Strict Equality
- Type Coercion
- Scope
- Global Scope
- Function Scope
- Block Scope
- Hoisting
- Temporal Dead Zone
- TDZ
- Variable Declaration
- Function Declaration

---

# 💪 Practice Tasks

### Task 1

Predict the output:

```javascript
console.log(10 == "10");
console.log(10 === "10");
```

---

### Task 2

Predict the output:

```javascript
console.log(false == 0);
console.log(false === 0);
```

---

### Task 3

What will be the output?

```javascript
console.log(a);

var a = 20;
```

---

### Task 4

What will happen?

```javascript
console.log(age);

let age = 25;
```

---

### Task 5

Identify the Scope of each variable.

```javascript
let global = "A";

function test() {
  let functionVar = "B";

  if (true) {
    let blockVar = "C";

    console.log(global);
    console.log(functionVar);
    console.log(blockVar);
  }
}
```

---

### Task 6

Can this function be called before declaration?

```javascript
sayHello();

function sayHello() {
  console.log("Hello, JavaScript!");
}
```

Explain **why**.

---

# 💎 Mentor Notes

এই ক্লাসটি JavaScript-এর Core Foundation-এর অংশ।

এই তিনটি Topic ভালোভাবে বুঝতে পারলে ভবিষ্যতে—

- DOM Manipulation
- Event Handling
- Functions
- Closures
- Callbacks
- Async JavaScript
- React Components
- React Hooks

বোঝা অনেক সহজ হবে।

> **Golden Rules**
>
> - ✅ Prefer `===` over `==`
> - ✅ Use `let` and `const` instead of `var`
> - ✅ Never access `let`/`const` before declaration
> - ✅ Understand Scope before writing complex functions
> - ✅ Remember: Hoisting moves declarations, **not initializations**