# ⚛️ React Study Guide

## 📄 Table of Contents

- The rise of SPAs and frontend frameworks
- Introduction to React
- Components
- JSX
- Props
- State in React
- Fundamentals of State Management
- Derived State
- The children prop
- Split a UI into components
- How rendering works
- How diffing works
- The key prop
- State update batching
- How events work in React
- The component lifecycle
- A first look at events
- useEffect
- React hooks and their rules
- useState
- useRef
- custom hooks
- Managing state with useReducer
- useState vs useReducer
- Routing
- Styling options
- The Context API
- Performance optimizations and wasted renders
- Understanding memo
- useMemo and useCallback
- Code splitting
- useEffect rules and best practices
- Intro to Redux
- redux middleware and thunks
- Redux Toolkit (RTK)
- Redux vs Context API
- TailwindCSS
- Supabase
- React Query
- Server-Side Rendering
- Hydration
- React Server Components
- React Suspense
- Server Actions

## React Notes

### Why Do Front-End Frameworks Exist?

- The Rise of SPAs
- SSR -> Wordpress -> jQuery -> Tons of JS code -> CSR -> FE Frameworks -> Back to SSR with Next, Remix.
- Maintaining UI in sync with data in a huge enterprise app like AirBnb or Facebook is impossible with vanilla JS
- FE Frameworks:
  - Solve the problem of keeping UI and data in sync
  - Enforce a structured way of writing code and avoid 'spaghetti code'
  - Give developers and teams a consistent way of building FE apps

### What is React?

- A JS library for building UIs
- Main characteristics:
  - Based on components
  - Declarative: Abstracting away the DOM, we use JSX to describe how the UI should look and behave
  - State-driven: 'Reacts' to state changes by re-rendering the UI
  - JS Library: React is only the 'view' layer. Next.js and Remix are frameworks built on top of React
  - Extremely popular, created and backed by Facebook (Created in 2011 by Jordan Walke)

### Setting up a project

Two options:

- create-react-app
- Vite

The React docs now recommend to use a production-grade framework like NextJS or Remix for production apps, but don't worry about that when just learning React.

### React Basics

What are components? - React apps are entirely made out of components - Building blocks of UIs in React - A component has its own data, logic and appearance - Components can be reused, nested inside each other, and pass data between them

What is JSX? - Declarative syntax to describe what components look like and how they work - Components must return a block of JSX - Each JSX element is converted to a React.createElement function call - Imperative approach: - Manual DOM element selections and DOM traversing - Step-by-step DOM mutations until we reach the desired UI - Declarative approach (The React way): - Describe what the UI should look like using JSX, based on current data - React is an abstraction away from the DOM - We think of UI as a reflection of the current data

Separation of Concerns

Traditionally separation of concerns meant having one file for HTML, one for CSS and one for JS.

With the rise of SPAs, we put JS in charge of HTML, we acknowledge that logic and UI are tightly coupled, and so we separate logically the UI in components, with each component being its own unit of data, logic and appearence.

### Props, Immutability and One-Way data flow

- Props are used to pass data from parent components to child components
- State is internal data that can be updated by the component's logic
- Props are read-only, they are immutable
- If you need to mutate pros, what you actually need is state
- One way data flow makes apps more predictable, easier to debug and more performant

### State, events and forms: What is state?

- State is data that a component can hold over time, throughout the app's lifecycle
- We call a single local component variable a 'piece of state' or 'state variable'
- Updating component state triggers React to re-render the component

### The mechanics of state

- In React, a view is updated by re-rendering the component
- A component is re-rendered when its state is updated
- State is preserved throughout re-renders
- One way to update state is through event handlers

### More state guidelines

- One component, one state: Each component manages its own state
- We can have a lot of different instances of the same component. Each instance manages its own state
- We view the UI as a reflection of data changing over time
- We describe those data changes using state, event handlers, and JSX

Remember:

- Use a state variable for any data that the component should keep track of over time
- For data that should not trigger component re-renders, don't use state, use a regular variable instead.

### State vs Props

State:

- Internal data, owned by the component
- Can be used by the component itself
- Updating state causes component to re-render
- Used to make components interactive

Props:

- External data, owned by parent component
- Similar to function parameters
- Read-only
- Receiving new props causes the component to re-render (usually when parent's state is updated)

### Thinking in React: State management

The process of thinking in React:

- Break the desired UI into components and establish a component tree
- Build a static version in React (without state)
- Think about state:
  - When to use state
  - Types of state: local vs global
  - Where to place each piece of state
- Establish data flow:
  - One-way data flow
  - Accessing global state

Ask yourself the following questions:

- How to break up a UI design into components?
- How to make some components reusable?
- How to assemble UI from reusable components?
- What pieces of state do I need for interactivity?
- Where to place state? (What component should own each piece of state?)
- What types of state can or should I use?
- How to make data flow through the app?

## 📕 React Books

Packt - Fang Jin - Designing React Hooks the Right Way
Packt - Shama Hoque - Full-Stack React Projects
Packt - David Choi - Full-Stack React, TypeScript and Node
Packt - Sebastian Grebe - Full-Stack Web Development with GraphQL and React
Packt - Daniel Irvine - Mastering React Test-Driven Development
Packt - Daishi Kato - Micro State Management with React Hooks
Packt - Carlos Santana Roldán - React 18 Design Patterns and Best Practices
Packt - Juntao Qiu - React Anti-Patterns
Packt - Alan Alickovic - React Application Architecture For Production
