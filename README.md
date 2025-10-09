# 200-JavaScript-Interview-Questions
This repository contains categorized JavaScript questions with answers.

## 📑 Table of Categories

| Category              | Number of Questions | Link to Questions |
|-----------------------|---------------------|------------------|
| 🔴 Basics             | 11                  | [View](#-basics) |
| 🟠 variables & scope  | 10                  | [View](#-variables--scope) |
| 🟡 Functions      | 10                  | [View](#-functions) |
| 🟢 Object & Arrays      | 20                  | [View](#-object--arrays) |
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

** 🔴 Key Takeaway**
JavaScript quirks come from:
- Loose typing system
- Automatic type coercion
- Backward compatibility with old code
- Some design decisions made quickly in its early history.
</details>
---
<details>
<summary><b>Q5. What is <code>NaN</code> in JavaScript?</b></summary>

### 🔴 Definition
`NaN` stands for **Not-a-Number**.  
It is a special value in JavaScript that represents a result which is **not a valid number**.

- Type of `NaN` is actually `"number"` (quirk of JS).  
- It usually appears when you try to perform a **mathematical operation on invalid data**.

---

### 🔴 Examples

```js
console.log(0 / 0);          // NaN
console.log("hello" * 10);   // NaN
console.log(Math.sqrt(-1));  // NaN
console.log(parseInt("abc")); // NaN
```

### 🔴 Checking `NaN`

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

### 🔴 Key Points

- `NaN` is of type <b>number.</b>
- It represents an invalid numeric operation.
- It is <b>the only JavaScript value not equal to itself.</b>
- Use `Number.isNaN()` for reliable checking.

</details>
---
<details>
<summary><b>Q6. What is the difference between <code>==</code> and <code>===</code> in JavaScript?</b></summary>

### 🔴 `==` (Equality Operator)
- Compares **values only**.  
- Performs **type coercion** (converts operands to the same type before comparison).  

```js
console.log(5 == "5");     // true  (string "5" converted to number 5)
console.log(0 == false);   // true  (false converted to 0)
console.log(null == undefined); // true (special case)
```
### 🔴 `===` (Strict Equality Operator)
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

### 🔴 Definition
In JavaScript, every value is either considered **truthy** or **falsy** when evaluated in a **Boolean context** (like inside an `if` statement).

- **Truthy values** → Treated as `true`
- **Falsy values** → Treated as `false`

### 🔴 Falsy Values
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

### 🔴 Examples

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

### 🔴 Definition
**Type coercion** in JavaScript is the process of **automatically or implicitly converting values from one data type to another** (such as converting a string to a number, or a number to a boolean).

JavaScript is a **loosely typed language**, so variables are not bound to a specific type, and coercion happens frequently.


### 🔴 Types of Type Coercion

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
### 🔴 Rule 1: Boolean Context (Truthy / Falsy)
When a value is used in a **conditional (`if`, `while`, `!`, `||`, `&&`)**, JS converts it to **boolean**.

- Falsy values: `false, 0, -0, 0n, "", null, undefined, NaN`
- Everything else is truthy

```js
if ("hello") console.log("Truthy"); // runs
if (0) console.log("Falsy");        // doesn’t run
```

### 🔴 Rule 2: Numeric Operators `(- * / % **)`

- All operands are converted to **numbers.**

```js
console.log("5" - 2);   // 3   ("5" → 5)
console.log("10" * "2"); // 20
console.log(true - 1);  // 0   (true → 1)
console.log("abc" / 2); // NaN ("abc" → NaN)
```
### 🔴 Rule 3: The `+` Operator (Special Case)
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
### 🔴 Rule 4: Comparisons `(==)`
- The **loose equality `(==)` operator** does type coercion.

```js
console.log(5 == "5");      // true   ("5" → 5)
console.log(0 == false);    // true   (false → 0)
console.log(null == undefined); // true (special case)
console.log([] == "");      // true   ([] → "")
console.log([1] == 1);      // true   ([1] → "1" → 1)
```
👉 Always prefer `===` to avoid these pitfalls.


### 🔴 Rule 5: Objects to Primitives
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

### 🔴 Definition

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

### 🔴 Prototype in Arrays and Objects
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

### 🔴 Key Points
- **Every object has a prototype** (except `Object.create(null)`).
- **Prototype itself is an object,** so it can have its own prototype (creating the chain).
- **Methods and properties on the prototype are shared** across all objects created from the constructor.
- `instanceof` checks **if a prototype exists in the chain.**

</details>
---
<details>
<summary><b>Q10. What is the difference between <code>typeof</code> and <code>instanceof</code> in JavaScript?</b></summary>
<p>

### 🔴 Definition

**`typeof`** and **`instanceof`** are both operators used to check types in JavaScript, but they work differently:

- **`typeof`** returns a string indicating the type of a **value or variable**.  
- **`instanceof`** checks whether an **object** belongs to a specific **constructor or class** (i.e., exists in its prototype chain).


### 🔴 `typeof`

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
### 🔴 `instanceof`

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

### 🔴 `var`

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
### 🔴 `let`

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
### 🔴 `const`

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

### 🟠 Definition

**Scope** in JavaScript determines where variables, functions, and objects are accessible in our code during execution. It defines the **lifetime and visibility** of variables.

Think of your code as a house:

- Some rooms (functions/blocks) have their own keys (variables).
- Variables can only be used inside the room they belong to, unless they are global keys.

### 🟠 Types of Scope in JavaScript

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

### 🟠 Definition

**Hoisting** is JavaScript’s default behavior of **moving declarations (not initializations) to the top of their scope** (either the global scope or the function scope) **before code execution.**
This means you can **use variables and functions before they are actually declared** in the code.

### 🟠 How Hoisting Works

1. During the compilation phase, JavaScript scans the code.
2. It registers all variable and function declarations.
3. The declarations are “hoisted” to the top of their scope.
4. But:
  - **Variables declared with** `var` are hoisted and **initialized to** `undefined`.
  - **Variables declared with** `let` and `const` are hoisted but not **initialized** (they stay in the **Temporal Dead Zone** until the declaration line).
  - **Function declarations** are hoisted with their **entire body.**
  - **Function expressions** (with `var`, `let`, or `const`) behave like **variables** (only the variable is hoisted, not the function value).

### 🟠 Examples

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

### 🟠 Definition

The **Temporal Dead Zone** refers to the period between the **time** a variable is **hoisted** to the top of its scope and the time it is **initialized** with a value. During this period, if you try to **access the variable**, JavaScript will throw a **ReferenceError.**

### 🟠 Why does it happen?

- Variables declared with `let` and `const` are hoisted to the top of their scope (just like var), BUT they are not **initialized** until the actual declaration line is executed.
- This "gap" between hoisting and initialization is called the **Temporal Dead Zone.**

### 🟠 Example 1: Using let before declaration
```js
console.log(a); // ReferenceError: Cannot access 'a' before initialization
let a = 10;
console.log(a); //  10
```
Here, `a` is hoisted but not initialized until the line `let a = 10`; executes.
So, before that line, it’s in the **TDZ.**

### 🟠 Example 2: With `var`

```js
console.log(b); // undefined (no TDZ for var)
var b = 20;
console.log(b); //  20
```
For `var`, the variable is **hoisted and initialized** to undefined, so there’s no **TDZ.**

### 🟠 Example 3: With `const`

```js
console.log(c); //  ReferenceError
const c = 30;
```
`const` also has a TDZ.
Additionally, it must be initialized at the time of declaration.

</details>
---

<details>
<summary><b>Q15. Why You Should Avoid <code>var</code> in JavaScript? </b></summary>
<p>

Modern JavaScript provides `let` and `const`, which fix many of the long-standing issues with `var`. While `var` still works, using it can easily lead to bugs and unexpected behavior.

### 🟠 Why does it happen?

- Variables declared with `let` and `const` are hoisted to the top of their scope (just like var), BUT they are not **initialized** until the actual declaration line is executed.
- This "gap" between hoisting and initialization is called the **Temporal Dead Zone.**

### 🟠 Example 1: `var` Has `Function Scope`, Not `Block Scope` *This is the biggest problem.*
```js
if (true) {
  var x = 10;
}
console.log(x); //  10 (still accessible outside the block)
```
- Compare this to let or const:
```js
if (true) {
  let y = 20;
}
console.log(y); //  ReferenceError: y is not defined
```
👉 `var` ignores block boundaries (`if`, `for`, etc.), *which can cause variable leaks and overwrite values accidentally.*

### 🟠 Example 2: `var` Allows Re-declaration *You can declare the same variable multiple times without error:*
```js
var name = "Suborno";
var name = "Maksuda"; //  No error
console.log(name); // "Maksuda"
```
- With `let` or `const`, this would throw an error:
```js
let name = "Suborno";
let name = "Maksuda"; //  SyntaxError
```
👉 This helps prevent accidental overwriting.

### 🟠 Example 3: `var` Variables Are Hoisted (in a confusing way)
All var declarations are hoisted to the top of their function or script, but not their **values** — leading to unexpected behavior:
```js
console.log(num); // undefined (not ReferenceError!)
var num = 5;
```
- What really happens:
```js
var num; // hoisted
console.log(num); // undefined
num = 5;
```
👉 With `let` and `cons`t, you get a **Temporal Dead Zone (TDZ)** error instead, which prevents you from using variables before they’re initialized.

```js
console.log(num); //  ReferenceError
let num = 5;
```
### 🟠 Example 4: `var` Pollutes the `Global Scope`

If you use `var` outside any function, it becomes a property of the `window` object in browsers:
```js
var message = "Hello";
console.log(window.message); // "Hello"
```

👉 This can cause naming conflicts with existing global variables or libraries. `let` and `const` don’t do this — they stay within the block/module scope.

### 🟠 Example 5: `let` and `const` Are the Modern Standard

Since ES6 (2015), almost all modern JS code uses let and const.
👉 They make code:
  - More predictable
  - Easier to debug
  - Safer from accidental bugs
  - Easier for others to understand
    
</details>
---

<details>
<summary><b>Q16. Difference between <code>shallow copy</code> and <code>deep copy</code> in js. </b></summary>
<p>

### 🟠 1. Shallow Copy — “Copied from the outside only”

Imagine you have a **box** (your object). Inside that box, there are **smaller boxes** (nested objects). A shallow copy makes a new outer box,
but **the smaller boxes inside are still shared between the old and new one.**

### 🟠 Example : 
```js
const original = {
  name: "Suborno",
  details: { city: "Dhaka", age: 22 }
};

// make a shallow copy
const copy = { ...original };

// change something inside 'details'
copy.details.city = "Chittagong";

console.log(original.details.city); //  "Chittagong"

```
👉 Think of it like:
  - You bought a new box, but you took the same little box from the old one and placed it inside — so both boxes share the same inner item. So when you change the inner box, both are affected.

### 🟠 2. Deep Copy — “Copied completely inside and out”

A deep copy makes **a brand new box and also makes new copies of every small box inside it**. That means it’s completely **separate from the original.**

### 🟠 Example : 
```js
const original = {
  name: "Suborno",
  details: { city: "Dhaka", age: 22 }
};

// make a deep copy
const deepCopy = structuredClone(original);

// change the city in deepCopy
deepCopy.details.city = "Chittagong";

console.log(original.details.city); // "Dhaka"

```
👉 This time:
  - You bought a **new box**, and you also made **new little boxes inside it** — so changing one doesn’t affect the other.
        
</details>
---

<details>
<summary><b>Q17. Difference between <code>reference types</code> and <code>primitive types</code> in js. </b></summary>
<p>

### 🟠 1. Definition

| Type              | Description |
|-----------------------|----------------------|
| **Primitive Types**             | Store **single, immutable values** (cannot be changed directly). |
| **Reference Types**             | Store **references (addresses)** to objects in memory, not the actual data. |

### 🟠 Primitive Types : 

There are 7 primitive data types:
- `String` – e.g. `"Hello"`
- `Number` – e.g. `42`
- `Boolean` – e.g. `true`
- `Undefined` – variable declared but not assigned
- `Null` – intentional empty value
- `Symbol` – unique and immutable value
- `BigInt` – large integer value


```js
let x = 10;
let y = x;   // y gets a COPY of x
y = 20;
console.log(x); // 10 (not affected)
```
**→ Each variable holds its own copy of the value.**

### 🟠 Reference Types : 

Common **reference types:**
- `Object`
- `Array` 
- `function` 
- `Date`, `Map`,`Set`, etc.

```js
let obj1 = { name: "Suborno" };
let obj2 = obj1;   // obj2 gets a REFERENCE to obj1
obj2.name = "Maksuda";

console.log(obj1.name); // Maksuda
```
**→ Both variables point to the same memory address.**

### 🟠 Comparison Behaviour : 

```js
// Primitive comparison
let a = 5;
let b = 5;
console.log(a === b); // true  (same value)

// Reference comparison
let arr1 = [1, 2];
let arr2 = [1, 2];
console.log(arr1 === arr2); // false (different memory reference)
```

| Features              | Primitive Types | Reference Types |
|-----------------------|-----------------|-----------------------------|
| Stored in             | Stack           | Heap (with stack reference) |
| What’s Stored            | Actual value           | Memory address (reference) |
| Mutable?            | No. Changing `x` creates a new value           | Mutable. Can change properties or elements directly |
| Copied by           | Value           | Reference |
| Comparison           | By Value           | By Reference |

</details>
---

<details>
<summary><b>Q18. Why are objects assigned by <code>reference</code> in JavaScript? </b></summary>
<p>

### 🟠 1. Definition

In JavaScript, **objects are assigned by reference** because they are **complex data structures** that can contain many properties, arrays, and nested objects.

If JavaScript tried to **copy the whole object** each time you assigned it to another variable, it would:

- Consume a lot of **memory**, and
- Take extra **processing time.**
  
So instead of copying the entire structure, JS simply copies the **memory address (reference)** where the object is stored.

### 🟠 Stack vs Heap memory : 
JavaScript divides memory into two main areas:

| Memory Area              | Used For | Characteristics |
|-----------------------|-----------------|-----------------------------|
| Stack             | Primitive values           | Small, fast access, fixed-size data |
| Heap            | Objects & functions           | Large, dynamic memory storage |

➡️ When you create an object:
```js
let person = { name: "Suborno" };
```
- The **actual object** `{ name: "Suborno" }` is stored in the heap.
- The variable `person` stores only a **reference (memory address)** in the **stack.**

When you do this:

```js
let person2 = person;
```
👉 JavaScript does **not** create a new object. Instead, it copies only the **reference (pointer)** to the same object in memory.

So now:
- `person` → points to the object in heap
- `person2` → points to the **same** object in heap

that's why: 
```js
person2.name = "Maksuda";
console.log(person.name); // "Maksuda"
```
Both variables reflect the same data — they share the same memory reference.

### 🟠 Why this design makes sense : 
There are **two main reasons:**

1. **Efficiency** → Copying large objects by value would be slow and memory-heavy.
2. **Consistency** → Objects can be nested and dynamic, so referencing them allows real-time updates across variables and functions.

</details>
---

<details>
<summary><b>Q18.  What are global variables and why should you avoid them? </b></summary>
<p>

### 🟠 1. Definition

In JavaScript, a **global variable** is a variable that is declared **outside of any function, block, or module**, and therefore it is **accessible from anywhere in your code** — inside **functions, loops, or even other scripts.**

```js
let count = 0; // global variable

function increment() {
  count++; // accessible inside the function
  console.log(count);
}

increment(); // 1
increment(); // 2
```
Here, `count` is a **global variable** — it exists in the **global scope**, which means it can be accessed or modified from any part of the script.

### 🟠 Why You Should Avoid Global Variables: 

Using too many **global variables** is considered **bad practice**. Here’s why:

1. ***Risk of Name Conflicts (Collisions):***

  - If two scripts (e.g., your code and a third-party library) use the same global variable name, one can overwrite the other.
```js
var user = "Alice";  // your variable
// Some library also defines 'user'
var user = "Bob";    // now your 'user' got overwritten!
```

2. ***Harder to Debug and Maintain:***

  - When many functions modify the same global variable, it’s difficult to track where and when changes happen.

- Bugs can appear unexpectedly.

3. ***Memory Usage and Lifetime Issues:***

  - Global variables stay in memory as long as the page or program is running, which can lead to unnecessary memory consumption.

4. ***Tight Coupling:***

  - Code becomes less modular and reusable because functions rely on global state instead of their own data.

5. ***Security Concerns:***

  - In browsers, global variables become properties of the `window` object. This means other scripts can easily read or change them:

```js
window.myGlobal = "secret";
// Any script can access or modify it
```
### 🟠 How to Avoid Global Variables: 

1. **Use `let`, `const`, or `var` inside functions or blocks**
```js
function run() {
  let result = 5; // local variable
  console.log(result);
}
```

2. **Use modules (ES6 Modules):**
```js
// file.js
export const name = "Suborno";

// main.js
import { name } from "./file.js";
```

3. **Use closures to encapsulate variables:**
```js
(function() {
  let counter = 0;
  function add() { counter++; }
  window.add = add; // only expose what’s needed
})();
```
</details>
---

## 🟡 Functions 

<details>
<summary><b>Q19.  What are <code>function declarations</code> vs <code>function expressions?</code> </b></summary>
<p>

### 🟡 Function Declaration: 

A **function declaration** defines a named function using the `function` keyword.

```js
function greet() {
  console.log("Hello!");
}
```

<b>Key Features:</b>

- Hoisted: You can call the function before it’s declared in the code.
- Has its own name (`greet`).
- Defined in the global or local scope (depending on where it’s written).

<b>Example: </b>

```js
sayHi(); // Works, because function declarations are hoisted

function sayHi() {
  console.log("Hi there!");
}
```

### 🟡 Function Expression: 

A **function expression** involves creating a function and assigning it to a variable.

```js
const greet = function() {
  console.log("Hello!");
};
```

<b>Key Features:</b>

- Not hoisted: You **cannot** call it before the line where it’s defined.
- Can be **anonymous** (no name) or **named.**
- Treated like a **value** — it can be passed around, assigned, or returned from another function.

<b>Example: </b>

```js
sayHi(); //  Error: Cannot access 'sayHi' before initialization

const sayHi = function() {
  console.log("Hi there!");
};

```

### 🟡 Bonus:: 

```js
const greet = () => console.log("Hello!");
```
It’s a **type of function expression** — concise, not hoisted, and does not bind its own `this.`

</details>
---

<details>
<summary><b>Q20.  What are <code>arrow functions</code> and how are they different? </b></summary>
<p>

An **arrow function** is a shorter, cleaner way to write a function expression in JavaScript. It uses the `=>` (arrow) syntax.

```js
// Regular function expression
const greet = function(name) {
  return "Hello, " + name;
};

// Arrow function version
const greet = (name) => {
  return "Hello, " + name;
};
```
Or even shorter (if there’s only one line of code and one parameter):
```js
const greet = name => "Hello, " + name;
```

### 🟡 Syntax Summary: 

|      Type      |     Example   |     Notes     |
|----------------|---------------|---------------|
| **No parameters** | `() => console.log("Hi")` | Must include parentheses |
| **One parameter** | `name => console.log(name)` | Parentheses optional |
| **Multiple parameters** | `(a, b) => a + b` | Parentheses required |
| **Multiple statements** | `(x, y) => { let sum = x + y; return sum; }` | Use `{}` and `return` |

### 🟡 How Are Arrow Functions Different? 

|      Feature      |     Arrow Function   |     Regular Function (Expression or Declaration)     |
|----------------|---------------|---------------|
| **Syntax**   | Short & concise (`=>`)  | Longer (`function`)
| `this` **binding** | Lexically bound – uses `this` from the surrounding scope | Has its own `this` (depends on how it’s called) |
| `arguments` **object** | Not available | Available |
| `new` **keyword** | Cannot be used as a constructor | Can be used with `new` |
| **Hoisting** | Not hoisted | Function declarations are hoisted |
| **Readability** | Cleaner for small callbacks | Can be verbose |


### 🟡 Example of `this` Difference

```js
// Regular function
const user = {
  name: "Suborno",
  sayHi: function() {
    console.log("Hi, I’m " + this.name);
  }
};
user.sayHi(); // "Hi, I’m Suborno"
```
Now with an arrow function:
```js
const user = {
  name: "Suborno",
  sayHi: () => {
    console.log("Hi, I’m " + this.name);
  }
};
user.sayHi(); //  "Hi, I’m undefined"
```

👉 Because arrow functions **don’t have their own** `this`, they use `this` from the **outer scope**, which in this case isn’t `user`.

### 🟡 When to Use Arrow Functions: 

- Short, inline functions
- Callbacks (like in `map`, `filter`, `forEach`)
- Event handlers that don’t rely on `this`

</details>
---

<details>
<summary><b>Q21.  What are <code>higher-order</code> functions? </b></summary>
<p>

A **higher-order function** is a function that operates on other functions, either by **taking them as parameters** or **returning them**.

### 🟡 Function taking another function as an argument

```js
function greet(name) {
  return `Hello, ${name}!`;
}

function processUserInput(callback) {
  const name = "Suborno";
  return callback(name);
}

console.log(processUserInput(greet)); 
// Output: Hello, Suborno!
```

👉 `processUserInput()` is a **higher-order function** because it **takes another function** (`greet`) **as an argument.**

### 🟡 Function returning another function

```js
function multiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = multiplier(2);
console.log(double(5)); // Output: 10
```
👉 `multiplier()` is a **higher-order function** because it **returns another function.**

### 🟡 Common Built-in Higher-Order Functions
These are **array methods** that use callbacks:

```js
const numbers = [1, 2, 3, 4, 5];

// map() → transforms each element
const doubled = numbers.map(n => n * 2);

// filter() → selects elements based on condition
const evens = numbers.filter(n => n % 2 === 0);

// reduce() → combines all elements into a single value
const sum = numbers.reduce((acc, n) => acc + n, 0);

console.log(doubled); // [2, 4, 6, 8, 10]
console.log(evens);   // [2, 4]
console.log(sum);     // 15
}
```
👉 Each of these functions (`map`, `filter`, `reduce`) **takes another function as an argument**, so they are **higher-order functions**.

### 🟡 Why Use Higher-Order Functions?
- Make code **more modular and reusable**
- Allow **functional programming** style
- Simplify **data transformations**
- Enable **composition** of behavior

</details>
---


<details>
<summary><b>Q22.  What are <code>first-class functions</code>?</b></summary>
<p>

In **JavaScript, functions are first-class citizens (or first-class functions)** — meaning **functions are treated like any other value** in the language.

### 🟡 Definition

A **first-class function** means that functions in JavaScript can:
- Be **assigned** to variables,
- Be **passed** as arguments to other functions,
- Be **returned** from other functions,
- Be **stored** in data structures (like arrays, objects, etc).

### 🟡 Example 1 : Assigning a function to a variable

```js
const greet = function() {
  console.log("Hello!");
};

greet(); // Output: Hello!
}
```
👉 Here, the function is stored in a variable — just like a number or string.

### 🟡 Example 2 : Passing a function as an argument

```js
function sayHello() {
  return "Hello!";
}

function greetUser(callback) {
  console.log(callback());
}

greetUser(sayHello); // Output: Hello!
```
👉 `sayHello` is passed as an argument (a callback) to `greetUser.`

### 🟡 Example 3 : Returning a function from another function

```js
function multiplyBy(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = multiplyBy(2);
console.log(double(5)); // Output: 10

```
👉 Here, `multiplyBy` returns a new function — this is possible because functions are first-class.

### 🟡 Example 4 : Storing functions in arrays or objects

```js
const actions = [
  () => console.log("Start"),
  () => console.log("Stop")
];

actions[0](); // Output: Start
actions[1](); // Output: Stop
```
</details>
---


<details>
<summary><b>Q24. Difference between <code>synchronous</code> and <code>asynchronous</code> callbacks.</b></summary>
<p>

A **callback function is a function that is passed as an argument** to another function **and is executed later** (or “called back”) inside that other function. So, A **callback** is a function that gets **called back** after something happens.

### 🟡 Why use callbacks?

Callbacks are used when:

- You want to **control the order** of function execution.
- You want to **run code after** something else finishes (like loading data, waiting for a user’s input, etc).
- You want **reusable functions** that can behave differently depending on the callback.

### 🟡 Example 

```js
function greet(name) {
  console.log(`Hello, ${name}!`);
}

function processUserInput(callback) {
  const name = "Suborno";
  callback(name); // calling the callback
}

processUserInput(greet);

```
👉 Explanation:

  - `greet` is a function.
  - `processUserInput` takes another function as a parameter (`callback`).
  - Inside `processUserInput`, we “call back” that function with the name `"Suborno"`.
  - So the output is → `Hello, Suborno!`

### 🟡 Example with Anonymous Callback:

Instead of naming the callback, we can define it directly:

```js
processUserInput(function(name) {
  console.log(`Welcome, ${name}!`); //Welcome, Suborno!
});
```
</details>
---

<details>
<summary><b>Q25. What is <code>function currying</code>?</b></summary>
<p>

### 🟡 Definition

**Function currying** means **transforming a function that takes multiple arguments into a sequence of functions,**
each taking **one argument at a time.**

### 🟡 Why do this? 

Currying helps you:
- Reuse functions with **preset arguments** (partial application)
- Make your code **more modular and flexible**
- Delay execution until all arguments are provided

### 🟡 Example 1: Normal Function (uncurried)

```js
function add(a, b, c) {
  return a + b + c;
}

console.log(add(2, 3, 4)); // Output: 9

```

### 🟡 Example 2: Curried Function

```js
function add(a) {
  return function(b) {
    return function(c) {
      return a + b + c;
    };
  };
}

console.log(add(2)(3)(4)); // Output: 9

```

👉 Here, 
- `add(2)` returns a new function that expects `b`.
- `add(2)(3)` returns another function that expects `c`.
- `add(2)(3)(4)` finally returns the result → `9`.

### 🟡 Arrow Function Version

You can make it shorter with arrow syntax:
```js
const add = a => b => c => a + b + c;

console.log(add(2)(3)(4)); // Output: 9
```

### 🟡 Real-life Example
Imagine you have a function that formats messages:

```js
function greet(greeting) {
  return function(name) {
    return `${greeting}, ${name}!`;
  };
}

const sayHello = greet("Hello");
console.log(sayHello("Suborno")); // Output: Hello, Suborno!
console.log(sayHello("Maksuda")); // Output: Hello, Maksuda!

```
👉 Here, The first call `greet("Hello")` “locks in” the greeting word.
Then you can reuse it for different names — `that’s the power of currying.`



</details>
---

<details>
<summary><b>Q26. What are <code>pure functions</code> in JavaScript?</b></summary>
<p>

In **JavaScript**, a **pure function** is a function that follows **two main rules:**

### 🟡 Same Input → Same Output 

A pure function always returns the **same result** if given the **same arguments.** It doesn’t depend on or modify anything outside of itself.

### 🟡 Example

```js
function add(a, b) {
  return a + b;
}
```
👉 `add(2, 3)` will always return `5`, no matter when or how many times you call it.

### 🟡 No Side Effects

A pure function **does not change** anything outside its own scope.
That means:

- It doesn’t modify global variables.
- It doesn’t change input parameters.
- It doesn’t perform I/O operations (like logging, writing to a file, or making a network request).

### 🟡 Example (Impure function):

```js
let total = 0;
function addToTotal(value) {
  total += value; //  modifies external variable
}
```
### 🟡 Example (Pure version):

```js
function addToTotal(total, value) {
  return total + value; // ✅ no external modification
}

```

### 🟡 Why Use Pure Functions?

- **Predictable behavior** → easier debugging
- **Easier testing** → no external dependencies
- **Functional programming** foundation (used in React, Redux, etc.)
  
</details>
---


<details>
<summary><b>Q27. What is the difference between <code>call</code>, <code>apply</code>, and <code>bind</code>?</b></summary>
<p>

### 🟡 `call()` — Call immediately, pass arguments separately

```js
const person1 = { name: "Alice" };
const person2 = { name: "Bob" };

function introduce(city, country) {
  console.log(`${this.name} is from ${city}, ${country}.`);
}
// Using call()
introduce.call(person1, "Dhaka", "Bangladesh");
introduce.call(person2, "Paris", "France");

```

### 🟡 Output

```js
Alice is from Dhaka, Bangladesh.
Bob is from Paris, France.
```
- `call()` executes the function **immediately.**
- Arguments are passed **one by one** (comma-separated).
- `this` becomes the object you pass as the first argument.


### 🟡 `apply()` — Call immediately, pass args as an array

```js
const person1 = { name: "Alice" };
const person2 = { name: "Bob" };

function introduce(city, country) {
  console.log(`${this.name} is from ${city}, ${country}.`);
}

// Using apply()
introduce.apply(person1, ["Chittagong", "Bangladesh"]);
introduce.apply(person2, ["London", "UK"]);
```

### 🟡 Output

```js
Alice is from Chittagong, Bangladesh.
Bob is from London, UK.
```
- Works like `call()`, but the arguments are passed as an **array**.
- Very handy when you already have arguments stored in an array.

### 🟡 `bind()` — Does NOT call immediately

```js
const person1 = { name: "Alice" };
const person2 = { name: "Bob" };

function introduce(city, country) {
  console.log(`${this.name} is from ${city}, ${country}.`);
}

// Using bind()
const introduceAlice = introduce.bind(person1, "Sylhet", "Bangladesh");
const introduceBob = introduce.bind(person2);

// Call later
introduceAlice();           // uses default args passed during bind
introduceBob("Rome", "Italy"); // pass remaining args later

```

### 🟡 Output

```js
Alice is from Sylhet, Bangladesh.
Bob is from Rome, Italy.
```
- `bind()` creates a **new function** where `this` is permanently set.
- You can provide some or all arguments now (partial application).
- You call the function **later**, whenever you need.

</details>
---

<details>
<summary><b>Q28. How do you create <code>objects</code> in JavaScript?</b></summary>
<p>

### 🟡 Object Literal (Easiest and Most Common)

This is the simplest and fastest way.

```js
const person = {
  name: "Alice",
  age: 25,
  greet: function() {
    console.log("Hello!");
  }
};

person.greet(); // Output: Hello!
```
- Easy to read and write.
- Great for creating single objects.
- Not ideal when you need to create many similar objects.


### 🟡 Using the `new Object()` Constructor

```js
const person = new Object();
person.name = "Bob";
person.age = 30;
person.greet = function() {
  console.log("Hi, I'm " + this.name);
};

person.greet(); // Output: Hi, I'm Bob
```
- Similar to object literal, but created dynamically.
- More verbose and less common than literals.

### 🟡 Using a Constructor Function

A constructor function is used when you want to create **multiple similar objects.**

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function() {
    console.log("Hello, I'm " + this.name);
  };
}

const p1 = new Person("Alice", 25);
const p2 = new Person("Bob", 30);

p1.greet(); // Hello, I'm Alice
p2.greet(); // Hello, I'm Bob

```
- Useful for object templates.
- Functions are duplicated in each instance (can be optimized using prototypes).

### 🟡 Using `Object.create()`
Creates a new object with a **specified prototype**.

```js
const personProto = {
  greet() {
    console.log("Hello, I'm " + this.name);
  }
};

const person = Object.create(personProto);
person.name = "Charlie";

person.greet(); // Output: Hello, I'm Charlie
```

- Great for prototype-based inheritance.
- Slightly less intuitive for beginners.

### 🟡 Using ES6 `class` Syntax
Classes are just **syntactic sugar** over constructor functions.

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hi, I'm ${this.name}`);
  }
}

