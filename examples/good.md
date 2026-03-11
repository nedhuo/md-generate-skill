# Examples: Good Markdown

These examples show the same content rewritten following the skill rules.

---

## Good Example 1: Technical Note on React Hooks

# React Hooks

React Hooks let you use state and lifecycle features inside functional components, without writing a class. Introduced in React 16.8, they replaced most class component patterns in modern React codebases.

## Why it matters

Before Hooks, stateful logic was tied to class components, making it hard to share behavior between components. Hooks let you extract and reuse stateful logic as plain functions.

## How it works

Each Hook is a function that taps into React's internal state and effect system. The two most fundamental ones:

- `useState` — declares a state variable and a setter function
- `useEffect` — runs side effects after render (data fetching, subscriptions, DOM mutations)

React tracks Hook calls by their order within a component, which is why Hooks must be called at the top level — never inside conditionals or loops.

## Usage

```jsx
import { useState, useEffect } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

## Gotchas

Only call Hooks at the top level of a React function. Calling them inside loops, conditions, or nested functions breaks React's ordering guarantee and causes subtle bugs.

---

## Good Example 2: Tutorial — Setting up Node.js

# Setting up Node.js

By the end of this guide, you'll have Node.js and npm installed and verified on your machine.

## Prerequisites

- A terminal (macOS/Linux) or PowerShell (Windows)
- Admin/sudo access

## Steps

1. Go to [nodejs.org](https://nodejs.org) and download the LTS installer for your OS.
2. Run the installer and follow the prompts. Accept the default installation path.
3. Verify the installation:

```bash
node --version
npm --version
```

## Verification

Both commands should print a version number, for example:

```
v20.11.0
10.2.4
```

If either command returns "command not found", close and reopen your terminal, then retry.

## Troubleshooting

`node: command not found` after install — the installer didn't add Node to your PATH. On macOS, add `export PATH="/usr/local/bin:$PATH"` to your `~/.zshrc` and run `source ~/.zshrc`.

---

## Good Example 3: Configuration as prose + list

### Configuration

The server reads configuration from environment variables at startup.

- `PORT` — port to listen on (default: `3000`)
- `HOST` — bind address (default: `localhost`)
- `DEBUG` — set to `true` to enable verbose logging

Project layout:

- `src/` — application source code
- `dist/` — compiled output (generated, do not edit)
- `tests/` — unit and integration tests
