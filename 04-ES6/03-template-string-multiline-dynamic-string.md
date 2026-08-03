# Template String - Multiline and Dynamic String

> 📚 Module: ES6
> 🎓 Class: 3/10

---

# 📚 What I Learned Today

- Template String
- Backticks (``)
- String Interpolation
- Dynamic String
- Multiline String
- Using Expressions inside Template String
- Template String with Function
- Template String with Default Parameter

---

# 📌 What is Template String?

### Definition (English)

A **Template String** is a modern way of creating strings in JavaScript using **backticks (` `)**. It supports string interpolation, multiline strings, and embedded expressions.

### সংজ্ঞা (বাংলা)

**Template String** হলো JavaScript-এ **Backtick (` `)** ব্যবহার করে String লেখার একটি আধুনিক পদ্ধতি। এর মাধ্যমে Dynamic Value, Multiline String এবং Expression সহজে ব্যবহার করা যায়।

---

# ❓ Why Use Template Strings?

Before ES6, developers used the `+` operator to join strings and variables, making the code longer and harder to read.

Template Strings make code cleaner, shorter, and more readable.

(ES6-এর আগে `+` Operator ব্যবহার করে String ও Variable যুক্ত করতে হতো। এতে Code বড় এবং পড়তে কঠিন হতো। Template String Code-কে আরও পরিষ্কার ও সহজ করে।)

---

# 💻 Syntax

```js
let message = `Hello ${name}`;
```

---

# ✅ Course Example

### Before ES6

```js
let name = "Utsho";
let price = 500;
let quantity = 5;

let message = "Hello " + name + ". Your bill is " + (price * quantity);

console.log(message);
```

### Output

```text
Hello Utsho. Your bill is 2500
```

---

# ✅ Course Example

### ES6 Template String

```js
let name = "Utsho";
let price = 500;
let quantity = 5;

let message = `Hello ${name}. Your bill is ${price * quantity}.`;

console.log(message);
```

### Output

```text
Hello Utsho. Your bill is 2500.
```

---

# ✅ Multiline String

```js
let amount = 3000;

function admissionConfirmationMail(name, amount) {
  let message = `Hello, ${name},
Your payment is successful.
Your paid amount is ${amount}.`;

  return message;
}

console.log(admissionConfirmationMail("Utsho", 3000));
```

### Output

```text
Hello, Utsho,
Your payment is successful.
Your paid amount is 3000.
```

---

# ✅ Template String with Default Parameter

```js
function admissionConfirmationMail(name = "Student", amount = 0) {
  let message = `Hello, ${name},
Your payment is successful.
Your paid amount is ${amount}.`;

  return message;
}

console.log(admissionConfirmationMail("Utsho", 3000));
console.log(admissionConfirmationMail(undefined, 5000));
```

### Output

```text
Hello, Utsho,
Your payment is successful.
Your paid amount is 3000.

Hello, Student,
Your payment is successful.
Your paid amount is 5000.
```

---

# 📊 String Concatenation vs Template String

| String Concatenation (`+`) | Template String |
|-----------------------------|-----------------|
| Uses `+` operator | Uses Backticks (``) |
| Harder to read | Cleaner and readable |
| Difficult for multiline | Supports multiline |
| Dynamic values are lengthy | Uses `${}` easily |
| Old approach | Modern ES6 approach |

---

# ⭐ Important Notes

- Template Strings were introduced in **ES6 (ECMAScript 2015)**.
- Always use **Backticks (` `)** instead of single (`'`) or double (`"` ) quotes.
- `${}` is used to insert variables or expressions.
- Supports multiline strings without using `\n`.
- Any valid JavaScript expression can be written inside `${}`.

---

# 🎯 Interview Questions

### 1. What is a Template String?

A Template String is an ES6 feature that allows creating strings using backticks and `${}`.

---

### 2. Which symbol is used for Template Strings?

**Backticks (` `)**

---

### 3. How do you insert variables inside a Template String?

Using `${variableName}`.

---

### 4. Can you write JavaScript expressions inside `${}`?

**Yes.**

Example:

```js
`${10 + 20}`
```

---

### 5. Why are Template Strings better than string concatenation?

Because they are cleaner, easier to read, and support multiline strings and expressions.

---

# ⚠️ Common Mistakes

- Using single quotes (`' '`) instead of backticks.
- Forgetting `${}` while inserting variables.
- Mixing `+` concatenation unnecessarily with Template Strings.

---

# 🧠 Memory Trick

```text
` `  ➜ Backticks

${} ➜ Insert Variable or Expression

Template String = Clean + Dynamic + Multiline
```

---

# ⚡ Quick Revision

- Introduced in ES6.
- Uses Backticks (``).
- `${}` is used for Dynamic Values.
- Supports Multiline Strings.
- Replaces string concatenation using `+`.

---

# 🔑 Keywords

- Template String
- Backticks
- String Interpolation
- Dynamic String
- Multiline String
- `${}`
- ES6
- String Concatenation