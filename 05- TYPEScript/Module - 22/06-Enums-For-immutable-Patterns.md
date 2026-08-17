# 📚 Module: 22 | 🎓 Class: 06

# Enums for Immutable Patterns

> **Topic:** Enum, Numeric Enum, String Enum & Immutable Patterns

---

# 📖 What I Learned Today

- What is Enum
- Numeric Enum
- String Enum
- Accessing Enum Values
- Enum for Fixed Values
- Enum vs Union Type
- Immutable Patterns
- JavaScript vs TypeScript
- Core Concept Analysis
- Common Mistakes
- Quick Revision
- Interview Questions

---

# 📌 What is an Enum?



An Enum is a TypeScript feature that defines a set of **named constant values**.

Enum ব্যবহার করে নির্দিষ্ট কিছু **named constant values**-এর একটি group তৈরি করা যায়। যখন কোনো variable-এর value কয়েকটি নির্দিষ্ট option-এর মধ্যেই সীমাবদ্ধ থাকবে, তখন Enum ব্যবহার করা যায়।

---

# Part 1 — Basic Enum

## Syntax

```ts
enum Direction {
    Up,
    Down,
    Left,
    Right
}
```

এখানে:

```text
Direction
→ Enum Name

Up, Down, Left, Right
→ Enum Members
```

Value access:

```ts
Direction.Up;
Direction.Down;
```

---

# Part 2 — Numeric Enum

Defaultভাবে Enum-এর প্রথম member-এর value `0` থেকে শুরু হয়।

```ts
enum Direction {
    Up,
    Down,
    Left,
    Right
}
```

Values:

```text
Up    → 0
Down  → 1
Left  → 2
Right → 3
```

নিজে থেকে starting value দেওয়া যায়:

```ts
enum Direction {
    Up = 1,
    Down,
    Left,
    Right
}
```

Values:

```text
Up    → 1
Down  → 2
Left  → 3
Right → 4
```

---

# Part 3 — String Enum

String Enum-এ প্রতিটি member-এর জন্য string value explicitly define করা হয়।

```ts
enum Status {
    Success = "SUCCESS",
    Error = "ERROR",
    Loading = "LOADING"
}
```

ব্যবহার:

```ts
const currentStatus: Status = Status.Success;
```

---

# Part 4 — Enum Example

```ts
enum Role {
    Admin = "ADMIN",
    User = "USER",
    Guest = "GUEST"
}

const userRole: Role = Role.Admin;
```

এখানে `userRole` শুধু `Role` enum-এর valid member-এর value গ্রহণ করবে।

---

# Part 5 — Enum for Fixed Values

যখন কোনো variable-এর value নির্দিষ্ট কয়েকটি option-এর মধ্যে থাকবে, Enum ব্যবহার করা যায়।

```ts
enum OrderStatus {
    Pending = "PENDING",
    Shipped = "SHIPPED",
    Delivered = "DELIVERED",
    Cancelled = "CANCELLED"
}

let status: OrderStatus = OrderStatus.Pending;
```

এখানে valid values:

```text
PENDING
SHIPPED
DELIVERED
CANCELLED
```

---

# Part 6 — Immutable Pattern

## 📌 What does Immutable Mean?



Immutable means a value or state should not be changed after it is created.

Immutable বলতে এমন data বা state বোঝায় যেটি তৈরি হওয়ার পরে পরিবর্তন করা উচিত নয়।

Enum-এর values predefined এবং fixed হওয়ায় এটি fixed set of values represent করতে useful।

```ts
enum Role {
    Admin = "ADMIN",
    User = "USER"
}
```

এখানে নতুন arbitrary value:

```ts
const role: Role = "MANAGER"; // ❌
```

দেওয়া যাবে না।

---

# Part 7 — Enum vs Union Type

একই ধরনের fixed values Union Type দিয়েও তৈরি করা যায়।

### Enum

```ts
enum Role {
    Admin = "ADMIN",
    User = "USER",
    Guest = "GUEST"
}

let role: Role = Role.Admin;
```

### Union Type

```ts
type Role = "ADMIN" | "USER" | "GUEST";

let role: Role = "ADMIN";
```

---

# 🔍 Enum vs Union Type

| Feature | Enum | Union Type |
|---|---|---|
| Fixed Values | ✅ | ✅ |
| Named Group | ✅ | ❌ |
| String Literals | Possible | ✅ |
| Runtime JavaScript Output | Usually generates runtime code | ❌ |
| TypeScript-only | ❌ | ✅ |
| Simple Fixed Options | Useful | Often simpler |

