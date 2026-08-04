# Arrow Function

## Definition

**An Arrow Function is a shorter syntax for writing functions in JavaScript. It was introduced in ES6 to make code cleaner and more readable.**

(Arrow Function হলো JavaScript-এ Function লেখার একটি সংক্ষিপ্ত (Short) Syntax। এটি ES6-এ এসেছে যাতে Code আরও পরিষ্কার ও ছোট হয়।)

---

## Traditional Function

```js
function sayGreet(name) {
    return `Hello ${name}, Good morning.`;
}

console.log(sayGreet("Utsho"));
```

---

## Arrow Function Syntax

```js
const sayGreet = (name) => {
    return `Hello ${name}, Good morning.`;
};

console.log(sayGreet("Utsho"));
```

---

## General Syntax

```js
const functionName = () => {

}
```

---

## Single Parameter

Parentheses `()` optional.

```js
const sayHi = name => {
    return `Hello ${name}`;
};
```

অথবা

```js
const sayHi = (name) => {
    return `Hello ${name}`;
};
```

---

## Multiple Parameters

Parentheses Required.

```js
const sum = (a, b) => {
    return a + b;
};
```

---

## No Parameter

```js
const sayHi = () => {
    return "Hi";
};
```

---

## Implicit Return (Single Statement)

এক লাইনের Function হলে `return` লিখতে হয় না।

```js
const multiply = (a, b) => a * b;

console.log(multiply(5, 5));
```

Output

```text
25
```

---

## Example

```js
const sayHi = () => "Hi";

console.log(sayHi());
```

Output

```text
Hi
```

---

## `this` in Traditional Function

```js
const student = {
    name: "Utsho",
    age: 26,

    showName: function () {
        return `Name: ${this.name}, Age: ${this.age}`;
    }
};

console.log(student.showName());
```

Output

```text
Name: Utsho, Age: 26
```

---

## `this` in Arrow Function

```js
const student = {
    name: "Utsho",
    age: 26,

    showAge: () => {
        return `Age: ${this.age}`;
    }
};

console.log(student.showAge());
```

Output

```text
Age: undefined
```

---

## Why?

Arrow Function-এর নিজের `this` থাকে না।

এটি বাইরের (Lexical) Scope-এর `this` ব্যবহার করে।

Traditional Function-এর নিজের `this` থাকে।

---

## Difference

| Traditional Function | Arrow Function |
|----------------------|---------------|
| `function` keyword ব্যবহার করে | `=>` ব্যবহার করে |
| নিজের `this` থাকে | নিজের `this` থাকে না |
| Syntax বড় | Syntax ছোট |
| সব জায়গায় ব্যবহার করা যায় | Callback ও ছোট Function-এর জন্য বেশি ব্যবহার হয় |

---

## Interview Question

### What is an Arrow Function?

**Answer:**

An Arrow Function is a shorter way to write functions in JavaScript. It was introduced in ES6 and provides a concise syntax. Unlike traditional functions, it does not have its own `this`.

---

## Common Mistake

❌

```js
showAge: () => {
    return this.age;
}
```

`this.age` → `undefined`

---

## Quick Revision

- Arrow Function এসেছে ES6-এ।
- `=>` ব্যবহার করা হয়।
- Single Parameter হলে `()` Optional।
- Multiple Parameter হলে `()` Required।
- Single Statement হলে `return` লেখা লাগে না।
- Arrow Function-এর নিজের `this` থাকে না।