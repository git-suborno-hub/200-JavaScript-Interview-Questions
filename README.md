# 200-JavaScript-Interview-Questions
This repository contains categorized JavaScript questions with answers.

## 📑 Table of Categories

| Category              | Number of Questions | Link to Questions |
|-----------------------|---------------------|------------------|
| 🔴 Basics             | 11                  | [View](#-basics) |
| 🟠 variables & scope  | 10                  | [View](#-variables--scope) |
| 🟡 Functions      | 10                  | [View](#-functions) |
| 🟢 Object & Arrays      | 20                  | [View](#-object--arrays) |
| 🔵 Strings & Numbers      | 10                  | [View](#-strings--numbers) |
| 🟣 DOM Manipulation   | 10                  | [View](#-dom-manipulation) |
| 🟤 Events    | 10                  | [View](#-events) |
| ⚫ ES6+ Features     | 10                  | [View](#-es-features) |
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

🔴 JavaScript is a <b>high-level, lightweight, interpreted programming language</b> mainly used for making web pages interactive.

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

### 🔴 `undefined`
- A variable that has been declared but **not assigned a value**.  
- Default value of uninitialized variables.  
- Default return value of functions that don’t explicitly return.  

```js
let x; 
console.log(x); // undefined

function test() {}
console.log(test()); // undefined
```

### 🔴 `null`
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

### 🔴 Definition
A **quirk** in JavaScript refers to a behavior that feels **unexpected, confusing, or inconsistent** compared to most programming languages.  
They often come from the way JavaScript was originally designed and how it maintains backward compatibility.

---

### 🔴 Common JavaScript Quirks

1.  **`typeof null` is "object"**
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

### Examples

```js
console.log(0 / 0);          // NaN
console.log("hello" * 10);   // NaN
console.log(Math.sqrt(-1));  // NaN
console.log(parseInt("abc")); // NaN
```

### Checking `NaN`

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

### Key Points

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

### Examples

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
###  Rule 1: Boolean Context (Truthy / Falsy)
When a value is used in a **conditional (`if`, `while`, `!`, `||`, `&&`)**, JS converts it to **boolean**.

- Falsy values: `false, 0, -0, 0n, "", null, undefined, NaN`
- Everything else is truthy

```js
if ("hello") console.log("Truthy"); // runs
if (0) console.log("Falsy");        // doesn’t run
```

###  Rule 2: Numeric Operators `(- * / % **)`

- All operands are converted to **numbers.**

```js
console.log("5" - 2);   // 3   ("5" → 5)
console.log("10" * "2"); // 20
console.log(true - 1);  // 0   (true → 1)
console.log("abc" / 2); // NaN ("abc" → NaN)
```
###  Rule 3: The `+` Operator (Special Case)
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
###  Rule 4: Comparisons `(==)`
- The **loose equality `(==)` operator** does type coercion.

```js
console.log(5 == "5");      // true   ("5" → 5)
console.log(0 == false);    // true   (false → 0)
console.log(null == undefined); // true (special case)
console.log([] == "");      // true   ([] → "")
console.log([1] == 1);      // true   ([1] → "1" → 1)
```
👉 Always prefer `===` to avoid these pitfalls.


###  Rule 5: Objects to Primitives
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
<summary><b>Q1. What is Scope in JavaScript?</b></summary>
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
<summary><b>Q2. What is hoisting in JavaScript?</b></summary>
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
<summary><b>Q3. Temporal Dead Zone (TDZ) in JavaScript?</b></summary>
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
<summary><b>Q4. Why You Should Avoid <code>var</code> in JavaScript? </b></summary>
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
<summary><b>Q5. Difference between <code>shallow copy</code> and <code>deep copy</code> in js. </b></summary>
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
<summary><b>Q6. Difference between <code>reference types</code> and <code>primitive types</code> in js. </b></summary>
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
<summary><b>Q7. Why are objects assigned by <code>reference</code> in JavaScript? </b></summary>
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
<summary><b>Q8.  What are global variables and why should you avoid them? </b></summary>
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
<summary><b>Q1.  What are <code>function declarations</code> vs <code>function expressions?</code> </b></summary>
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
<summary><b>Q2.  What are <code>arrow functions</code> and how are they different? </b></summary>
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
<summary><b>Q3.  What are <code>higher-order</code> functions? </b></summary>
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
<summary><b>Q4.  What are <code>first-class functions</code>?</b></summary>
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
<summary><b>Q5. Difference between <code>synchronous</code> and <code>asynchronous</code> callbacks.</b></summary>
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
<summary><b>Q6. What is <code>function currying</code>?</b></summary>
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
<summary><b>Q7. What are <code>pure functions</code> in JavaScript?</b></summary>
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
<summary><b>Q8. What is the difference between <code>call</code>, <code>apply</code>, and <code>bind</code>?</b></summary>
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
<summary><b>Q9. How do you create <code>objects</code> in JavaScript?</b></summary>
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
<summary><b>Q1. How do you create <code>objects</code> in JavaScript?</b></summary>
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
<summary><b>Q2. What are <code>object prototypes</code> in JavaScript?</b></summary>
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
<summary><b>Q3. What is <code>Prototype Chain</code> in JavaScript?</b></summary>
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
<summary><b>Q4. Difference between <code>Object.create()</code> and <code>class-based</code> inheritance.</b></summary>
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
<summary><b>Q5. How do you <code>merge</code> objects in JavaScript?</b></summary>
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
<summary><b>Q6. What is <code>object destructuring</code>?</b></summary>
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
<summary><b>Q7. What is <code>object destructuring</code>?</b></summary>
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
<summary><b>Q8. What are object methods like <code>keys()</code>, <code>values()</code>, <code>entries()</code>?</b></summary>
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
<summary><b>Q9. How to <code>freeze</code> or <code>seal</code> an object? </b></summary>
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
<summary><b>Q10. Difference between shallow equality <code>(==)</code> and <code>deep equality</code> in objects. </b></summary>
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
<summary><b>Q11. Difference between <code>for</code>, <code>for...in</code>, and <code>for...of</code>. </b></summary>
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
<summary><b>Q12. Difference between <code>map</code>, <code>forEach</code>, and <code>filter</code>.</b></summary>
<p>

### 🟢 map()

To create a **new array** by transforming each element.

**Returns:** A **new array**
**Does not modify** the original array

### 🟢 Syntax:

```js
const newArray = array.map((element, index, array) => {
  // return transformed element
});

```
### 🟢 Example:

```js
const numbers = [1, 2, 3, 4];
const squares = numbers.map(num => num * num);
console.log(squares); // [1, 4, 9, 16]

```
👉 `map()` goes through each item, applies the callback, and returns a new array of the results.

### 🟢 forEach()

To perform an **action** on each element (like printing or updating), **not** to return a new array.

**Returns:** `undefined`
**Used for side effects** (like console logs, DOM updates, etc.)
**Does not create a new array** 

### 🟢 Syntax:

```js
array.forEach((element, index, array) => {
  // perform an action
});

```
### 🟢 Example:

```js
const numbers = [1, 2, 3, 4];
numbers.forEach(num => console.log(num * 2));
// Output: 2, 4, 6, 8

```
👉 `forEach()` executes the function for each item but doesn’t return anything.

### 🟢 filter()

To create a **new array** that includes only elements that pass a certain condition (test).

**Returns:** A new filtered array
**Does not modify** the original array 

### 🟢 Syntax:

```js
const newArray = array.filter((element, index, array) => {
  return condition;
});

```
### 🟢 Example:

```js
const numbers = [1, 2, 3, 4, 5];
const even = numbers.filter(num => num % 2 === 0);
console.log(even); // [2, 4]

```
👉 `filter()` only includes elements that make the callback return `true`.

</details>
--- 

<details>
<summary><b>Q13. Difference between <code>find</code> and <code>findIndex</code>.</b></summary>
<p>

### 🟢 Definiton

Both `find()` and `findIndex()` are **array methods in JavaScript** used to **search for elements**, but they return **different types of results**.

### 🟢 find()

Returns the **first element** in the array that **satisfies a condition.**

**Returns:** The **element itself**
**If no match is found:** Returns `undefined`

### 🟢 Syntax:

```js
array.find((element, index, array) => {
  return condition;
});
```
### 🟢 Example:

```js
const numbers = [10, 20, 30, 40];
const result = numbers.find(num => num > 25);
console.log(result); // 30

```
👉 `find()` returns the **first matching value** — here, `30` is the first number greater than 25.

### 🟢 findIndex()

Returns the **index** (position) of the **first element** that satisfies a condition.

**Returns:** The **index (number)**
**If no match is found:** Returns `-1`

### 🟢 Syntax:

```js
array.findIndex((element, index, array) => {
  return condition;
});

```
### 🟢 Example:

```js
const numbers = [10, 20, 30, 40];
const index = numbers.findIndex(num => num > 25);
console.log(index); // 2
```
👉 `findIndex()` returns the **position** — here, `30` is at index `25`.

</details>
---


<details>
<summary><b>Q14. How does <code>reduce()</code> works in JS?</b></summary>
<p>

`reduce()` is used to **reduce an array to a single value** by executing a function on each element of the array.

### 🟢 Syntax:

```js
array.reduce(callbackFunction, initialValue)
```
**Parameters:**

1. **callbackFunction** -> A function that runs on each element.
   - It takes **four** arguments:
     ```js
     function (accumulator, currentValue, currentIndex, array)
     ```
    - `accumulator` : the value that results from the previous iteration.
    - `currentValue` : the current array element being processed.
    - `currentIndex` (optional) : the current index.
    - `array` (optional) : the original array.

2. **initialValue** -> (optional) a value to start with.
   - If not provided, the first array element is used as the initial accumulator, and iteration starts from the **second element**.

### 🟢 Example 1: Sum of Numbers

```js
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce((acc, curr) => acc + curr, 0);

console.log(sum); // Output: 15
```

### 🟢 Example 2: Flatten an Array

```js
const nested = [[1, 2], [3, 4], [5]];

const flat = nested.reduce((acc, curr) => acc.concat(curr), []);

console.log(flat); // Output: [1, 2, 3, 4, 5]
```

### 🟢 Example 3: Count Occurrences

```js
const fruits = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple'];

const count = fruits.reduce((acc, fruit) => {
  acc[fruit] = (acc[fruit] || 0) + 1;
  return acc;
}, {});

console.log(count);
// Output: { apple: 3, banana: 2, orange: 1 }

```
### 🟢 Example 4: Find Max Value

```js
const nums = [5, 12, 8, 20, 7];

const max = nums.reduce((acc, curr) => (curr > acc ? curr : acc));

console.log(max); // Output: 20

```

</details>
---


<details>
<summary><b>Q15. Difference between <code>some()</code> and <code>every()</code>.</b></summary>
<p>

|     Method   |    Purpose    |    Returns    |
|--------------|----------------|---------------|
|  `some()`   | Checks if **at least one** element meets a condition   |  `true`/`false`|
|  `every()`   | Checks if `all` elements meet a condition   |  `true`/`false`|

### 🟢 Syntax (both are similar)

```js
array.some(callback(element, index, array))
array.every(callback(element, index, array))
```
Both methods:
- Loop through the array.
- Stop early (short-circuit) once the result is known.
- Return a **boolean** (`true` or `false`).


### 🟢 Example 1: Using `some()`

```js
const numbers = [1, 3, 5, 7, 9];

const hasEven = numbers.some(num => num % 2 === 0);

console.log(hasEven); // Output: false

```
Explanation:
- `some()` checks each number — none are even → returns `false`. If the array was `[1, 3, 4, 7]`, it would return `true` because **4 is even.**

### 🟢 Example 2: Using `every()`

```js
const numbers = [2, 4, 6, 8];

const allEven = numbers.every(num => num % 2 === 0);

console.log(allEven); // Output: true

```
Explanation:
- `every()` checks if all numbers are even — they are → returns `true`. If the array was `[2, 3, 6, 8]`, it would return `false` because **3 is not even.**

</details>
---


<details>
<summary><b>Q16. Difference between <code>push()</code>, <code>pop()</code>, <code>shift()</code> and <code>unshift()</code>.</b></summary>
<p>

|     Method   |    Works On    |    Description    |   Returns      |   Example    |
|--------------|----------------|---------------|------------------|----------|
|  `push()`   | End of array   |  Adds one or more elements **to the end** of an array.  |  New length of the array   |      `arr.push(4)`   |
|  `pop()`   | End of array   |  **Removes the last** element from an array.  |  The removed element   |      `arr.pop()`   |
|  `shift()`   | Beginning of array   |  **Removes the first** element from an array.  |  The removed element   |      `arr.shift()`   |
|  `unshift()`   | Beginning of array   |  Adds one or more elements **to the beginning** of an array.  |  New length of the array   |      `arr.unshift(0)`   |

### 🟢 Example: 

```js
let arr = [1, 2, 3];

// push() → add at end
arr.push(4);    
console.log(arr); // [1, 2, 3, 4]

// pop() → remove last
arr.pop();       
console.log(arr); // [1, 2, 3]

// shift() → remove first
arr.shift();     
console.log(arr); // [2, 3]

// unshift() → add at beginning
arr.unshift(1);  
console.log(arr); // [1, 2, 3]

```

</details>
---


<details>
<summary><b>Q17. What is <code>array destructuring</code>? </b></summary>
<p>

### 🟢 Definition: 

**Array destructuring** in **JavaScript** is a shorthand way to **extract values from an array** and **assign them to variables** in a single, clean line.

### 🟢 Example: 

```js
const numbers = [10, 20, 30];

const [a, b, c] = numbers;

console.log(a); // 10
console.log(b); // 20
console.log(c); // 30
```

### 🟢 Skipping Elements: 

You can skip unwanted values by leaving empty commas:

```js
const [first, , third] = [1, 2, 3];
console.log(first); // 1
console.log(third); // 3
```

### 🟢 Default Values: 

You can assign default values if the array doesn’t have enough elements:

```js
const [a = 1, b = 2, c = 3] = [10];
console.log(a); // 10
console.log(b); // 2
console.log(c); // 3
```


### 🟢 Swapping Variables: 

Array destructuring makes swapping values easy:

```js
let x = 5;
let y = 10;

[x, y] = [y, x];

console.log(x); // 10
console.log(y); // 5

```

### 🟢 Using with Functions

If a function returns an array, you can destructure the result directly:

```js
function getValues() {
  return [1, 2];
}

const [a, b] = getValues();
console.log(a, b); // 1 2
```

</details>
---


<details>
<summary><b>Q18. Difference between <code>spread operator</code><code>concat</code> </b></summary>


### 🟢 Spread Operator (`...`)

The **spread operator** expands (or “spreads out”) the elements of an array (or iterable) into another array or function call. Used for merging, copying, or passing elements.

### 🟢 Syntax: 

```js
const newArray = [...array1, ...array2];
```

### 🟢 Example: 

```js
const arr1 = [1, 2];
const arr2 = [3, 4];
const combined = [...arr1, ...arr2];
console.log(combined); // [1, 2, 3, 4]

```

### 🟢 Features: 

- Can combine arrays or clone them easily.
- Can also be used inside objects and function calls.
- Creates a **shallow copy**.

### 🟢 `concat()` Method

The `concat()` method merges two or more arrays and returns a **new array** without changing the originals.

### 🟢 Syntax: 

```js
const newArray = array1.concat(array2);

```

### 🟢 Example: 

```js
const arr1 = [1, 2];
const arr2 = [3, 4];
const combined = arr1.concat(arr2);
console.log(combined); // [1, 2, 3, 4]

```

### 🟢 Features: 

- Specifically made for joining arrays.
- Can merge multiple arrays or values:

```js
const result = arr1.concat(arr2, [5, 6], 7);
console.log(result); // [1, 2, 3, 4, 5, 6, 7]
```

### 🟢 Example Comparison: 

```js
const a = [1, 2];
const b = [3, 4];

// Using spread
const spreadResult = [...a, ...b, 5]; // [1, 2, 3, 4, 5]

// Using concat
const concatResult = a.concat(b, 5);  // [1, 2, 3, 4, 5]
```

👉 Both work similarly for arrays, but the spread operator is more flexible and modern — it’s preferred in modern JavaScript.

</details>
---

<details>
<summary><b>Q19. How do you remove duplicates from an array? </b></summary>


### 🟢 Using `Set` (Most Common & Easiest Way)

The `Set` object automatically stores **unique values** — duplicates are ignored.

### 🟢 Example: 

```js
const numbers = [1, 2, 2, 3, 4, 4, 5];
const unique = [...new Set(numbers)];
console.log(unique);
//  [1, 2, 3, 4, 5]
```

### 🟢 Features: 

- Very short and fast.
- Works for strings, numbers, booleans, etc.

### 🟢 Using `filter()` + `indexOf()`

### 🟢 Example: 

```js
const arr = [1, 2, 2, 3, 4, 4, 5];
const unique = arr.filter((value, index, self) => self.indexOf(value) === index);
console.log(unique);
//  [1, 2, 3, 4, 5]
```
**Explanation:**

- `indexOf(value)` gives the first index of that value.
- If the current index matches that, it means it’s the **first occurrence**, so it’s kept.

### 🟢 Using `reduce()` + `includes()`

### 🟢 Example: 

```js
const arr = [1, 2, 2, 3, 4, 4, 5];
const unique = arr.reduce((acc, curr) => {
  if (!acc.includes(curr)) acc.push(curr);
  return acc;
}, []);
console.log(unique);
//  [1, 2, 3, 4, 5]
```
**Explanation:**

- Good if you want more control over how duplicates are handled.

### 🟢 Removing Duplicates from Array of Objects

If you have **objects**, `Set` won’t work directly (because objects are compared by reference).

You can use `filter()` and `findIndex()` or `Map()`.


### 🟢 Example: 

```js
const users = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
  { id: 1, name: "Alice" }
];

const uniqueUsers = users.filter(
  (user, index, self) => index === self.findIndex(u => u.id === user.id)
);

console.log(uniqueUsers);
//  [{ id: 1, name: "Alice" }, { id: 2, name: "Bob" }]

```

</details>
---

## 🔵 Strings & Numbers

<details>
<summary><b>Q1. What are <code>template literals</code>? </b></summary>


### 🔵 Definition

**Template literals** in JavaScript are a special way to create strings — they make it easier to include variables, expressions, and even multi-line text.
They are enclosed by `backticks (` `)`, not `single (' ')` or `double (" ")` quotes.

### Syntax

```js
let name = "Suborno";
let message = `Hello, ${name}!`;
console.log(message); // Output: Hello, Suborno!

```
Here, `${name}` is a **placeholder** — JavaScript replaces it with the value of the variable.

### 🔵 Multi-line Strings

You can easily create strings that span multiple lines without using `\n`:

```js
let poem = `Roses are red,
Violets are blue,
JavaScript is fun,
And so are you!`;
console.log(poem);

```

### 🔵 Expression Interpolation

You can include not just variables, but **any expression** inside `${}`:

```js
let a = 10;
let b = 5;
console.log(`The sum is ${a + b}.`); // Output: The sum is 15.

```

### 🔵 Tagged Templates (Advanced)

You can use a **function** to process template literals — this is called a *tagged template*.

```js
function highlight(strings, value) {
  return `${strings[0]}***${value.toUpperCase()}***${strings[1]}`;
}

let result = highlight`Hello, ${"world"}!`;
console.log(result); // Output: Hello, ***WORLD***!

```

</details>
---

<details>
<summary><b>Q2. Difference between <code>single quotes</code>, <code>double quotes</code>, and <code>backticks</code>. </b></summary>


### 🔵 Single Quotes (' ')

- Used to define **simple string literals**.
- Do not support variable interpolation.
- Do not support multi-line strings (without escape characters).

```js
let name = 'Suborno';
let greeting = 'Hello, ' + name + '!'; // Must use + for concatenation

```

### 🔵 Double Quotes (" ")

- Work almost the same as single quotes.
- The only difference is **stylistic** — you can use them interchangeably.
- Helpful when your string contains a single quote (`'`) that you don’t want to escape.

```js
let message = "It's a nice day!";

```

### 🔵 Backticks `(``)` — Template Literals

- Introduced in **ES6 (ES2015)**.
- Allow **string interpolation with** `${}`.
- Support **multi-line strings** easily.
- Can include **expressions**, not just variables.

```js
let name = "Suborno";
let age = 20;

let info = `My name is ${name}, and I am ${age} years old.`;
console.log(info);

// Multi-line example
let poem = `Roses are red,
Violets are blue,
JavaScript is awesome,
And so are you!`;
```
</details>
---

<details>
<summary><b>Q3. Difference between <code>slice</code>, <code>substr</code>, and <code>substring</code>. </b></summary>


### 🔵 `slice(start, end)`

Extracts part of a string from `start` to `end` (not including `end`). Works with negative indexes (counts from the end).

```js
let text = "JavaScript";

console.log(text.slice(0, 4));   // "Java"
console.log(text.slice(4, 10));  // "Script"
console.log(text.slice(-6, -3)); // "Scr"

```
**Use case:** When you want to extract by position range (and need negative index support).

### 🔵 `substring(start, end)`

Extracts part of a string from `start` to `end` (not including `end`). but **does NOT support negative indexes**.

❗If `start` > `end`, it **swaps** the two values.

```js
let text = "JavaScript";

console.log(text.substring(0, 4));  // "Java"
console.log(text.substring(4, 0));  // "Java" (swapped)
console.log(text.substring(4, 10)); // "Script"
console.log(text.substring(-3, 4)); // "Java" (negative ignored)

```
**Use case:** When you want a simple, safe extraction without worrying about negative indexes.

### 🔵 `substr(start, length)`

Extracts a substring starting from `start` and taking `length` characters. Supports **negative** `start` (counts from the end). 

🚫 **But note:** `substr()` is **deprecated** (not recommended for new code).

```js
let text = "JavaScript";

console.log(text.substr(0, 4));   // "Java"
console.log(text.substr(4, 6));   // "Script"
console.log(text.substr(-6, 3));  // "Scr"

```
**Use case:** When you want to extract a specific **number of characters**, but better use `slice()` instead (since `substr()` is deprecated).

👉 **Use `slice()` in modern JavaScript — it’s the most flexible and predictable.**

</details>
---

<details>
<summary><b>Q4. What is string immutability in JavaScript?</b></summary>


### 🔵 Definition

In JavaScript, **strings are immutable**, meaning **once a string is created, it cannot be changed.**
You can’t modify a character inside a string — you can only create a new string.

```js
let str = "Hello";

str[0] = "Y";    //  This does nothing
console.log(str); // "Hello"
```
Even though it looks like you’re changing the first character, the original string remains the same — it’s **unchangeable**.

### 🔵 The Correct Way — Create a New String

To “change” a string, you must **build a new one**:

```js
let str = "Hello";
str = "Y" + str.slice(1);

console.log(str); //  "Yello"

```
Here, we didn’t edit the original string — we **constructed a new string** and reassigned it to the same variable.

### Another Example:
```js
let word = "cat";
let newWord = word.replace("c", "b");

console.log(newWord); // "bat"
console.log(word);    // "cat" (unchanged)
```
Even `replace()` or `toUpperCase()` **return new strings** instead of changing the original.

</details>
---

<details>
<summary><b>Q5. Difference between <code>parseInt</code> and <code>Number()</code>.</b></summary>


### 🔵 `parseInt()`

**Converts a string to an integer (whole number).**

It: 
- **Parses** the string **until it hits a non-numeric character.**
- Can handle **spaces** or **extra characters** (up to the first invalid one).
- Can take an **optional radix** (base) like binary (2), decimal (10), or hex (16).

```js
console.log(parseInt("42"));        // 42
console.log(parseInt("42px"));      // 42 ; stops at 'p'
console.log(parseInt("  100abc"));  // 100
console.log(parseInt("10", 2));     // 2  (binary 10 = 2)
console.log(parseInt("3.14"));      // 3  (decimal part ignored)
console.log(parseInt("abc123")); // NaN

```

### 🔵 `Number()`

**Converts the entire string (or value) into a number — integer or float.**

It: 
- Converts the **whole string**, not just part of it.
- Returns **NaN** if the string isn’t a valid number.
- Converts **booleans, null**, and other types too.

```js
console.log(Number("42"));      // 42
console.log(Number("3.14"));    // 3.14
console.log(Number("42px"));    // NaN 
console.log(Number("   42 "));  // 42 (trims spaces)
console.log(Number(true));      // 1
console.log(Number(false));     // 0
console.log(Number(null));      // 0
```
</details>
---

<details>
<summary><b>Q6. How does <code>toFixed()</code> work?</b></summary>


### 🔵 Definition

`number.toFixed(digits)`
- Returns a **string** representing the number with exactly `digits` digits **after the decimal point**.
- **Rounds** the number if necessary.

```js
let num = 3.14159;

console.log(num.toFixed(2)); // "3.14"
console.log(num.toFixed(4)); // "3.1416"
console.log(num.toFixed(0)); // "3"
```
👉 Notice: the result is a **string**, not a number.

### 🔵 Rounding Behavior

`toFixed()` **rounds** the number using standard rounding rules (≥ 0.5 rounds up):

```js
let n = 2.678;
console.log(n.toFixed(2)); // "2.68"
```
</details>
---

<details>
<summary><b>Q7.  Difference between <code>Math.floor()</code>, <code>Math.ceil()</code>, and <code>Math.round()</code>.</b></summary>


### 🔵 Here’s the difference between `Math.floor()`, `Math.ceil()`, and `Math.round()` in JavaScript

|     Methods       |    Description    |    Example Input      |    Output     |   Explanation      |
|----------------|----------------|----------------|----------------|----------------|
|`Math.floor()`   | Rounds **down** to the nearest integer  | `Math.floor(4.9)`  |  `4`    | Always rounds **down** (toward −∞).  |
|  |  | `Math.floor(-4.9)`  |  `-5`    | For negatives, it goes **more negative**.  |
|`Math.ceil()`   | Rounds **up** to the nearest integer  | `Math.ceil(4.1)`  |  `5`    | Always rounds **up** (toward +∞).  |
|  |  | `Math.ceil(-4.1)`  |  `-4`    | For negatives, it goes **less negative**.  |
|`Math.round()`   | Rounds to the **nearest integer**  | `Math.round(4.4)`  |  `4`    | 0.5 or higher → rounds up. |
|  |  | `Math.round(4.5)`  |  `5`    | 0.5 rounds **up** to next integer.  |
|  |  | `Math.round(-4.5)`  |  `-4`    | Negative 0.5 rounds **up toward 0**.  |

</details>
---

## 🟣 DOM Manipulation

<details>
<summary><b>Q1. What is the DOM in JavaScript?</b></summary>


### 🟣 Definition

The **DOM** in JavaScript stands for **Document Object Model**. It’s a **programming interface** that allows JavaScript (and other languages) to **interact with and manipulate** the content, structure, and style of a web page. 

When a web page loads, the browser takes the HTML code and **creates a tree-like structure** called the **DOM tree**.
Each HTML element (like `<div>`, `<p>`, `<h1>`, etc.) becomes an **object** (or “node”) in this tree.
JavaScript can then **access, modify, add, or remove** these nodes dynamically — without reloading the page. 

👉 The document object represents the entire web page

🧠 **Key Concepts:**

- `document` → The root object of the DOM (represents the whole page).
- **Elements (Nodes)** → Every HTML tag becomes a node in the DOM tree.
- **DOM Manipulation** → You can change text, styles, or even structure using JavaScript.
- **Event Handling** → The DOM lets you respond to user actions (like clicks, typing, etc.).

</details>
---

<details>
<summary><b>Q2. Difference between <code>document.getElementById</code> and <code>querySelector</code>.</b></summary>


### 🟣 Using `getElementById()`:

```html
<h1 id="title">Hello!</h1>
<script>
  const heading = document.getElementById("title");
  console.log(heading.textContent); // "Hello!"
</script>
```
Works **only** for elements with an `id` attribute.

### 🟣 Using `querySelector()`:

```html
<h1 class="title">Welcome!</h1>
<p id="message">Hi there!</p>

<script>
  // Select by class
  const heading = document.querySelector(".title");
  
  // Select by ID
  const message = document.querySelector("#message");
  
  // Select by tag
  const paragraph = document.querySelector("p");
</script>

```
Works with **any** valid CSS selector (ID, class, tag, attribute, etc.).
But returns only the first match if there are multiple elements.

### 🟣 When to Use Which

|  Use Case   |  Recommended Method  |
|-------------|----------------------|
| You know the element has a unique ID   |  `getElementById()`   |
| You want to select by class, tag, or attribute   |  `querySelector()`   |
| You want to select multiple elements   |  `querySelectorAll()` (returns a NodeList)  |


</details>
---

<details>
<summary><b>Q3. Difference between <code>innerHTML</code> , <code>innerText</code> and <code>textContent</code>.</b></summary>


|Property|Returns|Includes HTML Tags?|Affects Hidden Text?|Faster?|Common Use| 
|--------|-------|----------------|--------------------|-----------|---------|
|`innerHTML`|HTML code (tags + text)| Yes|Includes hidden elements| Slower (parses HTML)  | Insert or read HTML|
|`innerText`|Visible text (only what’s displayed)| No |Ignores hidden text| Medium  | Read/write visible text |
|`textContent`|All text (including hidden)| No |Includes hidden text| Fastest  | Read/write plain text |

### 🟣 Example HTML

```html
<div id="demo">
  <p>Hello <b>World</b>!</p>
  <p style="display: none;">Hidden text</p>
</div>

```

### 🟣 Examples in JavaScript

**`innerHTML`**
```js
let htmlValue = document.getElementById("demo").innerHTML;
console.log(htmlValue);

```
**Output**
```html
<p>Hello <b>World</b>!</p>
<p style="display: none;">Hidden text</p>
```
Returns **HTML markup** (including tags).

**`innerText`**
```js
let textValue = document.getElementById("demo").innerText;
console.log(textValue);

```
**Output**
```html
Hello World!

```
Does **not include hidden text** (from `display: none`). Represents what the user **actually sees on the page.**

**`textContent`**
```js
let contentValue = document.getElementById("demo").textContent;
console.log(contentValue);
```
**Output**
```html
Hello World!
Hidden text
```
- Includes all text, even hidden ones.
- Does not process HTML tags.
- Fastest because it doesn’t compute styles or layout.

### 🟣 When to Use Each

|Task|Recommended Property|
|----------|------------------|
|Get or set HTML (including tags)| `innerHTML`|
|Need formatted HTML content| `innerHTML`|
|Get visible text (what user sees)| `innerText`|
|Get all text (visible + hidden)| `textContent`|
|Need performance and no formatting| `textContent`|

</details>
---


<details>
<summary><b>Q4. How do you create elements dynamically in JavaScript?</b></summary>

### 🟣 Basic Steps to Create Elements Dynamically

|Step|Description|Example|
|--------|-------|----------------|
|1|Create a new element| `document.createElement("p")`|
|2|Add content (text or HTML)| `element.textContent = "Hello!"` |
|3|Set attributes or styles| `element.id = "greeting"` |
|4|Attach it to the DOM| `document.body.appendChild(element)` |

### 🟣 Example 1: Create and Add a Paragraph

```js
// 1. Create a new <p> element
let para = document.createElement("p");

// 2. Add text inside the paragraph
para.textContent = "This paragraph was added dynamically!";

// 3. Add a class for styling
para.className = "dynamic-text";

// 4. Add it to the page (for example, inside the <body>)
document.body.appendChild(para);

```

**Result**

A new paragraph appears on the page with the text
  “This paragraph was added dynamically!”

### 🟣 Example 2: Create Nested Elements

```js
// Create a <div> container
let div = document.createElement("div");
div.className = "card";

// Create a <h2> element
let title = document.createElement("h2");
title.textContent = "Dynamic Title";

// Create a <p> element
let description = document.createElement("p");
description.textContent = "This content was created using JavaScript.";

// Add <h2> and <p> inside the <div>
div.appendChild(title);
div.appendChild(description);

// Finally, add the <div> to the body
document.body.appendChild(div);

```

**Result**
```html
<div class="card">
  <h2>Dynamic Title</h2>
  <p>This content was created using JavaScript.</p>
</div>
```


### 🟣 Example 3: Add Elements to a Specific Container

```html
<div id="container"></div>
```
```js
let container = document.getElementById("container");
let button = document.createElement("button");
button.textContent = "Click Me!";
container.appendChild(button);
```
The button will appear **inside the** `#container` **div**, not the body.
</details>
---

<details>
<summary><b>Q5. What is the difference between <code>append</code>, <code>appendChild</code>, and <code>insertBefore</code>?</b></summary>


|Method|Used On|Can Add Multiple Nodes?|Can Add Text?|Returns|Browser Support|
|--------|-------|----------------|----------|-------------|------------------|
|`append()`|Parent Node| Yes |Yes (text strings)|`undefined`|Modern browsers (newer)|
|`appendChild()`|Parent Node| No (only one node) |No (only Node objects)|Returns appended node|All browsers|
|`insertBefore()`|Parent Node| No (only one node) |No (only Node objects)|Returns inserted node|All browsers|


### 🟣 `append()`

- Adds **one or more nodes or strings** to the **end** of a parent element.
- Can insert **text directly** without creating a text node.
- **Does not return** anything.
- Modern and more flexible.

```js
const div = document.createElement("div");
div.append("Hello ", document.createElement("span"), " World!");
```
**Output:** `<div>Hello <span></span> World!</div>`

### 🟣 `appendChild()`

- Adds **a single node** to the **end** of a parent element.
- Only accepts **Node objects**, not text strings.
- **Returns** the appended node.
- Works in all browsers (including old ones).

```js
const div = document.createElement("div");
const span = document.createElement("span");
div.appendChild(span);
```
**Output:** `<div><span></span></div>`



### 🟣 `insertBefore()`

- Inserts a node **before** a specified existing child node.
- Only accepts **Node objects**, not text.
- **Returns** the inserted node.
- Useful for placing an element **at a specific position**, not just the end.

```js
const list = document.querySelector("ul");
const newItem = document.createElement("li");
newItem.textContent = "New Item";
const firstItem = list.firstElementChild;
list.insertBefore(newItem, firstItem);
```
**Output:** Inserts `<li>New Item</li>` before the first `<li>`.

</details>
---


<details>
<summary><b>Q6. What is the difference between <code>removeChild</code> and <code>remove</code>?</b></summary>


|Feature|`removeChild()`|`remove()`|
|--------|-------|----------------|
|Used On|Parent Node| The element itself|
|What It Removes|Removes a specific child node from a parent| Removes the element itself from the DOM|
|Requires Parent Reference?|Yes — you must call it from the parent| No — called directly on the element|
|Returns|Returns the removed child node| Returns nothing (`undefined`)|
|Browser Support|All browsers (including old ones)| Modern browsers (IE not supported)|
|Example|`parent.removeChild(child)`| `element.remove()`|

### 🟣 `removeChild()`

- Must be called **on the parent** of the node you want to remove.
- You need a **reference to both the parent and the child.**
- **Returns** the removed child node (you can store or reuse it).

```js
const parent = document.getElementById("container");
const child = document.getElementById("item");

parent.removeChild(child);

```
**Output:** Removes `<div id="item">` from inside `<div id="container">`.

### 🟣 `remove()`

- Called **directly on the element itself** — no need to reference the parent.
- Simpler syntax and cleaner code.
- Does **not return anything**.


```js
const item = document.getElementById("item");
item.remove();

```
**Output:** Removes `<div id="item">` from the DOM.

</details>
---

<details>
<summary><b>Q7. What are data attributes in HTML/JS (data-*)? </b></summary>

**Data attributes** (written as `data-*`) in **HTML** are custom attributes that store extra information (metadata) directly on HTML elements.

They are especially useful when you want to associate some data with an element — data that **doesn’t have a built-in HTML attribute** — and you want to **access it later in JavaScript**.

### 🟣 Syntax

```html
<div id="user" data-id="101" data-name="Alice" data-role="admin"></div>
```
Here, 

- `data-id`, `data-name`, and `data-role` are **data attributes**.
- The prefix `data-` is **required**, but you can name the rest as you wish (`data-*`).


**Output:** Removes `<div id="item">` from inside `<div id="container">`.

### 🟣 Why Use Data Attributes?

They are:
- **Customizable:** You can define any name after `data-`.
- **HTML5 standard:** They are valid and supported in all modern browsers.
- **Useful for JS interaction:** JavaScript can easily access, modify, or use these values without needing global variables or hardcoded data.

### 🟣 Accessing Data Attributes in JavaScript

**1. Using the `.dataset` property**

```js
const user = document.getElementById('user');

console.log(user.dataset.id);     // "101"
console.log(user.dataset.name);   // "Alice"
console.log(user.dataset.role);   // "admin"
```
**Note:**

- The part **after** `data-` becomes a **camelCase property** in JavaScript.
    - Example: `data-user-id` → `dataset.userId`
 
**2. Setting / Changing Data Attributes**

```js
user.dataset.role = "editor"; // updates the attribute
console.log(user.dataset.role); // "editor"

```
You can also modify it through HTML:

```js
user.setAttribute('data-role', 'viewer');
```
 
</details>
---

<details>
<summary><b>Q8. How does classList work? </b></summary>

The `classList` property in JavaScript is a **convenient way to work with the classes of an HTML element**. It allows you to **read, add, remove, toggle, or check** CSS classes without manipulating the `className` string manually.

### 🟣 Accessing `classList`

```html
<div id="myDiv" class="box highlight"></div>
```

```js
const div = document.getElementById('myDiv');
console.log(div.classList); 
// DOMTokenList ["box", "highlight"]
```
Here, 

- `classList` returns a **DOMTokenList**, which acts like an array of class names.
- You can use methods on it to manipulate classes easily.

### 🟣 Methods of `classList`

|   Method   |   Description     |   Example   |
|-------------|-------------------|------------|
|`add(className1, …)`  | Adds one or more classes   | `div.classList.add('active')`|
|`remove(className1, …)`  | Removes one or more classes   | `div.classList.remove('highlight')`|
|`toggle(className, [force])`  | Toggles a class: adds if missing, removes if present. Optional force boolean forces add/remove   | `div.classList.toggle('active')`|
|`contains(className)`  | Checks if element has the class  | `div.classList.contains('box') // true`|
|`replace(oldClass, newClass)`  | Replaces one class with another  | `div.classList.replace('box', 'container')`|

They are:
- **Customizable:** You can define any name after `data-`.
- **HTML5 standard:** They are valid and supported in all modern browsers.
- **Useful for JS interaction:** JavaScript can easily access, modify, or use these values without needing global variables or hardcoded data.

### 🟣 Examples

```html
<div id="myDiv" class="box highlight"></div>
```

**1. Adding a class**

```js
div.classList.add('visible');
console.log(div.classList); // ["box", "highlight", "visible"]

```

**2. Removing a class**

```js
div.classList.remove('highlight');
console.log(div.classList); // ["box", "visible"]
```

**3. Toggling a class**

```js
div.classList.toggle('active'); // Adds 'active' if not present
div.classList.toggle('active'); // Removes 'active' if present

```

**4. Checking a class**

```js
if (div.classList.contains('box')) {
  console.log('Box class exists!');
}

```

**4. Replacing a class**

```js
div.classList.replace('box', 'container');
console.log(div.classList); // ["container", "visible"]
```

 ### 🟣 Advantages over `className`
 
- You **don’t need to worry about spaces** between class names.
- Easier to **add/remove multiple classes** dynamically.
- Cleaner and more **readable** code.
</details>
---


<details>
<summary><b>Q9. Difference between <code>setAttribute</code> and <code>direct property</code> assignment. </b></summary>

|   Aspect   |   `setAttribute(name, value)`     |   Direct Property Assignment   |
|-------------|-------------------|------------|
|Description  | A **DOM method** used to set the value of any **HTML attribute** on an element.   | Assigns a value directly to the **DOM element’s property** in JavaScript (e.g., `element.id = "value"`).|
|Scope  | Updates the **HTML attribute** but may not always change the corresponding DOM property.  | Updates the **DOM property**, but not always the HTML attribute.|
|Example  | `element.setAttribute("value", "Hello")`   | `element.value = "Hello"`|
|When it affects the UI  | Depends on the attribute — not all attributes are reflected immediately in the rendered UI.  | Usually updates the **live state** of the element (e.g., what’s displayed in a form input).|
|Type of Value  | Always treats the value as a **string**.  | Keeps the **data type** (string, number, boolean, etc.).|
|Can set custom attributes?  | Yes, you can set custom attributes like `data-user="John"`.  | No, unless that property exists on the element object.|
|Use Case  | When you need to manipulate **HTML attributes** directly (like `data-*`, `aria-*`, or for serialization).  | When you need to manipulate the **live state** or **behavior** of the element.|
|When to use  | Manipulating **HTML markup or custom attributes**. Examples: `element.setAttribute('data-id', 123)` | Manipulating **element state or behavior**. Example: `element.checked = true or element.value = "text"`|

### 🟣 Examples

```html
<input id="myInput" value="initial">
```

```js
const input = document.getElementById("myInput");

// Using setAttribute
input.setAttribute("value", "new"); 
console.log(input.value); //  "initial" (property not updated yet)
console.log(input.getAttribute("value")); //  "new"

// Using property assignment
input.value = "updated"; 
console.log(input.value); //  "updated"
console.log(input.getAttribute("value")); //  "new" (attribute didn’t change)

```

**Explanation**

- `setAttribute("value", ...)` changes the **HTML attribute**, not the current UI value.
- `input.value = ...` changes the **current input field’s value** (what the user sees).
</details>
---

## 🟤 Events

<details>
<summary><b>Q1. What is event delegation in JavaScript? </b></summary>

**Event Delegation** in JavaScript is a technique that allows you to handle events more efficiently by using **event bubbling**.

Instead of adding event listeners to **multiple child elements**, you attach a **single event listener** to a **common parent element**.

That parent then listens for events that bubble up from its children and handles them appropriately.

### 🟤 Examples

```html
<ul id="menu">
  <li>Home</li>
  <li>About</li>
  <li>Contact</li>
</ul>

<script>
  const menu = document.getElementById('menu');

  // Event delegation: attach one listener to the parent <ul>
  menu.addEventListener('click', function(event) {
    if (event.target.tagName === 'LI') {
      console.log(`You clicked on ${event.target.textContent}`);
    }
  });
</script>

```

**Explanation**

- The `<ul>` has **one** click listener.
- When you click a `<li>`, the event **bubbles up** to the `<ul>`.
- The `<ul>`’s listener checks which element triggered the event using `event.target`.
- You don’t need to attach a listener to every `<li>` individually.

### 🟤 How It Works

Event delegation relies on **event bubbling**:
  1. An event starts from the target element (e.g., `<li>`).
  2. It bubbles up through its ancestors (e.g., `<ul>`, `<body>`, `document`).
  3. A listener on any ancestor can catch it.

### 🟤 Advantages

  1. Fewer event listeners → better **performance**.
  2. Works for **dynamically added elements**.
  3. Easier **code management**.

</details>
---


<details>
<summary><b>Q2. Difference between <code>onclick</code> and <code>addEventListener</code>. </b></summary>

|Feature|`onclick`|`addEventListener()`|
|-------|----------|--------------------|
|Type|Property-based event handler|Method to attach event listeners|
|Usage|`element.onclick = function() { ... }`|`element.addEventListener('click', function() { ... })`|
|Multiple Handlers|Only one handler can exist — a new one overwrites the old one|You can attach multiple handlers for the same event|
|Event Removal|Must overwrite with `null`|Can remove using `removeEventListener()`|
|Supports Multiple Event Types|No, only one event per property|Yes, can handle any event type dynamically|
|Event Phases|Works only in the **bubbling phase**|Can specify **capturing** or **bubbling** phase|
|Modern Use|Older, less flexible|Preferred modern approach|

### 🟤 Example 1 — `onclick`

```js
const btn = document.querySelector('button');

btn.onclick = function() {
  console.log('Button clicked!');
};

// This will overwrite the previous one
btn.onclick = function() {
  console.log('Another handler');
};
```
Output: Only “**Another handler**” appears. (Second handler replaced the first one.)


### 🟤 Example 2 — `addEventListener()`

```js
const btn = document.querySelector('button');

btn.addEventListener('click', function() {
  console.log('First handler');
});

btn.addEventListener('click', function() {
  console.log('Second handler');
});

```
Output: 

```sql
First handler
Second handler
```
(Both handlers run - no overwriting)
</details>
---

<details>
<summary><b>Q3. What is <code>event propagation</code>? </b></summary>

Event propagation in JavaScript is **the process by which an event moves through the DOM tree** when it occurs on an element. Basically, when you trigger an event (like a click), it doesn’t just affect the element you clicked — it can also trigger event handlers on its ancestors (parent elements) or descendants, depending on the phase.

There are **two main phases** of event propagation:

### 🟤 Capturing Phase (Event Capturing)

- The event **starts from the top of the DOM tree** (`document`) and travels down to the target element.
- Rarely used directly, but you can attach listeners for this phase by passing `true` as the third argument in `addEventListener`.

```js
parent.addEventListener("click", () => {
  console.log("Parent clicked (capturing)");
}, true); // true → capturing phase

```

### 🟤 Target Phase

- The event **reaches the target element** (the element that was actually clicked).
- Event listeners on the target element execute here (regardless of capturing or bubbling).

```js
child.addEventListener("click", () => {
  console.log("Child clicked (target)");
});

```

### 🟤 Bubbling Phase (Event Bubbling)

- After reaching the target, the event **bubbles back up** the DOM tree from the target to the root.
- Most event listeners by default are triggered in this phase.

```js
parent.addEventListener("click", () => {
  console.log("Parent clicked (bubbling)");
});
```

### 🟤 Example

```js
<div id="parent">
  <button id="child">Click Me</button>
</div>

<script>
  const parent = document.getElementById("parent");
  const child = document.getElementById("child");

  parent.addEventListener("click", () => console.log("Parent clicked (bubbling)"));
  child.addEventListener("click", () => console.log("Child clicked (target)"));
</script>

```

**Clicking the button outputs:**
```java
Child clicked (target)
Parent clicked (bubbling)
```
</details>
---


<details>
<summary><b>Q4. What are <code>event bubbling</code> and <code>capturing</code> in js? </b></summary>

In **JavaScript, event bubbling** and **event capturing** are **two ways that events propagate (travel)** through the **DOM tree** when an event occurs on an element that is nested inside other elements.

### 🟤 Event Propagation Overview

When an event (like a click) happens on an element, it **doesn’t just affect that element** — it moves through the DOM in three phases:

| Phase | Description | Example order (for nested elements `<div><p><button></button></p></div>`)|
| 1. Capturing phase | Event moves **from the root → down to the target** | `document → html → body → div → p → button`|
| 2. Target phase | Event **reaches the target element** | `button`|
| 3. Bubbling phase | Event moves **back up from the target → root** | `button → p → div → body → html → document`|


### 🟤 Event Capturing (Trickling Down)

- The event is **first captured** by the outermost element and **propagates downward** to the target.
- Rarely used, but can be enabled by passing `true` as the third argument to `addEventListener`.
```js
div.addEventListener('click', () => {
  console.log('Div (capturing)');
}, true); // true = capturing phase

```
Output

```css
Div (capturing)
Button (target)
```

### 🟤 Event Bubbling (Default Behavior)

- After the event reaches the target, it **bubbles up** to its ancestors.
- This is the **default phase** (if you don’t pass `true`).

```js
div.addEventListener('click', () => {
  console.log('Div (bubbling)');
});
button.addEventListener('click', () => {
  console.log('Button');
});

```
Output

```css
Button
Div (bubbling)

```
</details>
---


<details>
<summary><b>Q5. How do you stop <code>event propagation</code>? </b></summary>

In JavaScript, you can stop **event propagation** using the `event.stopPropagation()` or `event.stopImmediatePropagation()` methods.

### 🟤 Event Propagation Overview

This **stops the event from bubbling or capturing** any further up or down the DOM tree.

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>

<script>
  document.getElementById("parent").addEventListener("click", () => {
    console.log("Parent clicked");
  });

  document.getElementById("child").addEventListener("click", (event) => {
    console.log("Child clicked");
    event.stopPropagation(); // stops event from reaching parent
  });
</script>
```
**Output when clicking the button:**

```html
Child clicked
```
The parent’s click event won’t fire because propagation was stopped.

### 🟤 `event.stopImmediatePropagation()`

This not only stops propagation but also **prevents other listeners on the same element** from running.

```js
button.addEventListener("click", (e) => {
  console.log("First listener");
  e.stopImmediatePropagation();
});

button.addEventListener("click", () => {
  console.log("Second listener");
});

```
Output when clicked:

```css
First listener
```
</details>
---

<details>
<summary><b>Q6. Difference between <code>preventDefault()</code> and <code>stopPropagation()</code>. </b></summary>

| Feature | `preventDefault()`  | `stopPropagation()`|
|---------|----------------------|--------------------|
|Purpose|Prevents the default browser behavior of an element|Stops the event from moving (propagating) through the DOM tree|
|Affects|Only the element’s default action|Event flow to parent/ancestor elements or other listeners|
|Example Use Case|Prevent a form from submitting, prevent a link from navigating|Stop a click on a child from triggering parent’s click handler|
|Does It Stop Event Listeners?|No, the event still triggers other listeners|Yes, it stops the event from reaching other listeners (or other elements)|
|Method Called On|`event.preventDefault()`|`event.stopPropagation()`|

### 🟤 Example 1: `preventDefault()`

```html
<a href="https://google.com" id="link">Go to Google</a>

<script>
document.getElementById("link").addEventListener("click", function(event) {
  event.preventDefault(); // stops the browser from navigating
  console.log("Link clicked but default prevented!");
});
</script>

```
**Clicking the link:** logs the message but **does not go to Google**.

### 🟤 Example 2: `stopPropagation()`

```html
<div id="parent">
  <button id="child">Click Me</button>
</div>

<script>
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent clicked");
});

document.getElementById("child").addEventListener("click", (event) => {
  event.stopPropagation(); // stops event from bubbling to parent
  console.log("Child clicked");
});
</script>

```
**Clicking the button:** logs only `"Child clicked"`. The parent’s click handler **does not run**.

</details>
---

<details>
<summary><b>Q7. What is <code>passive event listener</code> ? </b></summary>

In **JavaScript**, a **passive event listener** is a special kind of event listener that **never calls** `preventDefault()` on the event.

It is mainly used to **improve performance**, especially for **scrolling and touch events**.

### 🟤 Syntax

```js
element.addEventListener('scroll', handler, { passive: true });

```
Here, the third argument is an **options object**, and `{ passive: true }` marks the listener as passive.

### 🟤 Why Passive Listeners Exist

Normally, when you attach a scroll or touch event listener (like `touchstart`, `touchmove`, or `wheel`), the browser has to wait to see if your code calls `event.preventDefault()` before it can proceed with scrolling.
This waiting can `delay rendering` and make scrolling feel laggy on mobile devices.

If you mark the listener as passive, it tells the browser:

    “Don’t worry, I will not call `preventDefault()` — go ahead and scroll immediately.”

So the browser can start scrolling right away → resulting in smoother performance.

### 🟤 Example

```js
document.addEventListener('touchmove', (event) => {
  console.log('Touch moving...');
}, { passive: true });
```
This will allow the browser to scroll immediately when the user moves their finger, because the listener won’t block the scroll.

If you try to call `preventDefault()` inside a **passive listener**, the browser will **ignore it** and show a **warning in the console**:

```js
document.addEventListener('touchmove', (e) => {
  e.preventDefault(); // ❌ Ignored if passive: true
}, { passive: true });
```

</details>
---

<details>
<summary><b>Q8. Difference between <code>input</code> and <code>change</code> events.</b></summary>

|Feature|`input` Event | `change` Event|
|--------|--------------|---------------|
|When it fires| Fires **immediately** when the value of an input changes (on every keystroke)|Fires **when the element loses focus** after its value is changed|
|Applies to| Mostly for text-based inputs (`<input>`, `<textarea>`, etc.)|Works with all form elements (`<input>`, `<select>`, `<textarea>`, etc.)|
|Frequency| Fires continuously as user types or modifies value |Fires **once** when user finishes editing|
|Example use| Live search, character counters, instant validation |Submitting or reacting only after final value chosen|
|Event bubbling| Bubbles |Bubbles|


### 🟤 Example

**Using `input`**
```html
<input type="text" id="username" placeholder="Type something...">

<script>
document.getElementById('username').addEventListener('input', () => {
  console.log('Input event fired!');
});
</script>
```
Logs message **every time** you type or delete a character.

**Using `change`**
```html
<input type="text" id="username" placeholder="Type something...">

<script>
document.getElementById('username').addEventListener('change', () => {
  console.log('Change event fired!');
});
</script>
```
Logs message **only when you leave the field** (blur) after changing its value.

`input` reacts to every modification in real time, while `change` reacts only once when the user finalizes the change (usually after focus leaves the element).
</details>
---

<details>
<summary><b>Q9. Difference between <code>throttling</code> and <code>debouncing</code>. </b></summary>

|Concept|Description |
|--------|--------------|
|Debouncing| Ensures that a function runs **only after** a certain time has passed **since the last event**.|
|Throttling| Ensures that a function runs **at most once every fixed interval**, no matter how many times the event fires.|

### 🟤 Real-world Example

Imagine you’re typing in a search box that makes an API call on every keystroke:

- **Without control**: The function runs for every letter → too many calls

- **Debouncing**: Waits until you **stop typing for a bit**, then runs the function once 

- **Throttling**: Runs the function every **X milliseconds** while you’re typing — limiting the rate 

### 🟤 Example 1: Debounce
```js
function debounce(func, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => func.apply(this, args), delay);
  };
}

// Usage:
window.addEventListener('resize', debounce(() => {
  console.log('Resized after user stopped resizing');
}, 500));

```
Function runs **only after** the user stops resizing for 500ms.

### 🟤 Example 2: Throttle
```js
function throttle(func, interval) {
  let lastTime = 0;
  return function (...args) {
    const now = Date.now();
    if (now - lastTime >= interval) {
      func.apply(this, args);
      lastTime = now;
    }
  };
}

// Usage:
window.addEventListener('scroll', throttle(() => {
  console.log('Scroll event fired at controlled rate');
}, 300));

```
Function runs **at most once every 300ms**, no matter how fast the user scrolls.

|Feature|Debounce|Throttle|
|--------|---------|-----------|
|When function runs|After user stops performing the action for a specified time|At fixed intervals during continuous activity|
|Goal|Group multiple rapid events into a single one|Limit how often a function executes|
|Common use cases|Search input, resize events, form validation|Scroll events, window resizing, mouse move tracking|
|Example analogy|“Wait until you’re done talking, then I’ll respond.”|“I’ll respond every 1 second, no matter how much you talk.”|

</details>
---

<details>
<summary><b>Q10. How to trigger a <code>custom event</code> in JavaScript? </b></summary>

In JavaScript, we can **create and trigger (dispatch)** your own **custom events** using the built-in `CustomEvent` constructor and the `dispatchEvent()` method.

### 🟤 Step 1: Create a Custom Event

We can create a custom event with:

```js
const event = new CustomEvent('myEvent');
```
Here `'myEvent'` is the **event name** (you can choose any name).

### 🟤 Step 2: Add an Event Listener for It

```js
document.addEventListener('myEvent', () => {
  console.log('Custom event triggered!');
});

```
This listens for the `'myEvent'` event on the document.

### 🟤 Step 3: Trigger (Dispatch) the Event

```js
document.dispatchEvent(event);

```

**Output**
```js
Custom event triggered!
```

### 🟤 Passing Data with Custom Events

We can pass extra information (called **detail**) when creating the event:

```js
const customEvent = new CustomEvent('userLogin', {
  detail: { username: 'Suborno', time: '10:00 PM' }
});

document.addEventListener('userLogin', (e) => {
  console.log(`User: ${e.detail.username}, Time: ${e.detail.time}`);
});

document.dispatchEvent(customEvent);
```

**Output**
```js
User: Suborno, Time: 10:00 PM
```

### 🟤 Real-world Use Case

You might trigger a custom event when:

- A component finishes loading
- A background process completes
- You need to communicate between modules without direct function calls

</details>
---

<details>
<summary><b>Q11. Difference between <code>KeyboardEvent</code> and <code>InputEvent</code> in JavaScript? </b></summary>

|Feature|KeyboardEvent|InputEvent|
|--------|------------|-----------|
|Purpose|Represents events generated by keyboard actions (pressing or releasing keys).|Represents events that occur when the value of an <input>, <textarea>, or contentEditable element changes.|
|Triggered When|When a key is pressed (keydown), held, or released (keyup).|When the text value of an input changes (typing, pasting, deleting, autofill, etc.).|
|Event Types|keydown, keypress (deprecated), keyup.|input.|
|Target Elements|Usually any element that can receive keyboard focus.|Only input-related elements (like <input>, <textarea>, or elements with contenteditable="true").|
|Properties|key, code, altKey, ctrlKey, shiftKey, repeat, etc.|data, inputType, isComposing.|
|Captures Non-Text Keys?|Yes — detects keys like Arrow, Enter, Backspace, etc.|No — only fires when the element’s value actually changes.|
|Before Value Change?|Fires before the input value changes (keydown/keyup).|Fires after the value has changed.|
|Example Use Case|Detecting shortcut keys, navigation keys, or validating input while typing.|Reacting to changes in text content, such as live form validation or auto-suggestion.|


### 🟤 Example

```js
const input = document.querySelector('input');

input.addEventListener('keydown', (e) => {
  console.log('KeyboardEvent:', e.key);
});

input.addEventListener('input', (e) => {
  console.log('InputEvent:', e.data);
});

```
**Explanation:**
When you press `A`:
→ `keydown` fires first with `e.key = "a"`
→ `input` fires next with `e.data = "a"` (the input value has changed)

If you press `ArrowLeft`, only the **KeyboardEvent** fires — no value changed, so **InputEvent** doesn’t trigger.

</details>
---

<details>
<summary><b>Q12. How does delegation improve performance? </b></summary>

### 🟤 What delegation is:

Instead of attaching an event listener to **each individual child element**, you attach **one listener to a parent element**. When an event occurs, it bubbles up from the child to the parent, and the parent handles it.


Example in JavaScript:
```js
// Instead of adding click listeners to every button
document.querySelectorAll('button').forEach(btn => {
  btn.addEventListener('click', () => {
    console.log('Button clicked');
  });
});

// Use delegation
document.getElementById('button-container').addEventListener('click', (e) => {
  if(e.target.tagName === 'BUTTON') {
    console.log('Button clicked');
  }
});
```

### 🟤 Why delegation improves performance:

1. **Fewer event listeners** → less memory usage.

  - Adding hundreds or thousands of listeners can consume a lot of memory and slow down page load.

   - Delegation uses just one listener on the parent, no matter how many child elements exist.

2. **Dynamic content support**

  - If new child elements are added later (e.g., via innerHTML or appendChild), they automatically inherit the event handling without adding new listeners.

  - Without delegation, you would need to attach listeners manually for each new element.

3. **Better CPU efficiency**

  - The browser doesn’t have to loop through many listeners on every event — only the parent handles it and checks the target.
</details>
---

## ⚫ ES6+ Features {#es6-features}

<details>
<summary><b>Q1. What are <code>default parameters</code> in functions? </b></summary>

**Default parameters** in functions are **values that a function parameter takes if no argument** (or `undefined`) **is passed for that parameter** when the function is called.

This is very useful because it allows you to write functions that have optional parameters without having to check manually if the argument exists.

### ⚫ Syntax:
```js
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}
```
Here, `name` has a **default value** of "Guest".


### ⚫ Examples:

```js
greet("Alice"); // Output: Hello, Alice!
greet();        // Output: Hello, Guest!

```
- In the first call, `"Alice"` is passed → default is ignored.
- In the second call, no argument is passed → default `"Guest"` is used.

**Multiple Default Parameters**

```js
function multiply(a = 1, b = 1) {
  return a * b;
}

console.log(multiply(5, 2)); // 10
console.log(multiply(5));    // 5  (b defaults to 1)
console.log(multiply());     // 1  (both a and b default to 1)

```
**Key points:**

  - Defaults are **used only if the argument is** `undefined`. Passing `null` or `0` **does not trigger the default**.

   - They make functions **cleaner and safer** by avoiding manual checks like:

```js
function greet(name) {
  name = name || "Guest"; // old way
  console.log(`Hello, ${name}!`);
}
```
</details>
---
