# 📚 Module: 21 | 🎓 Class: 02

# Setting Up and Running TypeScript

> **Topic:** TypeScript Setup, Compilation & Running TypeScript Code

---

# 📖 What I Learned Today

- What is TypeScript Setup
- Node.js
- npm
- TypeScript Installation
- TypeScript Compiler
- `.ts` File
- `tsc` Command
- Compile TypeScript to JavaScript
- Run JavaScript with Node.js
- `tsconfig.json`
- JavaScript vs TypeScript Workflow
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What is TypeScript Setup?



TypeScript setup means preparing the development environment to **write, compile and run TypeScript code**.

TypeScript setup বলতে TypeScript code লেখার, JavaScript-এ compile করার এবং সেই JavaScript run করার জন্য প্রয়োজনীয় environment তৈরি করাকে বোঝায়।

---

# Part 1 — Required Tools

TypeScript ব্যবহার করার জন্য সাধারণত প্রয়োজন:

- Node.js
- npm
- TypeScript
- Code Editor, যেমন VS Code

### 🔍 Workflow

```text
TypeScript Code
      ↓
   TypeScript Compiler
      ↓
JavaScript Code
      ↓
    Node.js
      ↓
    Output
```

> Browser বা Node.js সরাসরি TypeScript code execute করে না। TypeScript প্রথমে JavaScript-এ compile করা হয়।

---

# Part 2 — Node.js

## 📌 What is Node.js?


Node.js is a JavaScript runtime that allows JavaScript to run outside the browser.

Node.js হলো একটি JavaScript runtime environment, যার মাধ্যমে browser-এর বাইরে JavaScript code run করা যায়।

### Check Node.js

```bash
node --version
```

### Check npm

```bash
npm --version
```

---

# Part 3 — TypeScript Installation

## Global Installation

TypeScript globally install করার command:

```bash
npm install -g typescript
```

Installation check:

```bash
tsc --version
```

এখানে `tsc` হলো **TypeScript Compiler**।

---

# Part 4 — TypeScript File

TypeScript file-এর extension হলো:

```text
.ts
```

Example:

```text
index.ts
```

### JavaScript

```text
index.js
```

### TypeScript

```text
index.ts
```

---

# Part 5 — TypeScript Compiler

## 📌 What is `tsc`?



`tsc` is the TypeScript Compiler that converts TypeScript code into JavaScript.

`tsc` হলো TypeScript Compiler। এটি TypeScript code-কে JavaScript code-এ compile করে।

---

# Compile TypeScript

```bash
tsc index.ts
```

এতে:

```text
index.ts
   ↓
index.js
```

তৈরি হবে।

---

# Run the JavaScript

Compile করার পরে Node.js দিয়ে JavaScript file run করা যায়:

```bash
node index.js
```

### Complete Workflow

```text
index.ts
   ↓
tsc index.ts
   ↓
index.js
   ↓
node index.js
   ↓
Output
```

---

# Part 6 — JavaScript vs TypeScript Workflow

### JavaScript

```text
.js File
   ↓
JavaScript Runtime
   ↓
Output
```

### TypeScript

```text
.ts File
   ↓
TypeScript Compiler (tsc)
   ↓
.js File
   ↓
JavaScript Runtime
   ↓
Output
```

---

# Part 7 — Core Concept Analysis

## JavaScript

```js
let age = 22;

console.log(age);
```

JavaScript file সরাসরি runtime-এ execute করা যায়।

---

## TypeScript

```ts
let age: number = 22;

console.log(age);
```

TypeScript file সরাসরি সাধারণ JavaScript runtime-এ run না করে প্রথমে compile করা হয়।

```text
TypeScript
   ↓
Compiler
   ↓
JavaScript
   ↓
Runtime
```

### 🔍 Main Difference

| Feature | JavaScript | TypeScript |
|---|---|---|
| File Extension | `.js` | `.ts` |
| Direct Runtime Execution | ✅ | সাধারণত ❌ |
| Compilation | প্রয়োজন নেই | JavaScript-এ compile হয় |
| Compiler | Not required | `tsc` |
| Type Checking | ❌ | ✅ |
| Runtime | Browser / Node.js | Compiled JavaScript Browser / Node.js-এ run করে |

