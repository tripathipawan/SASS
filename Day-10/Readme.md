# Day 10 — Final Review Project: Pricing Table

## 📅 What I Built Today

A complete **pricing table** (Basic / Most Popular / Premium plans) — the final review project, built mostly independently with minimal hints, combining almost every SASS concept learned across the entire 10-day journey.

---

## 🧩 Concepts Applied

| Concept | Where It Was Used |
|---|---|
| **Variables** | All colors (`$bg`, `$bg2`, `$text`, `$heading`, `$border`) in `_variables.scss` |
| **Function** | `mul($e)` (`8px * $e`) used for every padding, margin, gap, and border-radius value |
| **Nesting + `&`** | `.plan > .plan-price > span`, `.plan-features > li`, `.plan-btn` with `&:hover` |
| **Partials + `@use`** | `_variables.scss` and `_mixins.scss` imported into `style.scss` |
| **Mixin** | `flex-center` for centering the whole pricing section on the page |
| **`%placeholder` + `@extend`** | `%card` (grid layout: 3 columns + gap) extended into `.pricing-grid` |
| **Map + `@each`** | `$plan-badge` map (basic, medium, premium → gray, green, gold) looped to generate each plan's badge color |
| **`&:hover`** | Button hover state inverts background/text color |

---

## 🐞 Bugs I Hit & Fixed

1. **Grid "not working"** — the grid layout was actually working correctly the whole time; the real issue was that the `.plan` cards inside it had no visible styling (no border/padding) yet, making it look like the grid wasn't doing anything. Confirmed using browser DevTools that `display: grid` was applied, then added styling to the `.plan` elements to make the layout visible.

2. **Duplicate class + undefined variable** — had written `.pricing-subtitle` twice by mistake (one of them meant to be `.pricing-title` for the `<h1>`), and one of those blocks referenced a variable (`$color`) that was never defined in `_variables.scss`. This likely caused a silent compile issue. Fixed by correcting the class name and pointing to an actual defined variable (`$text`).

---

## 🔑 Key Takeaways

- "It's not working" can mean different things — sometimes the CSS property itself is broken, and sometimes it's working fine but there's nothing visible to confirm it (like an unstyled grid item). Checking computed styles in DevTools is the fastest way to tell the difference.
- Copy-pasting a class block and forgetting to rename it (`.pricing-subtitle` written twice) is an easy mistake to make when building multiple similar sections quickly — worth a quick re-read before moving on.
- Referencing an undefined variable can silently break the whole compile, not just that one line — always good to double-check a partial's variable names if newly written CSS doesn't show up at all.
- By Day 10, combining variables, functions, nesting, mixins, placeholders, and maps into one project felt natural rather than something to consciously plan out — which was the actual goal of this 10-day practice run.

---

## 🏁 10-Day SASS Journey — Complete

This wraps up the full roadmap: Days 1–5 covered the core SASS concepts one at a time, and Days 6–10 were independent practice projects (Profile Card, FAQ Accordion, Testimonial Cards, Badge Generator, Pricing Table) built to make those concepts feel second nature.

**Next step:** Moving on to learning Tailwind CSS, while keeping this SASS foundation as a base for any Bootstrap/SASS-based projects in the future.