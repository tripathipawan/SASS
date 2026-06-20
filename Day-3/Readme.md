# Day 3 — Logic & Math: Functions, Operators & @extend

## 📅 What I Learned Today

### 1. Operators
- SASS allows direct math operations on values: addition (`+`), subtraction (`-`), multiplication (`*`), division (`/`), and modulo (`%`).
- Learned that in modern Dart Sass, `math.div()` is the recommended way to divide values safely (instead of the older `/` operator).
- Used multiplication throughout the project via a custom function to keep spacing consistent.

### 2. Functions (`@function`)
- A **function** returns a single **value**, unlike a mixin which returns a block of CSS properties.
- Created a custom function to calculate consistent spacing values:
  ```scss
  @function spacing($multiplier) {
    @return 8px * $multiplier;
  }
  ```
- Used it everywhere instead of hardcoding pixel values:
  ```scss
  padding: spacing(1);
  gap: spacing(4);
  height: spacing(25);
  ```
- This makes it easy to scale the entire design's spacing system by changing just one base value.

### 3. Mixin vs Function — The Difference
| | Mixin | Function |
|---|---|---|
| Returns | A block of CSS properties | A single value |
| Called with | `@include mixin-name;` | `function-name()` directly where a value is expected |

### 4. @extend & Placeholders (`%`)
- `@extend` lets one selector inherit all the styles of another, without duplicating CSS like a mixin does.
- Learned that `@extend` groups selectors together in the compiled CSS instead of repeating the same properties for each one — keeping the output smaller.
- Used **`%placeholder`** selectors for styles that are never meant to be used standalone in HTML, only to be extended:
  ```scss
  %card-base {
    // shared card styles
  }

  .card {
    @extend %card-base;
  }
  ```
- Created two placeholders: `%card-base` (shared structure for all pricing cards) and `%btn-base` (shared structure for all buttons), then extended them across multiple classes and added unique colors on top.

---

## 💻 What I Built

A **3-tier pricing card section** (Basic, Pro, Premium) with consistent spacing powered by a custom `spacing()` function, shared card/button structure via `%placeholder` + `@extend`, and a hover effect (`scale()` + `box-shadow`) on each card for a subtle interactive feel.

---

## 🔑 Key Takeaways

- Functions are for **calculating and returning values** (like a reusable formula); mixins are for **reusing whole style blocks**.
- `@extend` with `%placeholders` is the cleanest way to share styles across multiple classes without bloating the compiled CSS.
- Defining a single spacing function early on makes the whole project's spacing easy to adjust and keeps numbers consistent instead of scattering random pixel values everywhere.
- Need to double check shared hover styles on placeholders — if every extended element shares the exact same hover behavior, that might not always be the desired result; sometimes each variant needs its own distinct hover style defined individually.

---

## ➡️ Next Up: Day 4

- Control Directives: `@if` / `@else`
- `@each` (looping over lists)
- `@for` (looping over a number range)
- Maps (`$map: (key: value)`)