# Day 2 — Reusability: Partials, @use & Mixins

## 📅 What I Learned Today

### 1. Partials
- A **partial** is a SCSS file whose name starts with an underscore `_` (e.g. `_variables.scss`, `_mixins.scss`).
- The underscore tells the Sass compiler: "Don't compile this file on its own — it's meant to be imported into another file."
- Used partials to split my code into separate files instead of writing everything in one giant `style.scss`:
  - `_variables.scss` → stores all color, font, and spacing variables.
  - `_mixins.scss` → stores reusable style blocks.

### 2. @use
- `@use` is the modern way to import one SCSS file into another (replacing the older, deprecated `@import`).
- When importing, I don't write the underscore or the `.scss` extension:
  ```scss
  @use "./partials/variables" as v;
  @use "./partials/mixins" as m;
  ```
- Every variable or mixin from an imported file must be accessed using its **namespace** (the name given after `as`):
  ```scss
  color: v.$primary-color;
  @include m.flex-center;
  ```
- This namespace system keeps things organized and avoids naming conflicts between files.

### 3. @forward (Concept Only)
- `@forward` is used to collect multiple partials into a single "index" file, so the main `style.scss` only needs **one** `@use` statement instead of many.
- I understood this concept but didn't need to apply it yet since my project only has two partials. It becomes useful in larger projects with many partial files.

### 4. Mixins
- A **mixin** is a reusable block of CSS — similar to a function in programming. Write the styles once, then reuse them anywhere with `@include`.
- Created simple mixins with no parameters:
  ```scss
  @mixin flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  ```
- Created mixins that accept **parameters**, making them flexible for different use cases:
  ```scss
  @mixin rounded($pos) {
    border-radius: $pos;
  }
  ```
  This single mixin can round all four corners, or just specific ones, depending on what value is passed in (e.g. `@include m.rounded(20px 20px 0 0);` for only the top corners).

---

## 💻 What I Built

A **stopwatch/timer UI** with a display area on top and Start / Reset / Stop buttons at the bottom. Used `@use` with namespaces for variables and mixins throughout, and applied the `rounded()` mixin with different parameter combinations to control corner radius on different elements — including a creative hover effect that swaps which corners are rounded.

---

## 🔑 Key Takeaways

- Partials = breaking code into smaller, organized files.
- `@use` = the modern way to import partials, always accessed through a namespace.
- `@forward` = bundles multiple partials into one importable file (useful for bigger projects).
- Mixins = reusable style blocks, just like functions — can also accept parameters for flexibility.
- Writing one flexible, parameterized mixin (like `rounded($pos)`) is better than writing multiple single-purpose mixins.

---

## ➡️ Next Up: Day 3

- Functions (`@function`)
- Operators (math operations on values)
- `@extend` / Inheritance