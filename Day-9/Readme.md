# Day 9 — Practice Project: Badge / Tag Generator

## 📅 What I Built Today

A **badge/tag generator** — a set of colored status badges (Primary, Success, Danger, Warning, Info) plus size variants (Small, Medium, Large), and a spacing utility-class demo (`p-1` to `p-5`). Built to reinforce Day 4's concepts: Maps, `@each`, and `@for`.

---

## 🧩 Concepts Reinforced

| Concept | Where It Was Used |
|---|---|
| **Map** | `$badges` (color name → hex value) and a **nested map** `$badge-sizes` (size name → another map of `padding` + `font`) |
| **`@each` (simple map)** | Looped over `$badges` to generate `.badge-{name}` background colors |
| **`@each` (nested map)** | Looped over `$badge-sizes`, using `map-get()` *twice* — once to get each size's inner map, and once more to pull out `padding` and `font` from it |
| **`@for`** | Generated `.p-1` through `.p-5` spacing utility classes from a number range |
| **Function** | A small `mul($e)` function (`8px * $e`) used for consistent spacing throughout |

---

## 🐞 Bugs I Hit & Fixed

1. **Case sensitivity in map keys** — defined map keys like `Primary` (capitalized) while the HTML used lowercase classes like `badge-primary`. CSS class names are case-sensitive, so `.badge-Primary` (generated) never matched `.badge-primary` (in HTML). Fixed by keeping map keys lowercase to match the HTML exactly.

2. **Unrelated CSS nested inside a loop** — initially placed `.badge`, the `@for` spacing loop, and `.spacing-demo .box` *inside* the `@each $badges` loop. Since that loop runs once per map entry, all of that unrelated CSS was being duplicated 5 times in the compiled output — it still worked visually, but bloated the CSS unnecessarily. Fixed by moving anything that doesn't use the loop's variables (`$key`, `$value`) outside the loop entirely.

3. **CSS rule order matters for overrides** — even after splitting into separate loops, the size variants (`.badge-sm`, `.badge-md`, `.badge-lg`) were being overridden by the base `.badge` class because `.badge` appeared *after* them in the compiled CSS. Since both rules targeted the same elements with the same specificity, whichever came later in the file won. Fixed by ordering it as: base `.badge` styles first → color variants next → size variants last, so the size-specific padding/font-size correctly override the generic defaults.

---

## 🔑 Key Takeaways

- Map keys and class names must match exactly, including letter case — `Primary` and `primary` are treated as completely different identifiers.
- Only code that actually depends on a loop's variables belongs inside that loop; everything else should sit outside it, or it gets needlessly duplicated in the compiled CSS.
- When two CSS rules have equal specificity, **the one written later in the file wins** — so when combining "general defaults + specific overrides," the general styles need to come first and the overrides need to come last.
- Nested maps (a map whose values are themselves maps) require `map-get()` to be applied twice — once for the outer map, once for the inner one — to reach the actual value needed.

---

## ➡️ Next Up: Day 10

Pricing Table — the final review project, combining everything from Days 1–9 into one complete build.