> Modern TypeScript code-এ শুধু fixed string values দরকার হলে Union Type অনেক সময় Enum-এর simpler alternative।

---

# Part 8 — JavaScript vs TypeScript

JavaScript-এ built-in `enum` syntax নেই।

### JavaScript

```js
const Role = {
    Admin: "ADMIN",
    User: "USER",
    Guest: "GUEST"
};

const role = Role.Admin;
```

### TypeScript

```ts
enum Role {
    Admin = "ADMIN",
    User = "USER",
    Guest = "GUEST"
}

const role: Role = Role.Admin;
```

### 🔍 Difference

| JavaScript | TypeScript |
|---|---|
| Built-in Enum নেই | Enum আছে |
| Object দিয়ে similar pattern তৈরি করা যায় | `enum` দিয়ে named constants তৈরি করা যায় |
| Static enum type checking নেই | Enum type checking আছে |
| Object runtime-এ থাকে | Enum সাধারণত JavaScript output-এ runtime code তৈরি করে |

---

# Part 9 — Core Concept Analysis

Enum Type Alias বা Interface-এর মতো শুধু compile-time concept নয়। TypeScript Enum সাধারণত JavaScript-এ **runtime representation** তৈরি করে।

### TypeScript

```ts
enum Status {
    Success = "SUCCESS",
    Error = "ERROR"
}

const currentStatus: Status = Status.Success;
```

### Compiled JavaScript-এর ধারণা

```js
var Status;

(function (Status) {
    Status["Success"] = "SUCCESS";
    Status["Error"] = "ERROR";
})(Status || (Status = {}));

const currentStatus = Status.Success;
```

### 🔍 What Changed?

```text
TypeScript
→ enum syntax
→ Enum type checking

JavaScript
→ Object-like runtime representation
```

> তাই Enum, `type` বা `interface`-এর মতো পুরোপুরি compile-time-only নয়।

---

# Part 10 — Enum Access

Enum member dot notation দিয়ে access করা যায়।

```ts
enum Color {
    Red = "RED",
    Green = "GREEN",
    Blue = "BLUE"
}

console.log(Color.Red);
console.log(Color.Green);
```

Output:

```text
RED
GREEN
```

---

# Part 11 — Common Mistakes

## ❌ Mistake 1 — Invalid Enum Value

```ts
enum Role {
    Admin = "ADMIN",
    User = "USER"
}

let role: Role = "MANAGER";
```

`"MANAGER"` Enum-এর valid member নয়।

Correct:

```ts
let role: Role = Role.Admin;
```

---

## ❌ Mistake 2 — Numeric Enum-এর Value না বোঝা

```ts
enum Status {
    Pending,
    Success,
    Failed
}
```

এখানে:

```text
Pending → 0
Success → 1
Failed  → 2
```

---

## ❌ Mistake 3 — Enum এবং Union Type একই মনে করা

দুটো fixed values represent করতে পারে, কিন্তু তাদের implementation এবং runtime behavior একই নয়।

```text
Enum
→ Runtime representation থাকে

Union Type
→ Compile-time type
→ Runtime output তৈরি করে না
```

---

# ⚡ Quick Revision

```text
Enum
→ Named Constant Values

Numeric Enum
→ Default values start from 0

String Enum
→ Explicit string values

Enum
→ Fixed set of named values

Immutable Pattern
→ Data/state should not be changed

Union Type
→ Simple fixed values-এর alternative

Enum
→ Runtime representation তৈরি করে
```

### 🧠 Memory Trick

```text
Enum
→ Named + Fixed Values

Union
→ Fixed Values

readonly
→ Cannot Reassign
```

---

# 🎯 Interview Questions

## Q1. What is an Enum in TypeScript?

**Answer:**

Enum হলো TypeScript-এর একটি feature যা named constant values-এর একটি fixed set তৈরি করতে ব্যবহার করা হয়।

---

## Q2. What is the difference between Enum and Union Type?

**Answer:**

দুটোই fixed values represent করতে পারে। তবে Enum-এর runtime representation থাকে, যেখানে Union Type compile-time type system-এর অংশ এবং JavaScript output-এ আলাদা runtime code তৈরি করে না।

---

## Q3. Does TypeScript Enum exist at runtime?

**Answer:**

হ্যাঁ। সাধারণ TypeScript Enum JavaScript-এ runtime representation তৈরি করে। তাই এটি `interface` বা `type`-এর মতো শুধুমাত্র compile-time feature নয়।