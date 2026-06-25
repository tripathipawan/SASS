# Day 8 — Practice Project: Testimonial Cards Section

## 📅 What I Built Today

A **testimonial cards section** — a heading and a 3-column grid of customer review cards, each with a quote, author name, and role — built to reinforce Day 3's concepts: Functions, Operators, and `@extend` / Placeholders.

---

## 🧩 Concepts Reinforced

| Concept | Where It Was Used |
|---|---|
| **Functions (`@function`)** | Created a `spacing($multiplier)` function (`8px * $multiplier`) and used it consistently for every padding, margin, gap, and border-radius value across the section |
| **Operators** | Calculated the `.role` text's font-size using subtraction (`2rem - 1.2rem`) instead of writing the final value directly |
| **`%placeholder` + `@extend`** | Created `%card-base` holding all shared card styles (border, padding, flex layout, transition), then extended it into `.testimonial-card` |
| **Mixins** | Reused `flex-center` for centering layouts (body, section, individual cards) |
| **Nesting** | `.testimonials > h1`, `.testimonial-grid > .testimonial-card > .author/.role`, plus `&:hover` for the card's hover effect |

---

## 🐞 What I Initially Missed (First Attempt)

My first version of this project used hardcoded pixel values everywhere and didn't use a function, a placeholder, or any operator — even though the card was visually complete and looked good. This was a good reminder that **a finished-looking UI doesn't automatically mean the day's specific practice goal was met** — the visual result and the concept being practiced are two different things to check.

After revisiting it:
- Replaced every hardcoded spacing value with calls to the `spacing()` function.
- Pulled the repeated card styles out into a `%card-base` placeholder and extended it.
- Added one operator-based calculation instead of a flat value, just to keep the syntax fresh.

---

## 🔑 Key Takeaways

- It's easy to build something that *looks* right while skipping the actual concept being practiced — worth double-checking against the day's specific goals, not just the final visual output.
- A single spacing function used everywhere makes the whole layout's rhythm easy to scale or adjust later by changing just the base multiplier values.
- Even with only one card variant (unlike Day 5's three differently-colored cards), placeholders are still worth using for practice — the benefit becomes more obvious once there's more than one thing extending from it.

---

## ➡️ Next Up: Day 9

Badge / Tag Generator — practicing Maps, `@each`, and `@for` further.



<!-- Day 8 complete - Testimonial Cards (Functions, Operators and Extend practice) -->