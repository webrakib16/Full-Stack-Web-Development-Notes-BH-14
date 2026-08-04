# ES6 – Class 7: Object Methods

## What I Learned Today

- `Object.keys()`
- `Object.values()`
- `Object.entries()`
- `delete` Operator
- `Object.seal()`
- `Object.freeze()`

---

# Object.keys()

**Object.keys()** (কোনো Object-এর সব Property Name একটি Array আকারে রিটার্ন করে।)

### Syntax

```javascript
Object.keys(objectName);
```

### Example

```javascript
const user = {
  name: "John Doe",
  age: 35,
  id: 40003
};

const keys = Object.keys(user);

console.log(keys);
```

### Output

```javascript
["name", "age", "id"]
```

---

# Object.values()

**Object.values()** (Object-এর সব Property Value একটি Array হিসেবে রিটার্ন করে।)

### Syntax

```javascript
Object.values(objectName);
```

### Example

```javascript
const values = Object.values(user);

console.log(values);
```

### Output

```javascript
["John Doe", 35, 40003]
```

---

# Object.entries()

**Object.entries()** (Object-এর প্রতিটি Property-কে `[key, value]` Pair হিসেবে একটি Array-এর ভিতরে Array আকারে রিটার্ন করে।)

### Syntax

```javascript
Object.entries(objectName);
```

### Example

```javascript
const entries = Object.entries(user);

console.log(entries);
```

### Output

```javascript
[
  ["name", "John Doe"],
  ["age", 35],
  ["id", 40003]
]
```

> মনে রাখবে: **Entries = Array of Arrays**

---

# Loop Through Object

### Using Object.keys()

```javascript
const keys = Object.keys(user);

for (const key of keys) {
  console.log(key, user[key]);
}
```

### Output

```javascript
name John Doe
age 35
id 40003
```

---

# Loop Through Object.entries()

```javascript
const entries = Object.entries(user);

for (const item of entries) {
    const [key, value] = item;
    console.log(key, value);
}
```

### আরও Short Version

```javascript
for (const [key, value] of Object.entries(user)) {
    console.log(key, value);
}
```

---

# delete Operator

**delete** (Object থেকে কোনো Property সম্পূর্ণ Remove করে দেয়।)

### Syntax

```javascript
delete object.property;
```

### Example

```javascript
const user = {
    name: "Rakib",
    age: 24
};

delete user.age;

console.log(user);
```

### Output

```javascript
{
   name: "Rakib"
}
```

---

# Object.seal()

**Object.seal()** (Object-কে Seal করে দেয়। নতুন Property যোগ করা বা Delete করা যায় না, কিন্তু Existing Property-এর Value পরিবর্তন করা যায়।)

### Syntax

```javascript
Object.seal(objectName);
```

### Example

```javascript
const bankAccount = {
    accountNumber: "1234",
    balance: 5000
};

Object.seal(bankAccount);

bankAccount.balance = 300;
delete bankAccount.balance;
bankAccount.newName = "ABC";

console.log(bankAccount);
```

### Output

```javascript
{
    accountNumber: "1234",
    balance: 300
}
```

---

# Object.freeze()

**Object.freeze()** (Object-কে সম্পূর্ণ Lock করে দেয়। Add, Delete কিংবা Edit—কোনোটাই করা যায় না।)

### Syntax

```javascript
Object.freeze(objectName);
```

### Example

```javascript
const birthCertificate = {
    name: "Rakib",
    birthDate: "05-05-2006"
};

Object.freeze(birthCertificate);

birthCertificate.name = "Rahim";
delete birthCertificate.birthDate;
birthCertificate.new = "Test";

console.log(birthCertificate);
```

### Output

```javascript
{
    name: "Rakib",
    birthDate: "05-05-2006"
}
```

---

# seal() vs freeze()

| Feature | Object.seal() | Object.freeze() |
|----------|---------------|-----------------|
| Add Property | ❌ | ❌ |
| Delete Property | ❌ | ❌ |
| Edit Existing Value | ✅ | ❌ |
| Object Locked | Partially | Completely |

---

# Quick Comparison

| Method | Returns |
|---------|----------|
| Object.keys() | Array of Keys |
| Object.values() | Array of Values |
| Object.entries() | Array of `[key, value]` |
| delete | Removes Property |
| Object.seal() | Prevents Add & Delete |
| Object.freeze() | Prevents Add, Delete & Edit |

---

# Common Mistakes

### ❌ Wrong

```javascript
console.log(user.key);
```

### ✅ Correct

```javascript
console.log(user[key]);
```

---

### ❌ Wrong

```javascript
for (const item of Object.entries(user)) {
    console.log(item.key);
}
```

### ✅ Correct

```javascript
for (const [key, value] of Object.entries(user)) {
    console.log(key, value);
}
```

---

### ❌ Wrong

```javascript
Object.freeze(user);

user.age = 30;
```

ভাববে Value Update হবে।

### ✅ Reality

কোনো পরিবর্তন হবে না।

---

# Interview Questions

### Q1. `Object.keys()` কী Return করে?

**Answer:** Object-এর সব Property Name-এর Array।

---

### Q2. `Object.values()` কী Return করে?

**Answer:** Object-এর সব Property Value-এর Array।

---

### Q3. `Object.entries()` কী Return করে?

**Answer:** Array of Arrays (`[key, value]`)।

---

### Q4. `delete` কী করে?

**Answer:** Object থেকে Property Remove করে।

---

### Q5. `Object.seal()` এবং `Object.freeze()`-এর পার্থক্য কী?

**Answer:**

- `seal()` → Edit করা যায়, Add/Delete করা যায় না।
- `freeze()` → Add, Delete, Edit—কোনোটাই করা যায় না।

---

# Memory Trick

- 🔑 **keys() → শুধু Key**
- 📦 **values() → শুধু Value**
- 🧩 **entries() → Key + Value Pair**
- 🗑️ **delete → Property Remove**
- 🔒 **seal → Edit Allowed**
- ❄️ **freeze → Everything Locked**

---

# One Minute Revision

- `Object.keys()` → Keys Array
- `Object.values()` → Values Array
- `Object.entries()` → Array of `[key, value]`
- `delete` → Property Remove
- `Object.seal()` → Add/Delete বন্ধ, Edit Allowed
- `Object.freeze()` → Add/Delete/Edit সব বন্ধ