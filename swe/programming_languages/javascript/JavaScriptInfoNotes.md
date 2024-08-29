Today, JavaScript can execute not only in the browser, but also on the server, or actually on any device that has a special program called the JavaScript engine.

The browser has an embedded engine, different engines have different names:

- V8 - in Chrome, Opera and Edge
- SpiderMonkey - in Firefox
- Chakra for IE
- JavaScriptCore, Nitro and SquirrelFish for Safari, etc.

The basics of how a JavaScript engine works are pretty easy:

- The engine (embedded if it’s a browser) reads (“parses”) the script.
- Then it converts (“compiles”) the script to machine code.
- And then the machine code runs, pretty fast.

The engine applies optimizations at each step of the process. It even watches the compiled script as it runs, analyzes the data that flows through it, and further optimizes the machine code based on that knowledge.

### What can in-browser JavaScript do?

Modern JavaScript is a "safe" programming language. It does not provide low-level access to memory or the CPU, contrary to C, C++ or Rust for example.

In-browser JavaScript can do everything related to webpage manipulation, interaction with the user, and the webserver.

## What CAN’T in-browser JavaScript do?

- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs.
- There are ways to interact with the camera/microphone and other devices, but they require a user’s explicit permission.
- Different tabs/windows generally do not know about each other.
- JavaScript from one page may not access the other page if they come from different sites (from a different domain, protocol or port). This is called the “Same Origin Policy”.

### Languages 'over' JavaScript

- CoffeeScript. Usually, Ruby devs like it.
- TypeScript adds 'strict data typing'. Developed by Microsoft.
- Flow also adds data typing, but in a different way. Developed by Facebook.
- Dart is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- Kotlin is a modern, concise and safe programming language that can target the browser or Node.

## Manuals and specifications

This book is a tutorial. It aims to help you gradually learn the language. But once you’re familiar with the basics, you’ll need other resources.

The [ECMA-262 specification](https://www.ecma-international.org/publications/standards/Ecma-262.htm) contains the most in-depth, detailed and formalized information about JavaScript. It defines the language.

A new specification version is released every year. Meanwhile there's a draft at [TC39](https://tc39.es/ecma262/).

[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) is the most used day-to-day reference.
