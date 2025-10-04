# 200-JavaScript-Interview-Questions
This repository contains categorized JavaScript questions with answers.

## 📑 Table of Categories

| Category              | Number of Questions | Link to Questions |
|-----------------------|---------------------|------------------|
| 🔴 Basics             | 11                  | [View](#-basics) |
| 🟠 variables & scope  | 10                  | [View](#-variables--scope) |
| 🟡 Functions      | 10                  | [View](#--functions) |
| 🟢 Object & Arrays      | 20                  | [View](#--object--arrays) |
| 🔵 Strings & Numbers      | 10                  | [View](#--strings--numbers) |
| 🟣 DOM Manipulation   | 10                  | [View](#-dom-manipulation) |
| 🟤 Events    | 10                  | [View](#-events-) |
| ⚫ ES6+ Features     | 10                  | [View](#-asynchronous-js) |
| ⚪ Asynchronous JavaScript     | 10                  | [View](#-asynchronous-) |
| 🟥 Advanced Concepts      | 10                  | [View](#-advanced) |
| 🟧 Object-Oriented JavaScript       | 10                  | [View](#-object-oriented-) |
| 🟨 Error Handling       | 10                  | [View](#-error-handling-) |
| 🟩 Browser APIs       | 10                  | [View](#-browser-apis-) |
| 🟦 Performance & Optimization       | 10                  | [View](#-performance-optimization-) |
| 🟪 Security in JavaScript        | 10                  | [View](#-security--) |
| 🟫 Testing & Tools         | 10                  | [View](#-testing-tools-) |
| 📘 Modern Topics        | 10                  | [View](#-modern-topics-) |
| 📙 Tricky & Real-world Questions        | 10                  | [View](#-tricky-real-) |
| 📗 Practical/Scenario-based        | 10                  | [View](#-practical-scenario-) |

## 🔴 Basics

<details>
<summary><b>Q1. What is JavaScript and how is it different from Java?</b></summary> 

👉 JavaScript is a <b>high-level, lightweight, interpreted programming language</b> mainly used for making web pages interactive.

- Runs directly inside the <b>browser (client-side)</b>, though it’s also used on <b>servers (via Node.js)</b>.

- It is the standard scripting language of the web.

  ```js
  document.getElementById("demo").innerHTML = "Hello JavaScript!";
  ```
  This changes the text of an element on a webpage.

  👉 What is Java?

- Java is a <b>general-purpose, object-oriented, compiled programming language.</b>

- Runs on the <b>Java Virtual Machine (JVM)</b>, making it <b>platform-independent (“Write once, run anywhere”).</b>

- Used for <b>desktop apps, enterprise software, mobile apps (Android), and backend systems.</b>

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello Java!");
    }
}
```
This prints a message to the console.
</details>
---
<details>
<summary><b>Q2. What are the different data types in JavaScript?</b></summary>

JavaScript has **two categories** of data types:  

### 1. Primitive Types (immutable, stored by value)
- **String** → `"Hello"`
- **Number** → `42`, `3.14`
- **BigInt** → `12345678901234567890n`
- **Boolean** → `true`, `false`
- **Undefined** → a variable declared but not assigned  
- **Null** → represents an intentional "empty" value  
- **Symbol** → unique and immutable value (often used as object keys)  

```js
let name = "Suborno";     // String
let age = 21;             // Number
let big = 1234567890n;    // BigInt
let isDev = true;         // Boolean
let x;                    // Undefined
let y = null;             // Null
let sym = Symbol("id");   // Symbol
```
### 2. Non-Primitive (Reference) Types
- **Object** → collections of key-value pairs
- **Array** → ordered list of values
- **Function** → callable object

```js
let user = { name: "Suborno", age: 21 }; // Object
let skills = ["JS", "React", "Node"];    // Array
function greet() { return "Hello!"; }    // Function
```
</details>
---
<details>
<summary><b>Q3. What is the difference between <code>null</code> and <code>undefined</code> in JavaScript?</b></summary>

### `undefined`
- A variable that has been declared but **not assigned a value**.  
- Default value of uninitialized variables.  
- Default return value of functions that don’t explicitly return.  

```js
let x; 
console.log(x); // undefined

function test() {}
console.log(test()); // undefined
```

### `null`
- Represents an **intentional absence** of any value. 
- Must be explicitly assigned by the developer. 
- Often used to indicate "no object" or "empty value".  

```js
let y = null;
console.log(y); // null
```
</details>
---
<details>
<summary><b>Q4. What is a "quirk" of JavaScript? Can you give examples?</b></summary>

###  Definition
A **quirk** in JavaScript refers to a behavior that feels **unexpected, confusing, or inconsistent** compared to most programming languages.  
They often come from the way JavaScript was originally designed and how it maintains backward compatibility.

---

###  Common JavaScript Quirks

1. **`typeof null` is "object"**
```js
console.log(typeof null); // "object" 😮
```
👉 This is a historical bug in JS, kept for backward compatibility(new systems still support old features, code, or data so nothing breaks when upgrading.).

2. **`NaN` is a number**
```js
console.log(typeof NaN); // "number"
```
👉 Even though `NaN` means <i>Not-a-Number</i>, its type is `number`.

3. **`==` vs `===` (Type Coercion)**
```js
console.log(0 == "0");    // true
console.log(0 === "0");   // false
```
👉 `==` does type coercion, `===` checks strictly.

4. **Automatic Semicolon Insertion (ASI)**
```js
function test() {
  return
    42;
}
console.log(test()); // undefined

```
👉 Returns `undefined` instead of `42` because JS inserts a semicolon after `return`.

5. **Array + Object Weirdness**
```js
console.log([] + {}); // "[object Object]"
console.log({} + []); // 0
```
👉 Returns `undefined` instead of `42` because JS inserts a semicolon after `return`.

**🔸 Key Takeaway**
JavaScript quirks come from:
- Loose typing system
- Automatic type coercion
- Backward compatibility with old code
- Some design decisions made quickly in its early history.
</details>
---
<details>
<summary><b>Q5. What is <code>NaN</code> in JavaScript?</b></summary>

### 🔹 Definition
`NaN` stands for **Not-a-Number**.  
It is a special value in JavaScript that represents a result which is **not a valid number**.

- Type of `NaN` is actually `"number"` (quirk of JS).  
- It usually appears when you try to perform a **mathematical operation on invalid data**.

---

### 🔹 Examples

```js
console.log(0 / 0);          // NaN
console.log("hello" * 10);   // NaN
console.log(Math.sqrt(-1));  // NaN
console.log(parseInt("abc")); // NaN
```

### 🔹 Checking `NaN`

The tricky part:
```js
console.log(NaN === NaN); // false
```
👉 `NaN` is <b>not equal to itself.</b>

So, to check for `NaN`, use:
```js
isNaN("hello");       // true (loose check)
Number.isNaN("hello"); // false (better strict check)
Number.isNaN(NaN);     // true
```

### 🔸 Key Points

- `NaN` is of type <b>number.</b>
- It represents an invalid numeric operation.
- It is <b>the only JavaScript value not equal to itself.</b>
- Use `Number.isNaN()` for reliable checking.

</details>
---
<details>
<summary><b>Q6. What is the difference between <code>==</code> and <code>===</code> in JavaScript?</b></summary>

### 🔹 `==` (Equality Operator)
- Compares **values only**.  
- Performs **type coercion** (converts operands to the same type before comparison).  

```js
console.log(5 == "5");     // true  (string "5" converted to number 5)
console.log(0 == false);   // true  (false converted to 0)
console.log(null == undefined); // true (special case)
```
### 🔹 `===` (Strict Equality Operator)
- Compares values and types. **values and types.**.  
- No type coercion — both must be the same type to be equal.

```js
console.log(5 === "5");    // false (number vs string)
console.log(0 === false);  // false (number vs boolean)
console.log(null === undefined); // false (different types)
console.log(5 === 5);      // true
```
</details>
---
<details>
<summary><b>Q7. What are "truthy" and "falsy" values in JavaScript?</b></summary>

### 🔹 Definition
In JavaScript, every value is either considered **truthy** or **falsy** when evaluated in a **Boolean context** (like inside an `if` statement).

- **Truthy values** → Treated as `true`
- **Falsy values** → Treated as `false`

### 🔹 Falsy Values
There are only **7 falsy values** in JavaScript:

1. `false`
2. `0`  (zero)
3. `-0` (negative zero)
4. `0n` (BigInt zero)
5. `""` (empty string)
6. `null`
7. `undefined`
8. `NaN`

👉 Everything else is **truthy**.

### 🔹 Examples

```js
if ("hello") {
  console.log("Truthy!"); //  Runs because non-empty string is truthy
}

if (0) {
  console.log("Falsy!");
} else {
  console.log("0 is falsy"); //  Runs
}

if (null) {
  console.log("Falsy!");
} else {
  console.log("null is falsy"); //  Runs
}

```
👉 Knowing truthy and falsy values helps avoid unexpected bugs, especially when using conditions or logical operators (&&, ||, !).

</details>
---
<details>
<summary><b>Q8. What is type coercion in JavaScript? </b></summary>

### 🔹 Definition
**Type coercion** in JavaScript is the process of **automatically or implicitly converting values from one data type to another** (such as converting a string to a number, or a number to a boolean).

JavaScript is a **loosely typed language**, so variables are not bound to a specific type, and coercion happens frequently.


### 🔹 Types of Type Coercion

1. **Implicit Coercion (automatic)**  
Happens when JavaScript automatically converts one type to another during operations.  

  ```js
  console.log("5" - 2);   // 3   ("5" converted to number)
  console.log("5" + 2);   // "52" (2 converted to string, concatenation)
  console.log(1 == "1");  // true (string "1" converted to number)
  ```

2. **Explicit Coercion (manual)**  
   When the developer explicitly converts a type using functions or constructors.

   ```js
   console.log(Number("42"));    // 42
   console.log(String(100));     // "100"
   console.log(Boolean(0));      // false
   ```
### 🔹 Rule 1: Boolean Context (Truthy / Falsy)
When a value is used in a **conditional (`if`, `while`, `!`, `||`, `&&`)**, JS converts it to **boolean**.

- Falsy values: `false, 0, -0, 0n, "", null, undefined, NaN`
- Everything else is truthy

```js
if ("hello") console.log("Truthy"); // runs
if (0) console.log("Falsy");        // doesn’t run
```

### 🔹 Rule 2: Numeric Operators `(- * / % **)`

- All operands are converted to **numbers.**

```js
console.log("5" - 2);   // 3   ("5" → 5)
console.log("10" * "2"); // 20
console.log(true - 1);  // 0   (true → 1)
console.log("abc" / 2); // NaN ("abc" → NaN)
```
### 🔹 Rule 3: The `+` Operator (Special Case)
- If **both operands are numbers** → numeric addition
- If **either operand is a string** → string concatenation

```js
console.log(5 + 2);     // 7   (number + number)
console.log("5" + 2);   // "52" (string + number → concatenation)
console.log(2 + "5");   // "25"
console.log("5" + true); // "5true"
console.log([] + 1);    // "1"   ([] → "" then "" + "1")
console.log([1,2] + [3,4]); // "1,23,4"
```
### 🔹 Rule 4: Comparisons `(==)`
- The **loose equality `(==)` operator** does type coercion.

```js
console.log(5 == "5");      // true   ("5" → 5)
console.log(0 == false);    // true   (false → 0)
console.log(null == undefined); // true (special case)
console.log([] == "");      // true   ([] → "")
console.log([1] == 1);      // true   ([1] → "1" → 1)
```
👉 Always prefer `===` to avoid these pitfalls.


### 🔹 Rule 5: Objects to Primitives
When an object/array is used where a primitive is expected, JS calls:
- `valueOf()`
- If not primitive, then `toString()`

```js
console.log([1,2].toString()); // "1,2"
console.log([1,2] + 3);        // "1,23"
console.log({} + "test");      // "[object Object]test"
```

</details>
---
<details>
<summary><b>Q9. What is Prototype? </b></summary>
<p>

### 🔹 Definition

- A **prototype** is simply **an object** that **another object inherits properties and methods from.**

- Every function in JavaScript (that is used as a constructor) has a `prototype` **property.**

- When an object is created from that function, the object’s internal link (`[[Prototype]]` or __proto__) points to the function’s `prototype.`
Think of a prototype like a **blueprint or template** for objects.

```js
function Person(name) {
  this.name = name;
}

// Add a method to the prototype
Person.prototype.greet = function() {
  console.log(`Hello, I am ${this.name}`);
};

// Create an object
let alice = new Person("Alice");

alice.greet();  // "Hello, I am Alice"
```
What’s happening:

- `alice` doesn’t have `greet` directly.

- JS looks at `alice.__proto__` → which points to `Person.prototype`.

- Finds `greet()` there → executes it.
So **prototype is where objects “inherit” properties and methods from.**
---

### 🔹 Prototype in Arrays and Objects
```js
let arr = [1,2,3];
console.log(arr.__proto__ === Array.prototype); // true
console.log(arr.__proto__.__proto__ === Object.prototype); // true

let obj = {name: "Bob"};
console.log(obj.__proto__ === Object.prototype); // true
```
- `Array.prototype` contains array methods like `.push(), .pop().`
- `Object.prototype` contains general object methods like `.toString()`.
- Objects inherit from their prototype via the **prototype chain**.

Imagine prototypes like linked **“backpacks”**:

```js
obj ---> Object.prototype ---> null
arr ---> Array.prototype ---> Object.prototype ---> null
alice ---> Person.prototype ---> Object.prototype ---> null
```



- Each object carries its own properties.
- If a property is missing, it **looks up the backpack chain** (prototype chain) to find it.

### 🔹 Key Points
- **Every object has a prototype** (except `Object.create(null)`).
- **Prototype itself is an object,** so it can have its own prototype (creating the chain).
- **Methods and properties on the prototype are shared** across all objects created from the constructor.
- `instanceof` checks **if a prototype exists in the chain.**

</details>
---
<details>
<summary><b>Q10. What is the difference between <code>typeof</code> and <code>instanceof</code> in JavaScript?</b></summary>
<p>

### 🔹 Definition

**`typeof`** and **`instanceof`** are both operators used to check types in JavaScript, but they work differently:

- **`typeof`** returns a string indicating the type of a **value or variable**.  
- **`instanceof`** checks whether an **object** belongs to a specific **constructor or class** (i.e., exists in its prototype chain).


### 🔹 `typeof`

- Returns a **string** describing the type.
- Works best for **primitive types**: `number`, `string`, `boolean`, `undefined`, `symbol`, `bigint`.
- For objects, arrays, or `null`, it may return `"object"` (quirk).

```js
console.log(typeof 42);        // "number"
console.log(typeof "hello");   // "string"
console.log(typeof true);      // "boolean"
console.log(typeof undefined); // "undefined"
console.log(typeof null);      // "object"  (quirk!)
console.log(typeof [1,2,3]);   // "object"
console.log(typeof {});        // "object"
```
### 🔹 `instanceof`

- Checks if an **object** is an **instance of a constructor** (class or function).
- Returns **boolean** (`true / false`).
- Works **only on objects**, not primitives.
  
```js
console.log([1,2,3] instanceof Array);          // true
console.log([1,2,3] instanceof Object);         // true (Array inherits from Object)
console.log({} instanceof Object);              // true
console.log("hello" instanceof String);         // false (primitive)
console.log(new String("hello") instanceof String); // true
```
</details>
---
<details>
<summary><b>Q11. What is the difference between <code>var</code>, <code>let</code>, and <code>const</code></b></summary>
<p>

### 🔹 `var`

- **Scope:** Function-scoped (or globally scoped if declared outside a function).
- **Hoisting:** Gets hoisted to the top and initialized with undefined.
- **Re-declaration:** Allowed within the same scope.
- **Re-assignment:** Allowed.

```js
var x = 10;
var x = 20; // re-declaration allowed
console.log(x); // 20

function test() {
  if (true) {
    var y = 5;
  }
  console.log(y); // 5 (function-scoped, not block-scoped)
}
test();
```
### 🔹 `let`

- **Scope:** Block-scoped (only exists inside `{ }`).
- **Hoisting:** Hoisted but **not initialized** (exists in the "temporal dead zone" until declared).
- **Re-declaration:** Not allowed in the same scope.
- **Re-assignment:** Allowed.

```js
let a = 10;
// let a = 20;  Error (cannot re-declare in same scope)
a = 20; //  can re-assign
console.log(a); // 20

{
  let b = 5;
  console.log(b); // 5
}
// console.log(b);  Error (block-scoped)
```
### 🔹 `const`

- **Scope:** Block-scoped (like `let`).
- **Hoisting:** Also in the temporal dead zone until declared.
- **Re-declaration:** Not allowed.
- **Re-assignment:** Not allowed (constant value).

```js
const pi = 3.14;
// pi = 3.1416;  Error (cannot re-assign)

{
  const c = 100;
  console.log(c); // 100
}
// console.log(c);  Error (block-scoped)
```
- Use `let` when the variable will change.
- Use `const` when the variable should not be reassigned.
- Avoid `var` (it’s old and can cause bugs due to function-scoping & hoisting).

</details>

---


## 🟠 variables & scope

<details>
<summary><b>Q12. What is Scope in JavaScript?</b></summary>
<p>

### 🔹 Definition

**Scope** in JavaScript determines where variables, functions, and objects are accessible in our code during execution. It defines the **lifetime and visibility** of variables.

Think of your code as a house:

- Some rooms (functions/blocks) have their own keys (variables).
- Variables can only be used inside the room they belong to, unless they are global keys.

### 🔹 Types of Scope in JavaScript

<b>📘 Global Scope:</b>

A variable declared **outside of any function or block** becomes global. Global variables can be accessed **anywhere in your program.**

```js
let username = "Suborno"; // Global variable
function greet() {
  console.log("Hello " + username); //  Accessible here
}
greet();
console.log(username); //  Accessible here too
```
⚠️ **Risk:** Too many global variables can cause conflicts, since any function can modify them.

<b>📘 Function Scope (Local Scope): </b>

Variables declared inside a **function** are only accessible **inside that function.** They cannot be used outside.

```js
function sayHi() {
  let message = "Hi, I am inside function"; // Local variable
  console.log(message); //  Accessible
}
sayHi();
console.log(message); //  ReferenceError: message is not defined
```
👉 Function scope keeps variables **private** to that function.

<b>📘 Block Scope (introduced in ES6 with let and const):</b>

Variables declared inside a `{ }` block are only accessible **inside that block.** Works with `if`, `for`, `while`, etc.

```js
if (true) {
  let age = 21; // Block scoped
  const country = "Bangladesh"; // Block scoped
  console.log(age, country); //  Accessible
}
console.log(age);     //  Not accessible
console.log(country); //  Not accessible
```
👉 But if you use `var`, it ignores block scope:

```js
if (true) {
  var number = 100; // var is not block scoped
}
console.log(number); // Accessible outside (unexpected behavior)
```
<b>📘 Lexical Scope / Closures:</b>

Inner functions can **access variables from their outer function**. This is called **lexical scoping** (scope is determined by code position, not where it’s executed).

```js
function outer() {
  let outerVar = "I am from outer scope";
  function inner() {
    console.log(outerVar); //  Can access outer variable
  }
  inner();
}
outer();
```
👉 This feature allows **closures**, where a function "remembers" its surrounding scope even after the outer function has finished executing.

</details>
---

<details>
<summary><b>Q13. What is hoisting in JavaScript?</b></summary>
<p>

### 🔹 Definition

**Hoisting** is JavaScript’s default behavior of **moving declarations (not initializations) to the top of their scope** (either the global scope or the function scope) **before code execution.**
This means you can **use variables and functions before they are actually declared** in the code.

### 🔹 How Hoisting Works

1. During the compilation phase, JavaScript scans the code.
2. It registers all variable and function declarations.
3. The declarations are “hoisted” to the top of their scope.
4. But:
  - **Variables declared with** `var` are hoisted and **initialized to** `undefined`.
  - **Variables declared with** `let` and `const` are hoisted but not **initialized** (they stay in the **Temporal Dead Zone** until the declaration line).
  - **Function declarations** are hoisted with their **entire body.**
  - **Function expressions** (with `var`, `let`, or `const`) behave like **variables** (only the variable is hoisted, not the function value).

### 🔹 Examples

<b>📘 Hoisting with `var`:</b>

```js
console.log(a); //  undefined (not ReferenceError)
var a = 5;
console.log(a); //  5
```
➡️ Behind the scenes:
```js
var a;          // Hoisted
console.log(a); // undefined
a = 5;          // Initialization
console.log(a); // 5
```

<b>📘 Hoisting with `let` and `const`:</b>

```js
console.log(b); //  ReferenceError (TDZ)
let b = 10;

console.log(c); //  ReferenceError (TDZ)
const c = 20;
```
👉 These are **hoisted** but not **initialized**, so they cannot be accessed before declaration.

<b>📘 Hoisting with Function Declarations:</b>

```js
greet(); //  Works fine

function greet() {
  console.log("Hello!");
}
```
👉 The entire function is hoisted, so you can call it before the declaration.

<b>📘 Hoisting with Function Expressions:</b>

```js
sayHi(); //  TypeError: sayHi is not a function

var sayHi = function () {
  console.log("Hi!");
};
```
👉 Here only the variable sayHi is **hoisted (initialized to undefined)**, but the **function assignment** happens later, so calling it before throws an error.

<b>📘 Arrow Functions:</b>

Arrow functions are just like function expressions:
```js
hello(); //  ReferenceError or TypeError (depends on var/let/const)

const hello = () => {
  console.log("Hello from arrow!");
};
```

</details>
---

<details>
<summary><b>Q14. Temporal Dead Zone (TDZ) in JavaScript?</b></summary>
<p>

### 🔹 Definition

The **Temporal Dead Zone** refers to the period between the **time** a variable is **hoisted** to the top of its scope and the time it is **initialized** with a value. During this period, if you try to **access the variable**, JavaScript will throw a **ReferenceError.**

### 🔹 Why does it happen?

- Variables declared with `let` and `const` are hoisted to the top of their scope (just like var), BUT they are not **initialized** until the actual declaration line is executed.
- This "gap" between hoisting and initialization is called the **Temporal Dead Zone.**

### 🔹 Example 1: Using let before declaration
```js
console.log(a); // ReferenceError: Cannot access 'a' before initialization
let a = 10;
console.log(a); //  10
```
Here, `a` is hoisted but not initialized until the line `let a = 10`; executes.
So, before that line, it’s in the **TDZ.**

### 🔹 Example 2: With `var`

```js
console.log(b); // undefined (no TDZ for var)
var b = 20;
console.log(b); //  20
```
For `var`, the variable is **hoisted and initialized** to undefined, so there’s no **TDZ.**

### 🔹 Example 3: With `const`

```js
console.log(c); //  ReferenceError
const c = 30;
```
`const` also has a TDZ.
Additionally, it must be initialized at the time of declaration.

</details>
---









