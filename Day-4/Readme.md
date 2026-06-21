# Day 4 — Control Flow: @if, @each, @for & Maps

## 📅 What I Learned Today

### 1. @if / @else if / @else
- Works just like conditional statements in programming — applies different styles based on a condition.
- Used inside a mixin to conditionally apply styles based on a parameter:
  ```scss
  @mixin fs($size) {
    font-size: $size;

    @if $size > 20px {
      font-weight: bold;
    } @else {
      font-weight: normal;
    }
  }
  ```
- Learned an important lesson here: when calling a mixin like `@include fs($size)`, an **actual value** must be passed in (e.g. `@include fs(24px)`), not the parameter name itself — the parameter name only exists inside the mixin's own definition.
- Also learned that values being compared with `>`, `<`, etc. should have matching units (e.g. comparing `px` to `px`).

### 2. Maps (`$map: (key: value)`)
- A **map** is a SASS data structure similar to an object/dictionary — it stores multiple key-value pairs in one variable:
  ```scss
  $colors: (
    primary: #00daf3,
    danger: red,
    success: green
  );
  ```
- This is extremely useful for organizing related values (like a whole color palette or a set of badge colors) in one place instead of as separate variables.

### 3. @each (Looping Over Lists & Maps)
- `@each` loops over every entry in a list or map and generates CSS automatically for each one.
- Looping over a map gives **two values per iteration** — the key and the value:
  ```scss
  @each $key, $value in $colors {
    .text-#{$key} {
      color: $value;
    }
  }
  ```
- Learned to use **interpolation (`#{}`)** to insert a variable's value directly into a selector name — this is what makes dynamic class names like `.text-primary`, `.badge-live`, etc. possible.
- Made a clear mistake early on by trying to reference a map key as if it were its own standalone variable (e.g. writing `$success` instead of `$key`), and learned that the loop variables (`$key`, `$value`) only exist within the loop — they aren't separate variables tied to the map's contents.

### 4. @for (Looping Over a Number Range)
- `@for` loops through a range of numbers, generating one rule per number — perfect for utility classes:
  ```scss
  @for $i from 1 to 6 {
    .p-#{$i} {
      padding: $i * 4px;
    }
  }
  ```
- Learned the difference between `through` (includes the last number) and `to` (excludes the last number).
- This is the same technique frameworks like Tailwind CSS and Bootstrap use internally to generate their utility classes (`.p-1`, `.p-2`, `.mt-3`, etc.) instead of writing each one by hand.

### 5. @while (Concept Covered)
- Works like a `while` loop — repeats as long as a condition is true. Needs a manual increment inside the loop to avoid running forever. Less commonly used than `@for` in everyday styling.

---

## 💻 What I Built

1. A small **utility-class system** (`.text-{color}`, `.bg-{color}`, `.p-{number}`) generated dynamically from a colors map and a number range — a simplified version of how real utility-first CSS frameworks work under the hood.
2. A **badge component generator**: a single `$badges` map (live, new, sale, hot, free) looped through with `@each` to automatically create five differently colored badge classes, plus one shared `.badge` class for common styling (padding, border-radius, font-weight).

---

## 🔑 Key Takeaways

- `@each` + Maps is one of the most powerful combinations in SASS — a few lines of code can generate dozens of CSS classes.
- Interpolation (`#{}`) is what bridges a SASS variable's value into an actual CSS selector or property name.
- When working with `@each $key, $value in $map`, always be clear about which variable goes where: the **key** for naming things (class names), and the **value** for the actual style value (colors, sizes, etc.).
- `@for` is ideal for generating numbered/scaled utility classes (spacing, sizing) without manually writing each one.
- Passing an actual value into a mixin/function call is different from the parameter name used inside its definition — mixing these up was my main mistake of the day, now fully understood.

---

## ➡️ Next Up: Day 5 — Final Mini Project

Combining everything learned across all 4 days — Variables, Nesting, Partials, `@use`, Mixins, Functions, `@extend`/Placeholders, and Control Directives (`@if`, `@each`, `@for`) — into one complete navbar + grid/card layout project.