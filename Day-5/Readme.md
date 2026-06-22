# Day 5 — Final Mini Project: Portfolio Landing Page

## 📅 What I Built Today

A complete **portfolio landing page** with three sections — Navbar, Hero, and a Cards grid — combining every SASS concept learned across Days 1 to 4 into one real project, instead of isolated examples.

---

## 🧩 Concepts Applied

| Concept | Where It Was Used |
|---|---|
| **Variables** | All colors (`$bg-color`, `$text-color`, `$heading-color`, `$border-color`, `$dark-color`) stored in `_variables.scss` |
| **Nesting + `&`** | Navbar structure (`nav > .logo`, `nav > ul > li > a`), Hero section (`h1`, `p`, `button`) |
| **Partials + `@use`** | Split code into `_variables.scss` and `_mixins.scss`, imported into `style.scss` with namespacing (`as *`) |
| **Mixins** | `flex-center`, `flex-between` (layout helpers), `pr` (button padding/border helper) |
| **Mixins importing from other partials** | Learned that `_mixins.scss` needed its own `@use './variables' as *;` to access color variables — partials don't automatically share scope with each other |
| **`%placeholder` + `@extend`** | `%card-base` holds shared card styles (padding, border-radius, border), extended by `.card` |
| **Map + `@each`** | `$card-colors` map (html, css, js → orange, dodgerblue, gold) looped with `@each` to generate `.card-html`, `.card-css`, `.card-js` with unique border and heading colors |

---

## 🐞 Bugs I Hit & Fixed

1. **Mixin not applying** — had commented out `@include pr;` by mistake, and the mixin itself referenced `$border-color` without importing the variables partial into `_mixins.scss`.
2. **Map name mismatch** — wrote `$card-color` in the `@each` loop instead of the actual map name `$card-colors`. Confirmed that variable/map names must match *exactly*, even a missing letter breaks it.
3. **Wrong property shorthand** — tried writing `border-color: 2px solid $color;`, not realizing `border-color` only accepts a color value, not the full `border` shorthand. Fixed by either using `border-color: $color;` alone, or `border: 2px solid $color;` if replacing the whole property.

---

## 🔑 Key Takeaways

- Real projects mix concepts together constantly — a single component (like the card) used variables, a placeholder, a map, and `@each` all at once.
- Partial files are independent scopes. If one partial needs a variable defined in another, it must `@use` that partial itself — importing into the main `style.scss` does not automatically share access between partials.
- Small naming mistakes (mismatched map names, wrong property names) are the most common source of bugs — careful, exact naming matters more in SASS than expected.
- Building one complete project end-to-end made the concepts "stick" far more than isolated practice examples did.

---

## ➡️ Next Up: Days 6–10 — Extra Practice Projects

Five more small practice projects (not large builds) to keep reinforcing Days 1–4's concepts — variables, nesting, partials, mixins, functions, operators, `@extend`, and control directives — until they feel second nature.