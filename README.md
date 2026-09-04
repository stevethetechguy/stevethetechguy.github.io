# stevethetechguy.github.io

My site. Built with Jekyll, hosted on GitHub Pages. Push to `master` and it rebuilds itself
in about a minute.

## Adding things

You never need to touch HTML. Everything lives in markdown or YAML.

| I want to... | Edit this |
|---|---|
| Write an essay | New file in `_posts/` named `YYYY-MM-DD-title.md` |
| Add a project | `_data/projects.yml` |
| Add a book | `_data/reading.yml` |
| Change my bio | `about.md` |
| Change my name, tagline, email | `_config.yml` |

### Writing an essay

Create `_posts/2026-09-15-what-i-learned.md`:

```markdown
---
layout: post
title: What I learned building a trading bot
blurb: One sentence that shows up in the list.
tags: [trading, python]
---

Your first paragraph. Just write markdown from here.

## A heading

More writing.
```

The date in the filename sets the publish date. Anything in `_drafts/` is not published.

### Adding a project

```yaml
- name: Ticketing Gateway System
  what: One sentence on what it does and why you built it.
  link: https://github.com/stevethetechguy/Ticketing-Gateway-System
  tags: [Java, Spring, Microservices]
  featured: true      # also shows on the home page
```

### Adding a book

```yaml
- title: The Pragmatic Programmer
  author: Hunt and Thomas
  status: current     # current | finished | queued
  note: Why you picked it up.
  finished: 2026-08   # only for finished books
```

## Design

The visual system is written down in `DESIGN-PRINCIPLES.md`. The short version: chunky
outlines, solid offset shadows, a box of eight crayon colors that rotate across cards, Fraunces
for headings and Nunito for everything else. Every color is contrast-checked.
