# Day 6 — Practice Project: Profile / Bio Card

## 📅 What I Built Today

A **profile/bio card** component — avatar, name, role, bio text, and social/portfolio links — built purely as revision practice for Day 1's concepts (Variables + Nesting), no new SASS features introduced.

---

## 🧩 Concepts Reinforced

| Concept | Where It Was Used |
|---|---|
| **Variables** | `$bg-color`, `$dark-color`, `$light-color` defined in `_variables.scss` |
| **Nesting + `&`** | `.profile-card` nested with `.avatar`, `.name`, `.role`, `.bio`, and `.socials > a`, including `&:hover` on the links |
| **Partials + `@use`** | Reused the same `_variables.scss` / `_mixins.scss` pattern from earlier days |
| **Mixins** | `flex-center` (centering the card on the page) and a new `color-border` mixin (combines `color` + `border` into one reusable block, used both on the card and again inside the link's hover state) |

---

## 🐞 Bug I Hit & Fixed

**`transform: scale()` wasn't working on the social links.**

- The links (`<a>` tags) were styled with `transform: scale(1.5, 0.5)`, but nothing visibly happened.
- Root cause: anchor tags are `inline` elements by default, and `transform` doesn't apply reliably to inline elements in CSS — this isn't a SASS issue at all, it's standard CSS box-model behavior.
- **Fix:** added `display: inline-block;` to the link styles. Once the element had its own box, `transform` started working correctly.
- Also switched the hover effect to a simpler `transform: scale(1.05);` for a subtle, uniform zoom instead of the stretched/squished `scale(1.5, 0.5)` look.

---

## 🔑 Key Takeaways

- Not every styling bug is a SASS problem — sometimes it's a fundamental CSS behavior (like `transform` needing a non-inline display type) that's easy to forget under the hood of nested SCSS code.
- Reusing a mixin in two different contexts (default state *and* hover state) is a clean way to avoid repeating the same `color` + `border` combination twice.
- Revision projects like this one are useful even without new concepts — they reveal small CSS gaps (like the inline/transform issue) that pure concept-learning doesn't always surface.

---

## ➡️ Next Up: Day 7

FAQ Accordion (styling only) — practicing Partials, `@use`, and Mixins further.