const person1 = new Person("Diana", 22);
person1.greet(); // Output: Hi, I'm Diana
```

- Cleaner and modern syntax.
- Easy to use inheritance with `extends`.

</details>
---

## 🟢 Object & Arrays


<details>
<summary><b>Q29. How do you create <code>objects</code> in JavaScript?</b></summary>
<p>

### 🟢 Object Literal (Easiest and Most Common)

This is the simplest and fastest way.

```js
const person = {
  name: "Alice",
  age: 25,
  greet: function() {
    console.log("Hello!");
  }
};

person.greet(); // Output: Hello!
```
- Easy to read and write.
- Great for creating single objects.
- Not ideal when you need to create many similar objects.


### 🟢 Using the `new Object()` Constructor

```js
const person = new Object();
person.name = "Bob";
person.age = 30;
person.greet = function() {
  console.log("Hi, I'm " + this.name);
};

person.greet(); // Output: Hi, I'm Bob
```
- Similar to object literal, but created dynamically.
- More verbose and less common than literals.

### 🟢 Using a Constructor Function

A constructor function is used when you want to create **multiple similar objects.**

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.greet = function() {
    console.log("Hello, I'm " + this.name);
  };
}

const p1 = new Person("Alice", 25);
const p2 = new Person("Bob", 30);

p1.greet(); // Hello, I'm Alice
p2.greet(); // Hello, I'm Bob

```
- Useful for object templates.
- Functions are duplicated in each instance (can be optimized using prototypes).

