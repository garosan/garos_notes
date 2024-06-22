# The Complete JavaScript Course 2024: From Zero to Expert

📕 Title: The Complete JavaScript Course 2024: From Zero to Expert

👨‍🏫 Instructors: Jonas Schmedtmann

🌐 Platform: Udemy

💾 Topics: JavaScript

📄 Sections: 20

🎥 Hours: 69h

## 📝 Table of Contents

- S1. Welcome, Welcome, Welcome
- S2. JavaScript Fundamentals - Part 1
- S3. JavaScript Fundamentals - Part 2
- S4. How to Navigate this Course
- S5. Developer Skills & Editor Setup
- S6. HTML & CSS Crash Course
- S7. JavaScript in the Browser: DOM and Events Fundamentals
- S8. How JavaScript Works Behind the Scenes
- S9. Data Structures, Modern Operators and Strings
- S10. A Closer Look at Functions
- S11. Working With Arrays
- S12. Numbers, Dates, Intl and Timers
- S13. Advanced DOM and Events
- S14. Object-Oriented Programming (OOP) with JavaScript
- S15. Mapty App: OOP, Geolocation, External Libraries and More!
- S16. Asynchronous JavaScript: Promises, Async/Await and AJAX
- S17. Modern JavaScript Development: Modules, Tooling and Functional
- S18. Forkify App: Building a Modern Application
- S19. Setting Up Git and Deployment
- S20. The End!

## 🛠️ Resources

## S1. Welcome, Welcome, Welcome!

[Course Starter Code](https://github.com/jonasschmedtmann/complete-javascript-course)

## S5. Developer Skills & Editor Setup

Setting up a personal code snippet for console.log 
Lecture 55, min 12

Installing Live Server extension.

https://www.codewars.com/ for coding challenges.

## S7. JavaScript in the browser: DOM and Events Fundamentals


## S8. How JavaScript Works Behind the Scenes

### High-Level Overview of JavaScript

A big picture definition of the language: JavaScript is a high-level, prototype-based object-oriented, multi-paradigm, interpreted or just-in-time compiled, dynamic, single-threaded, gargabe-collected programming language with first-class functions and a non-blocking event loop concurrency model.

So the topics of this section:

- high level
- garbage-collected
- interpreted or just-in-time compiled
- multi-paradigm
- prototype-based object-oriented
- first-class functions
- dynamic
- single-threaded
- non-blocking event loop

### The JavaScript Engine and Runtime

Every browser has its own JS engine. V8 is the engine that powers Chrome and Node.

The engine has a call stack and a heap.

Compilation vs Interpretation.

Interpretation: An interpreter runs through the source code and executes it line by line. The problem is that interpreted languages are way way slower. This is not acceptable with modern full-fledged applications.
So modern JS engines use an approach called JIT compilation: Entire code is converted into machine code at once, then executed immediately.

Steps:

1. The engine parses the file which contains the code into an abstract syntax tree (AST)
2. Compilation: Compiles the generated AST into machine code
3. Execution: Execution happens immediatly inside the call stack
4. Optimization: Engine runs a very unoptimized version of the code to start with, then it starts optimizing certain parts and replacing the unoptimized parts with the new ones.

A JavaScript runtime is a container with all the pieces we need to run JavaScript. The most common one is the browser. 
The browser JS runtime contains the JS engine, the WEB APIs (through the window object) and the callback queue.

An eventHandler function is also called a callback function.

*The event loop takes callback functions from the callback queue and puts them in the call stack so they can be executed.*

### Execution contexts and the call stack

A global execution context is created for top-level code. An execution context is an environment where JavaScript code is executed.

In any given JavaScript project, no matter how large or complex it is, there's only ever one global execution context.

For each function call, a new execution context is created *one execution context per function*.

What's inside an execution context?

- A variable environment
	- let, const and var declarations
	- Functions
	- arguments object
- Scope chain
	- (References to variable that are outside the execution context)
- this keyword

**Execution contexts belonging to arrow functions do not get an arguments object nor a this keyword.**

The call stack is basically the place that tracks where we are in the execution contexts.

[JavaScript Execution Context – How JS Works Behind the Scenes](https://www.freecodecamp.org/news/how-javascript-works-behind-the-scene-javascript-execution-context/)
[Microtasks and the JavaScript runtime environment](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API/Microtask_guide/In_depth)

