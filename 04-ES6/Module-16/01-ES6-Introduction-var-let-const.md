# ES6 Introduction & var vs let vs const

> 📚 Module: ES6
> 🎓 Class: 1/10


📚 What I Learned Today

- ECMAScript (ES)
- ES6 (ECMAScript 2015)
- Why ES6 was introduced
- ES6 Key Features
- Difference between [var, let, and const]


# 📌 What is ECMAScript (ES)?

# Definition

ECMAScript (JavaScript-এর অফিসিয়াল স্ট্যান্ডার্ড বা নিয়ম) is the official specification that defines how JavaScript should work.
(ECMAScript হলো JavaScript-এর অফিসিয়াল স্পেসিফিকেশন, যা JavaScript কীভাবে কাজ করবে তার নিয়ম নির্ধারণ করে।)

Example -

ECMAScript → Rules
JavaScript → Follows those Rules

⭐Interview Tip

JavaScript is a programming language, while ECMAScript is its official specification.


# 📌 What is ES6?

# Definition

ES6 (ECMAScript 2015) (JavaScript-এর ৬ষ্ঠ বড় সংস্করণ) is the sixth major version of ECMAScript released in 2015.
(ES6 হলো ECMAScript-এর ষষ্ঠ বড় সংস্করণ, যা ২০১৫ সালে প্রকাশিত হয় এবং JavaScript-এ অনেক আধুনিক Feature যোগ করে।)

# Why ES6?

- Cleaner Syntax
- Block Scope
- Better Variable Declaration
- Classes
- Modules
- Arrow Functions

---

# 📌 ES6 Key Features

- let
- const
- Arrow Function
- Template Literal
- Destructuring
- Rest Parameter
- Spread Operator
- Classes
- Modules
- Promises

---

# 📌 var

# Definition

var (ES6-এর আগে Variable Declare করার Keyword) is the old way of declaring variables in JavaScript.
(`var` হলো ES6-এর আগে Variable Declare করার Keyword।)

# Syntax

<!-- js -->
var name = "Rakib";

# Example

<!-- js -->
if (true) {
  var city = "Rajshahi";
}

console.log(city);

✅ Output = Rajshahi


⭐ *Important*

var is **Function Scoped** (শুধুমাত্র Function-এর ভিতরে সীমাবদ্ধ থাকে, Block Scope মানে না।)

---

# 📌 let

# Definition

*let* (যে Variable-এর Value পরে পরিবর্তন হতে পারে) is used to declare a Block Scoped variable.
(`let` দিয়ে এমন Variable Declare করা হয় যার Value পরে পরিবর্তন করা যেতে পারে।)

# Syntax

<!-- JS -->
let age = 22;


# Example

<!--JS -->
if (true) {
  let age = 22;
}

console.log(age);

❌ Output = ReferenceError


⭐ *Important*

`let` is *Block Scoped* (শুধুমাত্র `{}` ব্লকের ভিতরে ব্যবহার করা যায়।)

---

# 📌 const

# Definition

*const* (যে Variable-এর Value পরিবর্তন করা যায় না) is used to declare a constant variable.
(`const` দিয়ে এমন Variable Declare করা হয় যার Value পুনরায় পরিবর্তন করা যায় না।)

# Syntax

<!-- JS -->
const PI = 3.1416;

# Example

<!-- JS -->
const PI = 3.1416;

PI = 10;

❌ Output = TypeError

⭐ **Important**

`const` Declare করার সময় অবশ্যই Value দিতে হবে।

---

# 📊 var vs let vs const

| Feature | `var` | `let` | `const` |
|---------|-------|-------|---------|
| **Scope (কোথায় কাজ করে)** | Function Scope | Block Scope | Block Scope |
| **Redeclare (একই নাম আবার Declare)** | ✅ Yes | ❌ No | ❌ No |
| **Reassign (নতুন Value দেওয়া)** | ✅ Yes | ✅ Yes | ❌ No |
| **Hoisting (Declaration আগে Memory-তে যায়)** | ✅ Yes (`undefined`) | ✅ Yes (TDZ) | ✅ Yes (TDZ) |
| **Initialization Required (Declare-এর সময় Value লাগবে?)** | ❌ No | ❌ No | ✅ Yes |
| **Access Before Declaration** | `undefined` | ❌ ReferenceError | ❌ ReferenceError |
| **Modern JavaScript Usage** | ❌ Avoid | ✅ Recommended | ⭐ Best Choice |

---

# 💎 Best Practice

| Situation | Use |
|-----------|-----|
| Value পরিবর্তন হবে না | ✅ `const` |
| Value পরিবর্তন হবে | ✅ `let` |
| পুরোনো Project | ⚠️ `var` |

---

# 🎯 Interview Questions

### 1. What is ES6?

ES6 is the sixth major version of ECMAScript released in 2015.

---

### 2. What is ECMAScript?

ECMAScript is the official specification of JavaScript.

---

### 3. Which should you use: var, let or const?

✅ Use `const` by default.

✅ Use `let` if the value changes.

❌ Avoid `var`.

---

# ⚠️ Common Mistakes

- Using `var` everywhere.
- Reassigning a `const`.
- Redeclaring `let`.

---

# 🧠 Memory Trick

```text
const ➜ Constant

let ➜ Later Change

var ➜ Very Old
```

---

# ⚡ Quick Revision 

- ES = ECMAScript
- ES6 = ECMAScript 2015
- Released in 2015
- `var` → Function Scope
- `let` → Block Scope
- `const` → Block Scope
- `const` → Default Choice
- `let` → If value changes
- `var` → Avoid

---

# 🔑 Keywords

- ECMAScript
- ES6
- var
- let
- const
- Function Scope
- Block Scope
- Redeclare
- Reassign