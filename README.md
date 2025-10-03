# 200-JavaScript-Interview-Questions
This repository contains categorized JavaScript questions with answers.

## 📑 Table of Categories

| Category              | Number of Questions | Link to Questions |
|-----------------------|---------------------|------------------|
| 🔴 Basics             | 10                  | [View](#-basics) |
| 🟠 vartiables & Scope  | 10                  | [View](#-variables--scope) |
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
<summary><h3>Q1. What is JavaScript and how is it different from Java?</h3></summary> 

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

<details>
<summary><h3>Q. What are the different data types in JavaScript?</h3></summary>

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

<details>
<summary><h3>Q. What is the difference between <code>null</code> and <code>undefined</code> in JavaScript?</h3></summary>

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

<details>
<summary><h3>Q. What is a "quirk" of JavaScript? Can you give examples?</h3></summary>

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

3. **`NaN` is not equal to itself**
```js
console.log(NaN === NaN); // false
```
👉 Only value in JS that is not equal to itself.

4. **`NaN` is not equal to itself**
```js
console.log(NaN === NaN); // false
```
👉 Only value in JS that is not equal to itself.
</details>





<details>
<summary><h3>Q. What is <code>NaN</code> in JavaScript?</h3></summary>

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
</details>