### 🟢 Using `Object.create()`
Creates a new object with a **specified prototype**.

```js
const personProto = {
  greet() {
    console.log("Hello, I'm " + this.name);
  }
};

const person = Object.create(personProto);
person.name = "Charlie";

person.greet(); // Output: Hello, I'm Charlie
```

- Great for prototype-based inheritance.
- Slightly less intuitive for beginners.

### 🟢 Using ES6 `class` Syntax
Classes are just **syntactic sugar** over constructor functions.

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Hi, I'm ${this.name}`);
  }
}

const person1 = new Person("Diana", 22);
person1.greet(); // Output: Hi, I'm Diana
```

- Cleaner and modern syntax.
- Easy to use inheritance with `extends`.

</details>
---

<details>
<summary><b>Q29. What are <code>object prototypes</code> in JavaScript?</b></summary>
<p>

### 🟢 Definition

In **JavaScript**, every object has a hidden internal property called `[[Prototype]]`, which points to another object — known as its **prototype.**

This prototype object serves as a **template** from which the original object can **inherit properties and methods**.

Prototypes are how **JavaScript implements inheritance**.

If you try to access a property or method on an object and it doesn’t exist there, JavaScript automatically looks for it in the object’s **prototype**.

### 🟢 Example 

```js
const person = {
  greet() {
    console.log("Hello!");
  }
};

