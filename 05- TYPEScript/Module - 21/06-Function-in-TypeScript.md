# 📚 Module: 21 | 🎓 Class: 6

# Function in TypeScript

> **Topic:** Function, Input & Output

---

# 📖 What I Learned Today

- Function in TypeScript
- Function Input
- Function Output
- Parameter Type
- Return Type
- JavaScript vs TypeScript
- Important Syntax
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What is a Function?


A function is a reusable block of code that performs a specific task.

Function হলো এমন একটি reusable block of code যা একটি নির্দিষ্ট কাজ সম্পন্ন করে।

---

# Part 1 — Function Input

## 📌 What is Function Input?



Input is the data that we pass into a function through **parameters**.

Function-এর মধ্যে বাইরে থেকে যে data পাঠানো হয়, সেটিই input। এই input **parameter**-এর মাধ্যমে নেওয়া হয়।

---

# Syntax

```ts
function add(a: number, b: number) {
    return a + b;
}
```

এখানে:

```text
a → number
b → number
```

`a` এবং `b` হলো function-এর parameters।

---

# Example

```ts
function greet(name: string) {
    console.log(`Hello ${name}`);
}

greet("Rakib");
```

এখানে `name` হলো input parameter এবং এর type হলো `string`।

---

# Part 2 — Function Output

## 📌 What is Function Output?


Output is the value that a function returns after performing its task.

Function কাজ শেষ করার পর যে value `return` করে, সেটিই function-এর output।

---

# Return Type

TypeScript-এ function কী ধরনের value return করবে তা explicitly define করা যায়।

```ts
function add(a: number, b: number): number {
    return a + b;
}
```

এখানে:

```text
Input  → a: number, b: number

Output → number
```

---

# Example

```ts
function multiply(a: number, b: number): number {
    return a * b;
}

const result = multiply(5, 4);

console.log(result);
```

Output:

```text
20
```

---

# Part 3 — Input vs Output

| Concept | Meaning | TypeScript |
|---|---|---|
| Input | Function-এ পাঠানো data | Parameter type |
| Output | Function থেকে পাওয়া result | Return type |
| Input Example | `name: string` | Parameter |
| Output Example | `: number` | Return Type |

---

# Part 4 — JavaScript vs TypeScript

### JavaScript

```js
function add(a, b) {
    return a + b;
}
```

### TypeScript

```ts
function add(a: number, b: number): number {
    return a + b;
}
```

> TypeScript-এ parameter এবং return value-এর type define করা যায়।

---

# Part 5 — Important Syntax

## Function with Input

```ts
function greet(name: string) {
    console.log(`Hello ${name}`);
}
```

## Function with Input and Output

```ts
function add(a: number, b: number): number {
    return a + b;
}
```

## Function with No Input

```ts
function welcome(): string {
    return "Welcome";
}
```

---

# Part 6 — Common Mistakes

## ❌ Mistake 1 — Wrong Parameter Type

```ts
function add(a: number, b: number): number {
    return a + b;
}

add(10, "20");
```

`b` এর type `number`, তাই `"20"` দেওয়া যাবে না।

---

## ❌ Mistake 2 — Wrong Return Type

```ts
function getAge(): number {
    return "22";
}
```

Return type `number` দেওয়া হয়েছে, তাই `string` return করা যাবে না।

---

## ❌ Mistake 3 — Forgetting `return`

```ts
function add(a: number, b: number): number {
    a + b;
}
```

Function-এর return type `number` হলে একটি `number` value return করতে হবে।

---

# ⚡ Quick Revision

```text
Function
→ Reusable block of code

Input
→ Data passed into function
→ Parameter

Output
→ Value returned from function
→ Return Type
```

### 🧠 Memory Trick

```text
Input  → Parameter

Process → Function Body

Output → Return
```

---

# 🎯 Interview Questions

## Q1. What is the difference between a parameter and an argument?

**Answer:**

Parameter হলো function definition-এর variable, আর argument হলো function call করার সময় parameter-এ পাঠানো actual value।

---

## Q2. How do you define a return type in TypeScript?

**Answer:**

Function-এর parameter list-এর পরে `:` দিয়ে return type define করা হয়।

```ts
function add(a: number, b: number): number {
    return a + b;
}
```

---

## Q3. Why are parameter and return types useful in TypeScript?

**Answer:**

এগুলো function-এ কী ধরনের input নেওয়া যাবে এবং কী ধরনের output return হবে তা নিশ্চিত করে, ফলে ভুল type-এর data সহজে detect করা যায়।