---

# Part 8 — TypeScript Compiler Options

TypeScript compile করার সময় কিছু option ব্যবহার করা যায়।

### Output JavaScript File

```bash
tsc index.ts
```

### Watch Mode

```bash
tsc --watch
```

অথবা:

```bash
tsc -w
```

> Watch mode চালু থাকলে TypeScript file পরিবর্তন করলে compiler automatically আবার compile করে।

---

# Part 9 — `tsconfig.json`

## 📌 Definition



`tsconfig.json` is the configuration file used to define how a TypeScript project should be compiled.

`tsconfig.json` হলো TypeScript project-এর configuration file। এখানে TypeScript compiler কীভাবে code compile করবে তা নির্ধারণ করা যায়।

---

# Create `tsconfig.json`

```bash
tsc --init
```

এতে project-এর জন্য:

```text
tsconfig.json
```

file তৈরি হবে।

---

# Why Use `tsconfig.json`?

এর মাধ্যমে configure করা যায়:

- কোন TypeScript files compile হবে
- কোন JavaScript version target করা হবে
- Output কোথায় যাবে
- Strict type checking
- Module system
- অন্যান্য compiler options

---

# Part 10 — Important Commands

| Command | কাজ |
|---|---|
| `node --version` | Node.js version check |
| `npm --version` | npm version check |
| `tsc --version` | TypeScript version check |
| `npm install -g typescript` | TypeScript globally install |
| `tsc index.ts` | TypeScript compile |
| `node index.js` | JavaScript run |
| `tsc --watch` | Automatically compile |
| `tsc --init` | `tsconfig.json` তৈরি |

---

# Part 11 — Common Mistakes

## ❌ Mistake 1 — `.ts` File সরাসরি Node.js দিয়ে Run করা

```bash
node index.ts
```

সাধারণ workflow-এ আগে TypeScript compile করা উচিত:

```bash
tsc index.ts
```

তারপর:

```bash
node index.js
```

---

## ❌ Mistake 2 — `tsc` Command কাজ না করা

যদি:

```bash
tsc --version
```

কাজ না করে, তাহলে TypeScript installation বা PATH configuration check করতে হবে।

---

## ❌ Mistake 3 — JavaScript Output File কোথায় তৈরি হচ্ছে না বোঝা

```bash
tsc index.ts
```

চালালে সাধারণত একই directory-তে compiled JavaScript file তৈরি হতে পারে, যদি compiler configuration দিয়ে অন্য output directory নির্ধারণ করা না থাকে।

---

# ⚡ Quick Revision

```text
Node.js
→ JavaScript Runtime

npm
→ Package Manager

TypeScript
→ Superset of JavaScript

tsc
→ TypeScript Compiler

.ts
→ TypeScript File

.js
→ Compiled JavaScript File

tsconfig.json
→ TypeScript Project Configuration
```

### 🧠 Main Workflow

```text
Write
  ↓
TypeScript (.ts)
  ↓
Compile
  ↓
JavaScript (.js)
  ↓
Run
  ↓
Node.js / Browser
```

---

# 🎯 Interview Questions

## Q1. What is `tsc`?

**Answer:**

`tsc` হলো TypeScript Compiler, যা TypeScript code-কে JavaScript-এ compile করে।

---

## Q2. Why does TypeScript need to be compiled?

**Answer:**

TypeScript-এর type annotations এবং অন্যান্য TypeScript-specific features সাধারণ JavaScript runtime সরাসরি বুঝতে পারে না। তাই TypeScript code JavaScript-এ compile করে তারপর run করা হয়।

---

## Q3. What is the purpose of `tsconfig.json`?

**Answer:**

`tsconfig.json` TypeScript project-এর compiler configuration define করে। এর মাধ্যমে target, output, strict checking, module system ইত্যাদি configure করা যায়।