const student = Object.create(person); // student’s prototype is person
student.name = "Alice";

student.greet(); // "Hello!" (inherited from person)

```
- `student` doesn’t have `greet()`.
- JavaScript checks its prototype (`person`) and finds `greet()`.
- The method runs successfully.

### 🟢 Constructor Functions and Prototypes 

When you create objects using a **constructor function**, all instances share the same prototype.

```js
function Person(name) {
  this.name = name;
}

Person.prototype.sayHi = function() {
  console.log(`Hi, I'm ${this.name}`);
};

const p1 = new Person("Alice");
const p2 = new Person("Bob");

p1.sayHi(); // "Hi, I'm Alice"
p2.sayHi(); // "Hi, I'm Bob"

```
Both `p1` and `p2` share the same `sayHi()` method through `Person.prototype`.

### 🟢 Modern ES6 Class Syntax (Behind the scenes uses prototypes)

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  }
}

const p = new Person("Alice");
p.greet(); // "Hello, I'm Alice"
```
Even though it looks like a class, under the hood, JavaScript is still using **prototypes**.

</details>
---


<details>
<summary><b>Q30. What is <code>Prototype Chain</code> in JavaScript?</b></summary>
<p>

### 🟢 Definition

The **prototype chain** is the mechanism JavaScript uses to **look up properties and methods**.
- Every object has a hidden link to its prototype (`[[Prototype]]`).
- If a property or method is not found on the object itself, JavaScript **checks the prototype**.
- If it’s not found there, it checks the prototype of that prototype, and so on, until it reaches the top: `Object.prototype`.
- If nothing is found, it returns `undefined`.

