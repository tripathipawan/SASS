# Day 1 — Foundations: Setup, Variables & Nesting

## 📅 What I Learned Today

### 1. Setup
- Installed the **Live Sass Compiler** extension (by Glenn Marks) in VS Code.
- Learned that SASS files use the **`.scss`** extension (not `.sass`, which is a different indented syntax without curly braces).
- Clicked **"Watch Sass"** in the VS Code status bar to auto-compile `.scss` → `.css` on every save.
- Understood the role of each generated file:
  - `style.scss` → where I actually write my code.
  - `style.css` → the compiled, browser-readable CSS (auto-generated, never edited directly).
  - `style.css.map` → a source map that helps DevTools point back to the original `.scss` line during debugging.

### 2. Variables
- Learned to declare variables using the `$` symbol:
  ```scss
  $primary-color: #00daf3;
  $base-padding: 15px;
  ```
- Reused variables across multiple selectors instead of repeating hardcoded values.
- Discovered that **math operations** work directly on variables:
  ```scss
  padding: $base-padding $base-padding * 2;
  font-size: $text-size * 2;
  ```
- Used `//` for SCSS-only comments (these don't appear in the compiled CSS output).

### 3. Nesting
- Nested child selectors inside their parent to mirror HTML structure and avoid repeating the parent selector name:
  ```scss
  .card {
    h1 { color: $primary-color; }
    p  { font-size: $text-size; }
  }
  ```
- Learned the `&` symbol represents the **parent selector**, essential for pseudo-classes:
  ```scss
  .btn {
    &:hover {
      background-color: $primary-color;
    }
  }
  ```
- Learned the best practice: **avoid nesting more than 3 levels deep**, as it creates overly specific, hard-to-maintain CSS.

---

## 💻 What I Built

A simple card component (`.card`) with a heading, paragraph, and a button (`.btn`), styled entirely with SCSS variables and nesting. Added a smooth `transition` on the button's hover state as an extra touch beyond the core lesson.

---

## 🔑 Key Takeaways

- Variables = single source of truth for colors, fonts, spacing → easy to update everywhere at once.
- Nesting = cleaner, more readable code that mirrors HTML structure.
- `&` = parent selector reference, critical for pseudo-classes and states.
- Compiled CSS is auto-generated — never edit `style.css` directly.

---

## ➡️ Next Up: Day 2

- Partials (`_filename.scss`)
- `@use` and `@forward` (importing modules)
- Mixins (`@mixin` / `@include`)