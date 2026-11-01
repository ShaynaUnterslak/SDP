# UI_DIRECTION.md — Exam Visual Direction
## Editorial Utility / Swiss-Modernist
## Paper + ink + forest green

Use this unless the exam brief gives its own visual style.

Goal:
**intentional, readable, product-specific — not generic AI template.**

---

# PRINCIPLES

- left-aligned by default
- strong information hierarchy
- typography + spacing do most visual work
- neutral foundation + one accent colour
- restrained decoration
- cards only when content genuinely needs grouping
- product-specific layouts rather than repeated generic card grids

---

# PALETTE

- background/paper: `#F4F1E8`
- main surface: `#FCFBF7`
- ink/text: `#20231F`
- muted: `#666B63`
- forest accent: `#2F5D50`
- soft forest: `#DCE7E1`
- border: `#C9C5B9`
- warning/terracotta: `#B4553B`
- success: `#376B52`

If the domain strongly suggests another colour:
keep the principle **neutral + one deliberate accent**.

---

# TYPOGRAPHY

Avoid external font dependencies.

Headings:
`Georgia, 'Times New Roman', serif`

Body/UI:
`system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`

Code/data:
`ui-monospace, SFMono-Regular, Menlo, monospace`

---

# SHAPE / DEPTH

- radius generally 4–6px
- prefer borders over shadows
- shadows only when elevation has a real purpose
- no glass
- no backdrop blur as decoration
- no glowing blobs

---

# LAYOUT

- max width around 1100–1200px
- comfortable side padding
- left-aligned headings
- clear section rhythm
- compact readable forms/tables
- mobile collapses cleanly

Avoid:
- giant centred hero
- pill above hero
- centred CTA pair
- three identical icon cards
- endless bento cards
- cards nested in cards

---

# COMPONENTS

## Buttons
- primary: forest green
- secondary: paper/neutral + border
- destructive: terracotta/red
- modest radius
- obvious hover/focus
- no gradient

## Inputs
- visible label
- 1px border
- clear focus
- useful validation
- no gimmicks

## Tables/lists
- strong alignment
- subtle row separators
- do not wrap every row in a card

## Navigation
- simple
- clear active state
- no decorative pills unless genuinely appropriate

## Status
Use restrained badges only for actual status/category metadata.
Do not turn every label into a pill.

---

# REQUIRED PRODUCT STATES

Consider:
- empty
- loading
- error
- success
- disabled
- no-results

Use product-specific copy.

---

# GRAPHS

Only if rubric requires them or they are approved later.

Use:
- paper/white plot
- one accent + neutrals
- thin axes/grid
- direct labels where useful
- no 3D
- no rainbow palette
- no decorative gradients

---

# STRICT ANTI-GENERIC-AI LIST

Avoid unless explicitly required:
- purple-to-blue gradients
- gradient text
- glass/frosted panels
- glowing blobs
- giant centred marketing hero
- “✨ Introducing…” pills
- three identical feature cards
- emoji interface icons
- huge soft rounded corners everywhere
- excessive shadows
- fake metrics
- repetitive icon-title-description card patterns

---

# BUILD STRATEGY

During Core:
- establish shell
- palette
- typography
- spacing
- buttons/inputs
- table/list/card basics
- responsive container

During features:
- reuse those patterns

Near end:
- one dedicated polish pass

Do not repeatedly redesign individual screens.