Think of it like a **family tree for objects**: each object can inherit from a parent, which can inherit from a grandparent, and so on.

### 🟢 Example 

```js
const grandparent = {
  grandparentProp: "I am grandparent"
};

const parent = Object.create(grandparent);
parent.parentProp = "I am parent";

const child = Object.create(parent);
child.childProp = "I am child";

console.log(child.childProp);      // "I am child" (found on child)
console.log(child.parentProp);     // "I am parent" (found on parent prototype)
console.log(child.grandparentProp);// "I am grandparent" (found on grandparent prototype)
console.log(child.toString());     // [object Object] (found on Object.prototype)

```

Here’s the **prototype chain** visually:
```js
child ---> parent ---> grandparent ---> Object.prototype ---> null
```
- Arrows (`--->`) show the `[[Prototype]]` link.
- When you access a property, JS searches along this chain until it finds it.

</details>
---

<details>
<summary><b>Q31. Difference between <code>Object.create()</code> and <code>class-based</code> inheritance.</b></summary>
<p>

### 🟢 `Object.create()` — *Direct Prototypal Inheritance*

`Object.create(proto)` creates a **new object** and directly sets its **prototype** to the object you specify.

```js
const person = {
  greet() {
    console.log("Hello!");
  }
};

const student = Object.create(person); // student inherits directly from person
student.study = function() {
  console.log("Studying...");
};

student.greet(); // "Hello!" (inherited)
student.study(); // "Studying..."

```
- Simple and direct.
- No constructor functions.
- No `this` or `new` keyword needed.
- Best for **object-to-object** inheritance.
- Very flexible — you can even change prototypes at runtime.
- Think of it as “**inherit from this specific object**.”

