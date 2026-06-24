# Day 7 — Practice Project: FAQ Accordion

## 📅 What I Built Today

An **FAQ accordion** using the native HTML `<details>` / `<summary>` tags — no JavaScript needed for the click-to-expand behavior. The focus was purely on styling it with SASS, reinforcing Partials, `@use`, and Mixins from Day 2.

---

## 🧩 Concepts Reinforced

| Concept | Where It Was Used |
|---|---|
| **Partials + `@use`** | `_variables.scss` (colors) and `_mixins.scss` (reusable style blocks), imported into `style.scss` |
| **Mixins** | `flex-center` (centering the FAQ box on the page), `color` (a small mixin that just sets the text color) |
| **`%placeholder` + `@extend`** | Created `%color` placeholder, which itself calls the `color` mixin via `@include` — then extended it across the heading, summary, and paragraph text instead of repeating the mixin call three separate times |
| **Native HTML behavior** | Learned that `<details>` + `<summary>` gives a fully working accordion (expand/collapse) with zero JavaScript |

---

## 💡 New Things I Noticed

- A `%placeholder` can contain a mixin call (`@include`) inside it. This means you can wrap a mixin in a placeholder to `@extend` it in multiple places, combining both reuse techniques together instead of choosing one or the other.
- Browsers handle `<details>`/`<summary>` natively — clicking the `<summary>` toggles visibility of everything else inside the `<details>` tag automatically, which is a useful trick for simple accordions without needing JS.

---

## 🔑 Key Takeaways

- Mixins and placeholders aren't mutually exclusive — combining them (placeholder that wraps a mixin) is a valid and sometimes cleaner pattern when the same mixin call needs to be extended across many selectors.
- Small UX details matter even in pure CSS work — e.g. remembering to set `cursor: pointer` on a clickable `<summary>` so it's clear to the user that it's interactive.
- Not every interactive UI pattern requires JavaScript — some native HTML elements already come with built-in behavior.

---

## ➡️ Next Up: Day 8

Testimonial Cards Section — practicing Functions, Operators, and `@extend` / Placeholders further.