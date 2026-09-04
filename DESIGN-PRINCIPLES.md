# stevethetechguy.github.io — Design Principles

Source of truth for this site's visual system. `design-lead` reads this first and obeys it.

## Organizing idea

**The site is an almanac — one publication that reissues itself every season.**

An almanac is the rare format that is *natively* seasonal: it prints the celestial dates, records
what happened, and lists what is worth attending to now. That gives the seasonal theming a reason to
exist beyond decoration, and it gives every section a vocabulary — editions, entries, records,
observances — instead of the usual portfolio nouns.

The season is not a skin. It is the edition.

## Season model

**Astronomical**, switching on the exact equinox and solstice instant. Verified UTC moments for 2026:

| Transition | Instant (UTC) | Season begins |
|---|---|---|
| March equinox | 2026-03-20 14:46 | Spring |
| June solstice | 2026-06-21 08:25 | Summer |
| September equinox | 2026-09-23 00:05 | Autumn |
| December solstice | 2026-12-21 20:50 | Winter |

Instants are stored in UTC and converted by the browser, so the switch is correct in any timezone.
In Dallas the September equinox lands at 7:05 PM CDT on the 22nd.

Years other than 2026 fall back to conventional dates (Mar 20, Jun 21, Sep 22, Dec 21 at the same
times). **Refresh the exact table annually** — the fallback drifts by up to a day.

A `?season=` override renders any edition on demand. It never persists and never affects a normal
visitor.

## Color

Eight palettes: four seasons, each with a light and a dark rendering of the same hue family. Same
identity, two grounds — never an inversion. Every text token clears WCAG AA 4.5:1 against both
`--ground` and `--surface`, verified by calculation.

| Season | Light accent | Dark accent | Family | Min ratio |
|---|---|---|---|---|
| Spring | `#2A6238` moss | `#6DBE7C` | green, blossom pink second | 5.09 |
| Summer | `#0B5F79` deep sea | `#5CBFDD` | bleached warm ground, cool accent | 4.97 |
| Autumn | `#8C2F1E` oxblood | `#E08765` | oxblood and dark ochre, never terracotta | 5.18 |
| Winter | `#1F4E79` slate blue | `#7FB4DE` | cold blue-grey, no warmth | 5.20 |

Seven tokens per palette: `--ground`, `--surface`, `--ink`, `--ink2`, `--line`, `--accent`,
`--accent2`. Nothing outside that set is ever colored.

## Type

| Role | Face | Fallback | Treatment |
|---|---|---|---|
| Masthead | Instrument Serif 400 | Georgia, serif | Large, tight, high contrast |
| Section head | Instrument Serif 400 | Georgia, serif | Sentence case |
| Body | Karla 400/500 | system-ui | 1.6, max 66ch |
| Data & labels | Azeret Mono 400/600 | ui-monospace | Uppercase, 0.14em tracking, 10–12px |

The serif carries the almanac; the grotesque carries the reading; the mono carries anything with a
number in it. No role ever borrows another's face.

## Layout

- Single column, `680px` measure for reading, widening to `1100px` for records and grids
- Sections separated by a full-width rule and a mono section marker, in almanac fashion
- Radius `0`. Almanacs are printed, not rounded.
- Entries are rows with a hanging label, not cards

## Motion

Almost none. The season change is the only real transition, and it is a repaint, not an animation.

| Element | Property | Duration |
|---|---|---|
| Link and row hover | `color`, `background` | 0.12s |
| Season repaint | CSS custom properties | 0.3s ease |

Nothing on load. Nothing on scroll. `prefers-reduced-motion: reduce` disables all of it.

## Voice

First person, plain, no self-promotion adjectives. State the thing, not a claim about the thing.
An almanac records; it does not sell.

> **Before:** "Passionate full-stack developer with a strong foundation in modern web technologies."
> **After:** "I build backend services in Java and Spring, and I am working through reinforcement
> learning applied to markets."

> **Before:** "Check out my awesome projects below!"
> **After:** "Twelve public repositories. The four below are the ones worth reading."

## Non-negotiables

- Every content value comes from a single `DATA` object at the top of the script
- A section with no data **does not render** — never a placeholder, never "coming soon"
- Every text token verified at 4.5:1 in all eight palettes
- The page is fully legible at rest, in whichever edition is current
- Visible focus states; the season override reachable by keyboard
- Real repository data, pulled from the GitHub API, never hand-invented

## Deliberately not

- Skill bars, percentage ratings, or star-rating self-assessments
- A hero occupying the viewport before any content appears
- Animated backgrounds, particles, parallax, typewriter effects
- Terracotta-and-cream autumn — the most predictable seasonal palette there is
- Emoji as section markers
- "Passionate", "ninja", "rockstar", "guru", or any adjective applied to myself