### 🟢 Class-based Inheritance — *Syntactic Sugar for Prototypes*

Classes in JavaScript use **constructor functions** and **prototypes**, but the syntax looks like classical OOP (like Java or C++).

```js
class Person {
  greet() {
    console.log("Hello!");
  }
}

class Student extends Person {
  study() {
    console.log("Studying...");
  }
}

const s = new Student();
s.greet(); // "Hello!" (inherited from Person)
s.study(); // "Studying..."

```
- Uses `class` and `extends` keywords.
- Behind the scenes, JS sets `Student.prototype.__proto__ = Person.prototype`.
- Cleaner syntax for developers coming from other OOP languages.
- Ideal when you need **constructors, super calls**, and **structured inheritance.**
- Think of it as “**inherit from this class’s prototype.**”


|      Feature    |   `Object.create()`     |   **Class-based**(`class`/`extends`)    |
|------------------|-----------------------|--------------------|
|      Type    |   Object-to-object inheritance     |   Class (constructor)-based inheritance    |
|      Syntax    |   Functional / prototype-based    |   Declarative / class syntax    |
|      How it works    |   Creates a new object and sets its prototype directly     |   Uses constructor functions and prototype chaining    |
|      Ease of Use    |   Simple for small objects     |   Better for structured, large-scale code    |
|      `this` keyword    |   Optional     |   Commonly used inside constructors    |
|      Inheritance setup    |   Manual (`Object.create(proto)`)    |   Automatic (`extends` keyword)    |
|      Flexibility    |   More flexible, dynamic     |   More structured, but less flexible    |
|      Under the hood    |   Uses prototypes directly     |   Uses prototypes (syntactic sugar)    |


</details>
---


<details>
<summary><b>Q32. How do you <code>merge</code> objects in JavaScript?</b></summary>
<p>

### 🟢 Using `Object.assign()`

It copies properties from one or more **source** objects into a **target** object.

