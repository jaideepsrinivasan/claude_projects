# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm install       # install dependencies
npm run dev       # start dev server at http://localhost:5173
npm run build     # production build
npm run lint      # run ESLint
npm run preview   # preview production build
```

No test suite is configured.

## Architecture

This is a single-file React app — all state, logic, and UI live in `src/App.jsx`. There is no routing, no backend, and no external state library. All transaction data is held in a single `useState` array and never persisted (refreshing the page resets it to the hardcoded seed data).

**Data shape for a transaction:**
```js
{ id, description, amount (number), type ("income"|"expense"), category, date ("YYYY-MM-DD") }
```

**Key facts:**
- `amount` must be stored and handled as a `number` (use `parseFloat` when reading from form inputs or seed data strings).
- Summary totals (income, expenses, balance) are derived inline from the transactions array on every render.
- Filtering by type and category is also done inline — no derived state, no memoization.
- `src/App.css` contains all styles; there is no CSS framework or utility library.
- The `.delete-btn` class exists in CSS but the delete button is not yet wired up in the JSX — this is intentional (course exercise).
