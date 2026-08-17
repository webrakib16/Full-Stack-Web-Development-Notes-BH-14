# 📚 Module: 22 | 🎓 Class: 01

# `tsconfig.json` — Manual Setup

> **Topic:** TypeScript Configuration, `src` & `dist`, Terminal Commands

---

# 📖 What I Learned Today

- What is `tsconfig.json`
- Manual `tsconfig.json` setup
- `src` folder
- `dist` folder
- TypeScript Source Files
- Compiled JavaScript Files
- `rootDir`
- `outDir`
- `target`
- `module`
- Terminal Navigation
- TypeScript Compile Commands
- JavaScript Run Commands
- Compile Workflow
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What is `tsconfig.json`?



`tsconfig.json` is the configuration file that tells the TypeScript compiler how to compile a TypeScript project.

`tsconfig.json` হলো TypeScript project-এর configuration file। এখানে TypeScript compiler কীভাবে `.ts` files compile করবে, source files কোথায় থাকবে এবং compiled JavaScript কোথায় যাবে তা configure করা হয়।

---

# Part 1 — Project Structure

একটি সাধারণ TypeScript project:

```text
project/
│
├── src/
│   └── index.ts
│
├── dist/
│   └── index.js
│
└── tsconfig.json
```

### 📁 SRC

> **SRC - TypeScript source files**

এখানে আমাদের মূল TypeScript files থাকে।

```text
src/
└── index.ts
```

### 📁 DIST

> **DIST - Compiled JavaScript files**

এখানে TypeScript compile হওয়ার পর তৈরি হওয়া JavaScript files থাকে।

```text
dist/
└── index.js
```

### 🔄 Workflow

```text
src/index.ts
     ↓
TypeScript Compiler
     ↓
dist/index.js
     ↓
Node.js
     ↓
Output
```

---

# Part 2 — Manual `tsconfig.json` Setup

## Step 1 — Create Project Folder

Terminal-এ:

```bash
mkdir typescript-project
```

Folder-এর ভিতরে যাও:

```bash
cd typescript-project
```

---

## Step 2 — Create `src` Folder

```bash
mkdir src
```

---

## Step 3 — Create `dist` Folder

```bash
mkdir dist
```

Project structure:

```text
typescript-project/
│
├── src/
├── dist/
└──
```

---

# Part 3 — Initialize npm

```bash
npm init -y
```

এতে:

```text
package.json
```

file তৈরি হবে।

---

# Part 4 — Install TypeScript

```bash
npm install typescript --save-dev
```

TypeScript project-এর development dependency হিসেবে install হবে।

---

# Part 5 — Create `tsconfig.json`

Manual setup-এর জন্য project root-এ:

```text
tsconfig.json
```

file তৈরি করো।

Project structure:

```text
typescript-project/
│
├── src/
├── dist/
├── package.json
├── package-lock.json
└── tsconfig.json
```

---

# Part 6 — Basic `tsconfig.json`

```json
{
    "compilerOptions": {
        "target": "ES6",
        "module": "commonjs",
        "rootDir": "./src",
        "outDir": "./dist",
        "strict": true
    }
}
```

---

# Part 7 — Important `tsconfig.json` Options

| Option | কাজ |
|---|---|
| `target` | কোন JavaScript version-এ compile হবে |
| `module` | কোন module system ব্যবহার হবে |
| `rootDir` | TypeScript source files-এর folder |
| `outDir` | Compiled JavaScript files-এর folder |
| `strict` | Strict type checking চালু করে |

---

# `rootDir`

```json
"rootDir": "./src"
```

এটি TypeScript compiler-কে বলে:

> TypeScript source files `src` folder-এর মধ্যে আছে।

```text
src/
└── index.ts
```

---

# `outDir`

```json
"outDir": "./dist"
```

এটি বলে:

> Compiled JavaScript files `dist` folder-এ রাখতে হবে।

```text
dist/
└── index.js
```

---

# `target`

```json
"target": "ES6"
```

TypeScript code কোন JavaScript version-এর জন্য compile হবে তা নির্ধারণ করে।

---

# `module`

```json
"module": "commonjs"
```

Compiled JavaScript-এর module system নির্ধারণ করে।

---

# `strict`

```json
"strict": true
```

TypeScript-এর strict type checking চালু করে।

---

# Part 8 — Create TypeScript File

`src` folder-এর ভিতরে:

```text
src/
└── index.ts
```

Example:

```ts
const message: string = "Hello TypeScript";

console.log(message);
```

---