```js
const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };

const merged = Object.assign({}, obj1, obj2);
console.log(merged); // { a: 1, b: 3, c: 4 }
```
- It modifies the **first argument** (the target).
- Later sources **overwrite** earlier properties with the same key.
- To avoid mutating existing objects, pass an empty `{}` as the first argument.

  
### 🟢 Using the Spread Operator (`...`)

```js
const obj1 = { a: 1, b: 2 };
const obj2 = { b: 3, c: 4 };

const merged = { ...obj1, ...obj2 };
console.log(merged); // { a: 1, b: 3, c: 4 }

```
- The spread operator is a **modern and concise** way to merge.
- Works like `Object.assign()`, overwriting properties from left to right.
- Doesn’t mutate the original objects.

### 🟢 Deep Merging (Nested Objects)

Both `Object.assign()` and spread only perform a **shallow merge** (they don’t merge nested objects).

**Example of a problem**
```js
const obj1 = { a: { x: 1 } };
const obj2 = { a: { y: 2 } };

const merged = { ...obj1, ...obj2 };
console.log(merged); // { a: { y: 2 } } ; x is lost
```
**Solution**: Use a **deep merge** approach.

**Option 1 — Write a recursive function:**

```js
function deepMerge(target, source) {
  for (let key in source) {
    if (
      typeof source[key] === "object" &&
      !Array.isArray(source[key]) &&
      source[key] !== null
    ) {
      if (!target[key]) target[key] = {};
      deepMerge(target[key], source[key]);
    } else {
      target[key] = source[key];
    }
  }
  return target;
}

const obj1 = { a: { x: 1 } };
const obj2 = { a: { y: 2 } };

console.log(deepMerge({}, obj1, obj2)); // { a: { x: 1, y: 2 } }
```

**Option 2 — Use a library like Lodash:**

```js
// Using Lodash
_.merge(obj1, obj2);

```
</details>
--- 


<details>
<summary><b>Q33. What is <code>object destructuring</code>?</b></summary>
<p>

### 🟢 Definition

**Object destructuring** in **JavaScript** is a convenient way to **extract values from objects** and assign them to variables in a single statement.

It makes your code **cleaner, shorter**, and **more readable**.

```js
const person = {
  name: "Alice",
  age: 25,
  country: "Bangladesh"
};

// Destructuring
const { name, age } = person;

console.log(name); // Alice
console.log(age);  // 25

```
- `name` and `age` are extracted from the `person` object.
- You don’t need to write `person.name` or `person.age` repeatedly.

```js
const person = { name: "Alice", age: 25 };

const { name: fullName, age: years } = person;

console.log(fullName); // Alice
console.log(years);    // 25

```
The syntax `name: fullName` means "take the `name` property and store it in a variable called `fullName`."

### 🟢 Nested object destructuring:

```js
const user = {
  id: 101,
  info: {
    name: "Bob",
    city: "Dhaka"
  }
};

const { info: { name, city } } = user;

console.log(name); // Bob
console.log(city); // Dhaka

```
### 🟢 Using destructuring in function parameters:
You can destructure objects directly in function parameters:

```js
function displayUser({ name, age }) {
  console.log(`Name: ${name}, Age: ${age}`);
}

const user = { name: "Sara", age: 22 };
displayUser(user); // Name: Sara, Age: 22
```

</details>
--- 

<details>
<summary><b>Q34. What is <code>object destructuring</code>?</b></summary>
<p>

### 🟢 Definition

**Object destructuring** in **JavaScript** is a convenient way to **extract values from objects** and assign them to variables in a single statement.

It makes your code **cleaner, shorter**, and **more readable**.

```js
const person = {
  name: "Alice",
  age: 25,
  country: "Bangladesh"
};

// Destructuring
const { name, age } = person;

console.log(name); // Alice
console.log(age);  // 25

```
- `name` and `age` are extracted from the `person` object.
- You don’t need to write `person.name` or `person.age` repeatedly.

```js
const person = { name: "Alice", age: 25 };

const { name: fullName, age: years } = person;

console.log(fullName); // Alice
console.log(years);    // 25

```
The syntax `name: fullName` means "take the `name` property and store it in a variable called `fullName`."

### 🟢 Nested object destructuring:

```js
const user = {
  id: 101,
  info: {
    name: "Bob",
    city: "Dhaka"
  }
};

const { info: { name, city } } = user;

console.log(name); // Bob
console.log(city); // Dhaka

```
### 🟢 Using destructuring in function parameters:
You can destructure objects directly in function parameters:

```js
function displayUser({ name, age }) {
  console.log(`Name: ${name}, Age: ${age}`);
}

const user = { name: "Sara", age: 22 };
displayUser(user); // Name: Sara, Age: 22
```

</details>
--- 


<details>
<summary><b>Q35. What are object methods like <code>keys()</code>, <code>values()</code>, <code>entries()</code>?</b></summary>
<p>

### 🟢 Definition

In JavaScript, `Object.keys()`, `Object.values()`, and `Object.entries()` are **built-in object methods** that help you work with the properties (keys and values) of an object.

### 🟢 `Object.keys()`

```js
const person = { name: "Suborno", age: 21, city: "Dhaka" };

console.log(Object.keys(person));//["name", "age", "city"]
```
👉 Returns an array of **all the property names (keys)** of an object.

### 🟢 `Object.values()`

```js
const person = { name: "Suborno", age: 21, city: "Dhaka" };

console.log(Object.values(person)); //["Suborno", 21, "Dhaka"]

```
👉 Returns an array of **all the property values** of an object.

### 🟢 `Object.entries()`

```js
const person = { name: "Suborno", age: 21, city: "Dhaka" };

console.log(Object.entries(person));
```

**Output**
```js
[
  ["name", "Suborno"],
  ["age", 21],
  ["city", "Dhaka"]
]
```

You can even loop through these entries easily:

```js
for (const [key, value] of Object.entries(person)) {
  console.log(`${key}: ${value}`);
}
```
**Output**
```js
name: Suborno
age: 21
city: Dhaka

```
👉 Returns an array of **[key, value] pairs** from the object — each key-value pair becomes a small array.

</details>
--- 



<details>
<summary><b>Q36. How to <code>freeze</code> or <code>seal</code> an object? </b></summary>
<p>

### 🟢 Why We Use `Object.freeze()` or `Object.seal()`

These methods are mainly about controlling changes to your data and protecting object integrity — especially in large applications.

### 🧊 1. To prevent accidental changes

Sometimes you want an object’s data to stay constant.

```js
const CONFIG = {
  appName: "MyApp",
  version: "1.0"
};

Object.freeze(CONFIG);
```
👉 Now no one can change `CONFIG.version` by mistake anywhere in your code.
It’s a safe constant.

### 🧊 2. To maintain data integrity

If your object represents important or shared data (like settings, user roles, or API responses), freezing/sealing ensures other parts of your program **don’t modify it unexpectedly.**

