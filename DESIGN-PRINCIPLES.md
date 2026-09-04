# stevethetechguy.github.io — Design Principles

Source of truth for this site's visual system. `design-lead` reads this first and obeys it.

## Organizing idea

**A box of crayons.** Warm paper, thick outlines, solid offset shadows, and eight saturated
colors that rotate through the page so no two cards in a row are the same. The site should feel
like something made by hand and enjoyed, not a template filled in.

Personality is the point. Where a choice is between correct-and-flat or correct-and-fun, take fun.

## Color

One palette, no seasonal switching. Warm paper ground, near-black ink, and a crayon box of eight.

| Crayon | Light | Wash | Dark | Wash |
|---|---|---|---|---|
| Red | `#C0271C` | `#FCE3E0` | `#FF8A7A` | `#3B1B17` |
| Orange | `#AE5108` | `#FCEFE0` | `#FFA95C` | `#3B2610` |
| Gold | `#836400` | `#F6EECC` | `#E8C558` | `#332A0F` |
| Green | `#157A45` | `#E4F4EA` | `#5CD08D` | `#123020` |
| Teal | `#0E6E66` | `#D7EFEC` | `#4FD1C5` | `#0F2E2B` |
| Blue | `#1A5FC0` | `#DFE9FB` | `#7FAEF5` | `#17253F` |
| Purple | `#6B3AB8` | `#EAE1FA` | `#B79BF0` | `#27204A` |
| Pink | `#B32268` | `#FADFEB` | `#F58CC4` | `#3A1B2C` |

Ground `#FDF5EA` / `#12100D`, surface `#FFFFFF` / `#1C1916`, ink `#1B2220` / `#F3ECE1`.

**All 48 combinations verified at WCAG AA 4.5:1** — every crayon is legible as text on the
ground, on the surface, and on its own wash, in both themes. Lowest is 4.66.

**How crayons are assigned:** cards and rows take the next crayon from the box by
`nth-child(8n+k)`, so a grid reads as a spread of color rather than one accent repeated. The
crayon drives the card's offset shadow, its heading hover, its pills, and its date line. Nav
links each own a fixed crayon so the active page is always the same color.

## Type

| Role | Face | Fallback | Treatment |
|---|---|---|---|
| Headings | Fraunces 800 | Georgia, serif | `SOFT 70, WONK 1` — the soft, slightly odd cut |
| Body & UI | Nunito 400/600/700/800 | system-ui | 1.65, weight 600 for secondary text |
| Code | ui-monospace | Menlo | Crayon-washed background |

Fraunces with WONK on is the whole personality of the type. Never turn it off.

## Shape and depth

- Border `2.5px solid ink` on every raised object. Thick, like a marker outline.
- Radius `18px` on cards, `999px` on pills and buttons. Nothing sharp.
- Depth is a **solid offset shadow in the crayon color** — never a blur, never grey.
- Hover lifts by 3px and deepens the shadow to 8px. Transform and box-shadow only.
- A couple of elements sit at a slight rotation. Two is charming, ten is a mess.

## Motion

Hover only, 0.12s, transform and box-shadow. Nothing on load, nothing on scroll.
`prefers-reduced-motion: reduce` disables every transition — but static rotations stay, because
a tilt is not motion.

## Content model

Nothing is written in HTML. Essays are markdown in `_posts/`, projects and books are YAML in
`_data/`, and identity is `_config.yml`.

**A section with no data renders a designed empty state that says exactly which file to edit** —
never "coming soon", never a placeholder entry.

## Voice

First person, plain, warm. Contractions are fine. No adjectives applied to myself.

> **Before:** "Passionate full-stack developer with a strong foundation in modern web technologies."
> **After:** "I build backend services — mostly Java and Spring, with Python when the problem calls for it."

> **Before:** "Projects coming soon!"
> **After:** "Projects come from `_data/projects.yml`. Add a name, a sentence, and a link, push it, and it shows up here."

## Non-negotiables

- Every color token declared on bare `:root` before any theme block
- All 48 crayon/surface combinations verified at 4.5:1 by calculation
- Visible focus states; a skip link before the nav
- Empty states name the file to edit
- Real content only — no lorem, no invented projects, no fake reading list
- Page fully legible at rest, before any scroll or hover

## Deliberately not

- Seasonal theming or a theme picker — removed on purpose; a new look each season is done by hand
- A single accent color, which is what made the earlier version feel corporate
- Blurred drop shadows and grey depth
- Skill bars, percentage ratings, star self-assessments
- Hero that fills the viewport before any content
- "Passionate", "ninja", "rockstar", "guru"