# Part 9 — Compile TypeScript

Project root থেকে terminal-এ:

```bash
npx tsc
```

এখন:

```text
src/index.ts
      ↓
    npx tsc
      ↓
dist/index.js
```

---

# Part 10 — Run Compiled JavaScript

Compile করার পর:

```bash
node dist/index.js
```

Output:

```text
Hello TypeScript
```

---

# Part 11 — Terminal Navigation

## 📂 Current Folder দেখার জন্য

### Windows

```bash
cd
```

অথবা:

```bash
pwd
```

### Folder-এর ভিতরে যাওয়ার জন্য

```bash
cd folder-name
```

Example:

```bash
cd src
```

### এক ধাপ পিছনে যাওয়ার জন্য

```bash
cd ..
```

### Folder-এর Files দেখার জন্য

### Windows

```bash
dir
```

### macOS / Linux / Git Bash

```bash
ls
```

---

# Part 12 — Complete Terminal Workflow

```bash
mkdir typescript-project

cd typescript-project

mkdir src

mkdir dist

npm init -y

npm install typescript --save-dev
```

তারপর `tsconfig.json` তৈরি করে configuration দেওয়ার পর:

```bash
npx tsc
```

Compile হওয়ার পরে:

```bash
node dist/index.js
```

---

# Part 13 — JavaScript vs TypeScript Workflow

### JavaScript

```text
.js file
   ↓
Node.js
   ↓
Output
```

### TypeScript

```text
.ts file
   ↓
tsconfig.json
   ↓
TypeScript Compiler
   ↓
.js file
   ↓
Node.js
   ↓
Output
```

---

# Part 14 — Core Concept Analysis

| Concept | JavaScript | TypeScript |
|---|---|---|
| Source File | `.js` | `.ts` |
| Configuration | সাধারণত `tsconfig.json` প্রয়োজন নেই | `tsconfig.json` দিয়ে compiler configure করা যায় |
| Compilation | সাধারণত প্রয়োজন নেই | JavaScript-এ compile হয় |
| Source Directory | নির্দিষ্ট নয় | `rootDir` দিয়ে define করা যায় |
| Output Directory | নির্দিষ্ট নয় | `outDir` দিয়ে define করা যায় |
| Type Checking | ❌ | ✅ |
| Compiler | ❌ | `tsc` |

---

# Part 15 — Common Mistakes

## ❌ Mistake 1 — Wrong `rootDir`

```json
"rootDir": "./src"
```

কিন্তু TypeScript file `src`-এর বাইরে থাকলে configuration সমস্যা হতে পারে।

---

## ❌ Mistake 2 — Wrong `outDir`

```json
"outDir": "./dist"
```

Compiled JavaScript কোথায় যাবে সেটা `outDir` control করে।

---

## ❌ Mistake 3 — Wrong Folder থেকে Compile করা

সাধারণভাবে `tsconfig.json` যে project root-এ আছে, সেখান থেকে:

```bash
npx tsc
```

চালানো সহজ ও recommended।

---

# ⚡ Quick Revision

```text
tsconfig.json
→ TypeScript Compiler Configuration

src
→ TypeScript Source Files

dist
→ Compiled JavaScript Files

rootDir
→ Source Folder

outDir
→ Output Folder

target
→ JavaScript Version

module
→ Module System

strict
→ Strict Type Checking

npx tsc
→ Compile TypeScript

node dist/index.js
→ Run Compiled JavaScript
```

### 🧠 Main Workflow

```text
src
 ↓
.ts
 ↓
tsconfig.json
 ↓
npx tsc
 ↓
dist
 ↓
.js
 ↓
node
 ↓
Output
```

---

# 🎯 Interview Questions

## Q1. What is the purpose of `tsconfig.json`?

**Answer:**

`tsconfig.json` TypeScript compiler-এর configuration define করে। এটি source directory, output directory, target JavaScript version, module system এবং type checking-এর মতো বিষয় configure করতে ব্যবহৃত হয়।

---

## Q2. What is the difference between `rootDir` and `outDir`?

**Answer:**

`rootDir` TypeScript source files-এর directory নির্ধারণ করে, আর `outDir` compiled JavaScript files কোথায় তৈরি হবে তা নির্ধারণ করে।

---

## Q3. Why do we use `src` and `dist` folders?

**Answer:**

`src` folder-এ original TypeScript source files রাখা হয় এবং `dist` folder-এ compiled JavaScript files রাখা হয়। এতে source code এবং compiled code আলাদা ও organized থাকে।