```js
const roles = { admin: "full", user: "limited" };
Object.freeze(roles);

// Later in another file:
roles.user = "full"; //  Won’t work

```
👉 Keeps your system consistent and prevents bugs.

### 🧊 3. To create predictable, reliable code
### 🧊 4. When using objects as constants or configs
### 🧊 5. To prevent mutation in functional programming


### 🟢 `Object.freeze()`

**Purpose:**
Makes an object completely immutable — you can’t:
- Add new properties 
- Remove existing properties 
- Change existing property values 

```js
const person = { name: "Suborno", age: 21 };

Object.freeze(person);

person.age = 25;       //  Won’t change
person.city = "Dhaka"; //  Won’t add
delete person.name;    //  Won’t delete

console.log(person); // { name: "Suborno", age: 21 }
```
👉 The object stays **frozen** — no modification possible.

### 🟢 `Object.seal()`

**Purpose:**
Makes an object **partially immutable** — you can modify existing property values.

But you can’t:
- Add new properties
- Delete existing ones

```js
const car = { brand: "Toyota", color: "red" };

Object.seal(car);

car.color = "blue";   //  Allowed (you can modify)
car.model = "Corolla"; //  Not added
delete car.brand;      //  Not deleted

console.log(car); //{ brand: "Toyota", color: "blue" }
```
### 🟢 Check the object’s status

You can check whether an object is sealed or frozen:

```js
Object.isSealed(car);  // true
Object.isFrozen(person); // true

```
</details>
--- 


<details>
<summary><b>Q37. Difference between shallow equality <code>(==)</code> and <code>deep equality</code> in objects. </b></summary>
<p>

### 🟢 Shallow Equality (`==` or `===`)

In JavaScript, when you compare **objects** using `==` or `===`, you are comparing references, not contents.

That means:
- It checks whether **both variables point to the same object in memory**,
not whether their properties are equal.

```js
const obj1 = { name: "Suborno" };
const obj2 = { name: "Suborno" };
const obj3 = obj1;

console.log(obj1 === obj2); //  false
console.log(obj1 === obj3); //  true

```
👉 **Explanation:**

- `obj1` and `obj2` have the same content but live in **different memory locations.**
- `obj1` and `obj3` point to the **same object**, so they are equal.

### 🟢 Deep Equality

**Deep equality** means comparing the **actual contents (keys and values)** of two objects — not their memory references.
JavaScript doesn’t do this automatically — you have to check it yourself (or use libraries like Lodash).

```js
const obj1 = { name: "Suborno", age: 21 };
const obj2 = { name: "Suborno", age: 21 };

// Manual deep check
function isDeepEqual(a, b) {
  const keysA = Object.keys(a);
  const keysB = Object.keys(b);

  if (keysA.length !== keysB.length) return false;

  for (let key of keysA) {
    if (a[key] !== b[key]) return false;
  }

  return true;
}

console.log(isDeepEqual(obj1, obj2)); //  true

```
</details>
--- 

<details>
<summary><b>Q38. Difference between <code>for</code>, <code>for...in<code>, and <code>for...of<code>. </b></summary>
<p>

### 🟢 `for` loop

The **traditional** loop — used when you know how many times you want to repeat something (usually for arrays or numbers).

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```
👉 **Best For:**

- Looping a **specific number of times**
- Accessing array elements **by index**

### 🟢 Example:

```js
const fruits = ["apple", "banana", "mango"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]); // apple banana mango
}
```

### 🟢 `for...in` loop

Used for **iterating over the keys (property names)** of an **object**.

```js
for (let key in object) {
  // use key and object[key]
}
```
👉 `for...in` works on **objects**, not arrays (though you can use it on arrays, it’s not recommended because the order is not guaranteed).

### 🟢 Example:

```js
const person = { name: "Suborno", age: 21, city: "Dhaka" };

for (let key in person) {
  console.log(key, ":", person[key]);
}

Output:
name : Suborno
age : 21
city : Dhaka

```

### 🟢 `for...of` loop

Used to **iterate over iterable objects** — such as **arrays, strings, Maps, Sets**, etc. It gives **values**, not keys.

```js
for (let value of iterable) {
  // use value
}
```
👉 **Note**

- Works on **iterables** (arrays, strings, maps, sets)
- Doesn’t work directly on plain objects

### 🟢 Example:

```js
const fruits = ["apple", "banana", "mango"];

for (let fruit of fruits) {
  console.log(fruit);
}

Output:
apple
banana
mango
```

### 🟢 Quick Example Comparison:

```js
const arr = ["a", "b", "c"];
const obj = { x: 10, y: 20 };

// for
for (let i = 0; i < arr.length; i++) console.log(arr[i]); // a b c

// for...in
for (let key in obj) console.log(key, obj[key]); // x 10, y 20

// for...of
for (let value of arr) console.log(value); // a b c

```
</details>
--- 


<details>
<summary><b>Q39. Difference between <code>for</code>, <code>for...in<code>, and <code>for...of<code>. </b></summary>
<p>

### 🟢 `for` loop

The **traditional** loop — used when you know how many times you want to repeat something (usually for arrays or numbers).

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```
👉 **Best For:**

- Looping a **specific number of times**
- Accessing array elements **by index**

### 🟢 Example:

```js
const fruits = ["apple", "banana", "mango"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]); // apple banana mango
}
```

### 🟢 `for...in` loop

Used for **iterating over the keys (property names)** of an **object**.

```js
for (let key in object) {
  // use key and object[key]
}
```
👉 `for...in` works on **objects**, not arrays (though you can use it on arrays, it’s not recommended because the order is not guaranteed).

### 🟢 Example:

```js
const person = { name: "Suborno", age: 21, city: "Dhaka" };

for (let key in person) {
  console.log(key, ":", person[key]);
}

Output:
name : Suborno
age : 21
city : Dhaka

```

### 🟢 `for...of` loop

Used to **iterate over iterable objects** — such as **arrays, strings, Maps, Sets**, etc. It gives **values**, not keys.

```js
for (let value of iterable) {
  // use value
}
```
👉 **Note**

- Works on **iterables** (arrays, strings, maps, sets)
- Doesn’t work directly on plain objects

### 🟢 Example:

```js
const fruits = ["apple", "banana", "mango"];

for (let fruit of fruits) {
  console.log(fruit);
}

Output:
apple
banana
mango
```

### 🟢 Quick Example Comparison:

```js
const arr = ["a", "b", "c"];
const obj = { x: 10, y: 20 };

// for
for (let i = 0; i < arr.length; i++) console.log(arr[i]); // a b c

// for...in
for (let key in obj) console.log(key, obj[key]); // x 10, y 20

// for...of
for (let value of arr) console.log(value); // a b c

```
</details>
--- 
