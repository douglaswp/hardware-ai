# Contributing to tflops-calculator

Thank you for your interest in contributing! Below are the instructions for setting up the environment, the expected workflow, and the project conventions.

---

## Environment setup

**Prerequisites:** Node.js 18+ and npm.

```bash
git clone https://github.com/douglaswp/tflops-calculator.git
cd tflops-calculator
npm install
npm run dev
```

The development server will be available at `http://localhost:5173` with HMR (Hot Module Replacement) enabled.

---

## Workflow

1. Create a branch off `main` with a descriptive name:
   ```bash
   git checkout -b feat/feature-name
   # or
   git checkout -b fix/bug-description
   ```

2. Make your changes and ensure lint passes:
   ```bash
   npm run lint
   ```

3. Verify the production build completes without errors:
   ```bash
   npm run build
   ```

4. Open a Pull Request to `main` with a clear description of what was changed and why.

---

## Project conventions

### Language
The user interface is in **Portuguese (pt-BR)**: labels, error messages, placeholders, and code comments should follow this standard.

### Structure
All logic and components live in `src/App.jsx` (single file). When adding new components, define them in the same file following the existing structure, unless the complexity justifies extracting them to `src/components/`.

### Styling
Use exclusively **Tailwind CSS utility classes**. Do not add custom CSS to `App.css` or create new `.css` files for component styling. For theme variants, always pass the `isDark` prop and apply ternaries following the pattern:
```jsx
className={isDark ? 'bg-slate-800 text-slate-200' : 'bg-white text-slate-900'}
```

### Icons
Icons are inline SVG functional components defined at the top of `App.jsx`. Add new icons in that section following the same pattern — no external icon dependencies.

### Derived state
Use `useMemo` for computed values that depend on `hardwareList` or `selectedItems`. Avoid recalculating data inside JSX.

### Value formatting
- **Currency:** always use `formatCurrency(value)` (BRL format).
- **Numbers:** use `toLocaleString('pt-BR', ...)` for display.

### Lint
The project uses ESLint with `eslint-plugin-react-hooks` and `eslint-plugin-react-refresh`. Fix all errors before opening a PR. `UPPER_CASE` variables are intentionally ignored by the `no-unused-vars` rule.

---

## Available commands

| Command | Description |
|---|---|
| `npm run dev` | Starts the development server |
| `npm run build` | Generates the production build in `dist/` |
| `npm run preview` | Previews the production build |
| `npm run lint` | Runs ESLint |

---

## Reporting bugs or suggesting improvements

Open an [issue](https://github.com/douglaswp/tflops-calculator/issues) describing:
- The current behavior
- The expected behavior
- Steps to reproduce (if it's a bug)
