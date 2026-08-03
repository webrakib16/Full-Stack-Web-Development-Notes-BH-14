 # Default Parameters for Not-Provided Values

> 📚 Module: ES6
> 🎓 Class: 2/10

---

# 📚 What I Learned Today

- Default Parameters
- Why Default Parameters are Needed
- Syntax of Default Parameters
- Default Values in Function Parameters
- ES5 vs ES6 Approach
- `undefined` vs `null`

---

# 📌 What is Default Parameter?

### Definition (English)

A **Default Parameter** is a value assigned to a function parameter that is automatically used when no argument or `undefined` is passed.

### সংজ্ঞা (বাংলা)

**Default Parameter** হলো Function-এর Parameter-এর জন্য আগে থেকেই নির্ধারিত একটি Value, যা Argument না দিলে বা `undefined` দিলে স্বয়ংক্রিয়ভাবে ব্যবহার হয়।

---

# ❓ Why Use Default Parameters?

Before ES6, if a function was called without passing all arguments, the missing parameters became `undefined`.

Developers had to write extra code to handle missing values.

Default Parameters solve this problem by automatically assigning a fallback value.

(ES6-এর আগে কোনো Function-এ Argument না দিলে Parameter-এর Value `undefined` হয়ে যেত। তখন অতিরিক্ত Code লিখে Value Handle করতে হতো। Default Parameter এই সমস্যার সমাধান করে।)

---

# 💻 Syntax

```js
function functionName(parameter = defaultValue) {
  // code
}
```

---

# ✅ Course Example

```js
function add(num1 = 0, num2 = 0) {
  return num1 + num2;
}

console.log(add(10, 20));
console.log(add(10));
console.log(add());
```

### Output

```js
30
10
0
```

---

# ✅ Course Example

```js
function fullName(firstName, lastName = "") {
  return firstName + " " + lastName;
}

console.log(fullName("Rakib", "Hasan"));
console.log(fullName("Rakib"));
```

### Output

```js
Rakib Hasan
Rakib
```

---

# 📊 ES5 vs ES6

| ES5 | ES6 |
|------|------|
| Manual checking required | Built-in support |
| More code | Less code |
| Uses `if` statement or `||` operator | Uses `=` inside parameter |
| Less readable | Cleaner and easier |

---

# ⭐ Important Notes

- Default Parameters were introduced in **ES6 (ECMAScript 2015)**.
- The default value is used only when the argument is **not provided** or **`undefined`**.
- Passing any actual value ignores the default value.
- Multiple parameters can have default values.
- Default Parameters make code cleaner and easier to read.

---

# 🎯 Interview Questions

### 1. What is a Default Parameter?

A Default Parameter is a value that is automatically used when no argument or `undefined` is passed.

---

### 2. Which ES version introduced Default Parameters?

**ES6 (ECMAScript 2015).**

---

### 3. When does a Default Parameter work?

When no argument or `undefined` is passed.

---

### 4. Does `null` use the default value?

**No.** `null` is treated as an actual value.

---

### 5. Can multiple parameters have default values?

**Yes.**

```js
function sum(a = 0, b = 0, c = 0) {
  return a + b + c;
}
```

---

# ⚠️ Common Mistakes

- Thinking `null` uses the default value.
- Forgetting that only `undefined` triggers the default value.
- Writing unnecessary `if` statements instead of using Default Parameters.

---

# 🧠 Memory Trick

```text
No Argument ➜ Default Value ✅

undefined ➜ Default Value ✅

null ➜ Actual Value ❌
```

---

# ⚡ Quick Revision

- Introduced in ES6.
- Used in Function Parameters.
- Makes code cleaner and shorter.
- Works only with `undefined`.
- Does not work with `null`.
- Supports multiple default parameters.

---

# 🔑 Keywords

- Default Parameter
- Function
- Parameter
- Argument
- Undefined
- Null
- ES6
- Default Value