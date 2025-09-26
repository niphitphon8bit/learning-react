# React Fundamentals Notes

## 1. What is React?
- React is a declarative JavaScript library for building user interfaces from small, reusable components.
- React keeps an in-memory representation of the UI (often called the virtual DOM) and updates the real DOM efficiently when component state or props change.
- It focuses on the view layer only, so you often pair it with other libraries for routing, data fetching, or state management when building a full application.

## 2. Why are there multiple React packages?
- The core `react` package contains the component API (hooks, lifecycle, JSX support) and is shared across every environment.
- React DOM provides a renderer that knows how to translate React elements into DOM nodes in the browser: in a CDN setup you load both `react.development.js` and `react-dom.development.js`, and in a bundler setup you install `react` and `react-dom` from npm.
- React Native is a separate framework that ships with its own renderer; it does not run in the browser or share the same bundle as React DOM, even though it reuses the core `react` package API.

## 3. How do I set up React and what does `render` do?
- With script tags you load React, React DOM, and (optionally) Babel so the browser can understand JSX while you learn. Example:

```html
<div id="root"></div>
<script src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
<script type="text/babel">
  const root = ReactDOM.createRoot(document.getElementById('root'));
  root.render(<h1>Hello, React!</h1>);
</script>
```
- In modern React (18+) you call `ReactDOM.createRoot(domNode)` to create the root, then call `root.render(<App />)` to mount components into that DOM node. Older code uses `ReactDOM.render(<App />, domNode);`.
- In real projects you typically use a build tool (Vite, Create React App, Next.js, etc.) that installs `react` and `react-dom` and bundles your code instead of relying on global script tags.

## 4. What are JSX and Babel?
- JSX is a JavaScript syntax extension that lets you write markup-like code that compiles to `React.createElement(...)` (or the modern JSX runtime) calls. Browsers cannot execute JSX directly.
- Babel is a compiler/transpiler that can transform JSX and modern JavaScript features into code that current browsers understand.
- When learning without a build step you can include Babel via `<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>` and mark scripts with `type="text/babel"`. For production bundles you precompile JSX with Babel (or another tool) before shipping so you serve plain JavaScript.

---

**Key takeaway:** React gives you the component model; renderers such as React DOM or React Native connect that model to the target platform, and tools like Babel turn your JSX into executable JavaScript.