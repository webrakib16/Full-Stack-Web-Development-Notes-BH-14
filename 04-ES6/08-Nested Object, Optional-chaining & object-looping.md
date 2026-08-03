# ES6 – Class 8: Nested Object, Optional Chaining & Object Looping

## What I Learned Today

- Nested Object
- Dot Notation
- Bracket Notation
- Optional Chaining (`?.`)
- Object Looping (`for...in`)
- Object Looping using `Object.keys()`
- Object Looping using `Object.entries()`

---

# Nested Object

**Nested Object** (একটি Object-এর ভিতরে আরেকটি Object থাকলে তাকে Nested Object বলে।)

### Example

```javascript
const user = {
    name: "Utsho",
    age: 26,

    company: {
        name: "Programming Hero",

        address: {
            location: "Mirpur DOHS",
            street: "Something"
        }
    }
};
```

---

# Accessing Object Property

JavaScript-এ Object-এর Property Access করার দুইটি উপায় আছে।

- Dot Notation
- Bracket Notation

---

# Dot Notation

**Dot Notation** (`.` ব্যবহার করে Property Access করা।)

### Syntax

```javascript
object.property
```

### Example

```javascript
console.log(user.age);
console.log(user.company);
console.log(user.company.name);
```

---

# Bracket Notation

**Bracket Notation** (`[]` ব্যবহার করে Property Access করা।)

### Syntax

```javascript
object["property"]
```

### Example

```javascript
console.log(user["age"]);
console.log(user["company"]);
```

---

### যখন Property Name-এর মধ্যে Space থাকে

```javascript
const user = {
    "my address": "Rajshahi"
};

console.log(user["my address"]);
```

✅ Dot Notation এখানে কাজ করবে না।

❌ Wrong

```javascript
user.my address
```

---

### Variable দিয়ে Property Access

```javascript
const key = "company";

console.log(user[key]);
```

---

# Access Nested Object

### Example

```javascript
console.log(user.company.name);

console.log(user.company.address.location);

console.log(user.company.address.street);
```

### Output

```javascript
Programming Hero

Mirpur DOHS

Something
```

---

# Optional Chaining (?.)

**Optional Chaining (`?.`)** (যদি কোনো Property না থাকে তাহলে Error না দিয়ে `undefined` Return করে।)

### Syntax

```javascript
object?.property
```

---

### Without Optional Chaining

```javascript
console.log(user.company.address.location);
```

যদি `address` না থাকে তাহলে Error হবে।

---

### With Optional Chaining

```javascript
console.log(user?.company?.address?.location);
```

### Output

```javascript
Mirpur DOHS
```

---

### Example

```javascript
const user2 = {};

console.log(user2?.company?.name);
```

### Output

```javascript
undefined
```

Error হবে না।

---

# Object Loop (for...in)

**for...in Loop** (Object-এর প্রতিটি Property এক এক করে Loop করার জন্য ব্যবহার করা হয়।)

### Syntax

```javascript
for (let key in object) {

}
```

### Example

```javascript
for (let key in user) {
    console.log(key, user[key]);
}
```

### Output

```javascript
name Utsho

age 26

company { ... }
```

---

# Object Loop using Object.keys()

```javascript
const keys = Object.keys(user);

for (let key of keys) {
    console.log(key, user[key]);
}
```

---

# Object Loop using Object.entries()

```javascript
const entries = Object.entries(user);

for (let item of entries) {

    const [key, value] = item;

    console.log(key, value);
}
```

---

### Short Version

```javascript
for (const [key, value] of Object.entries(user)) {
    console.log(key, value);
}
```

---

# Dot Notation vs Bracket Notation

| Dot Notation | Bracket Notation |
|--------------|------------------|
| `user.name` | `user["name"]` |
| সহজ | একটু Flexible |
| Variable Support করে না | Variable Support করে |
| Space থাকলে কাজ করে না | Space থাকলেও কাজ করে |

---

# for...in vs Object.keys()

| for...in | Object.keys() |
|----------|---------------|
| সরাসরি Object Loop করে | আগে Keys Array তৈরি করে |
| Key Return করে | Keys Array Return করে |
| Object-এর জন্য ব্যবহৃত হয় | Array-এর মতো Loop করা যায় |

---

# Common Mistakes

### ❌ Wrong

```javascript
user.my address
```

### ✅ Correct

```javascript
user["my address"]
```

---

### ❌ Wrong

```javascript
console.log(user.company.address.location);
```

যদি `address` না থাকে তাহলে Error হবে।

### ✅ Correct

```javascript
console.log(user?.company?.address?.location);
```

---

### ❌ Wrong

```javascript
console.log(user.key);
```

### ✅ Correct

```javascript
console.log(user[key]);
```

---

# Interview Questions

### Q1. Nested Object কী?

**Answer:** Object-এর ভিতরে Object থাকলে তাকে Nested Object বলে।

---

### Q2. Dot Notation এবং Bracket Notation-এর পার্থক্য কী?

**Answer:**

- Dot (`.`) → সাধারণ Property Access করতে।
- Bracket (`[]`) → Variable বা Space থাকা Property Access করতে।

---

### Q3. Optional Chaining (`?.`) কেন ব্যবহার করা হয়?

**Answer:** Missing Property থাকলে Error এড়িয়ে `undefined` Return করার জন্য।

---

### Q4. Object Loop করার কয়টি উপায় শিখেছ?

**Answer:**

- `for...in`
- `Object.keys()`
- `Object.entries()`

---

### Q5. `user[key]` এবং `user.key`-এর মধ্যে পার্থক্য কী?

**Answer:**

- `user.key` → `key` নামে Property খোঁজে।
- `user[key]` → Variable-এর Value অনুযায়ী Property খোঁজে।

---

# Memory Trick

- 🏠 Nested Object → Object-এর ভিতরে Object
- 🔵 Dot (`.`) → Simple Property
- 🟨 Bracket (`[]`) → Variable + Space Property
- ❓ `?.` → Error থেকে বাঁচায়
- 🔁 `for...in` → Object Loop
- 🔑 `Object.keys()` → Keys
- 📦 `Object.entries()` → Key + Value Pair

---

# One Minute Revision

- Nested Object = Object-এর ভিতরে Object
- Dot Notation = `user.name`
- Bracket Notation = `user["name"]`
- Variable Property = `user[key]`
- Optional Chaining = `?.`
- `for...in` = Object Loop
- `Object.keys()` = Keys Array
- `Object.entries()` = Array of `[key, value]`