# shipui Foundation (v0.1) Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Ship installable shipui v0.1 — directory skeleton, SKILL.md with manifesto + 10-step workflow, and the pre-delivery QA checklist. After this plan, the user can install shipui into Claude Code and invoke it to get the workflow, even if the deep reference files (tokens, motion, etc.) come in follow-up plans.

**Architecture:** Markdown-only skill with thin SKILL.md router pattern. No code dependencies. Lives at `/Users/feli24a/Desktop/Proyectos/skills/` as a standalone repo (publishable). Follows the structure proven by `ui-ux-pro-max`, `awesome-design-md`, and `frontend-design`.

**Tech Stack:** Markdown, YAML frontmatter, MIT License. No runtime dependencies for v0.1.

**Spec reference:** `docs/superpowers/specs/2026-05-27-shipui-design.md`

**Scope of this plan:** Spec phases 1 + 2 only (Skeleton + Core Workflow). Follow-up plans will cover:
- `shipui-stack-foundation` (Phase 3-4): tokens + scout + contract references
- `shipui-quality` (Phase 5-7): motion + a11y + performance references
- `shipui-aesthetic` (Phase 6 + 10): aesthetic-direction + brand-inspiration + styles-catalog references
- `shipui-tooling` (Phase 8): data files + Python scripts
- `shipui-distribution` (Phase 9): plugin packaging + first release

---

## File Structure

After this plan, the repo at `/Users/feli24a/Desktop/Proyectos/skills/` will look like:

```
skills/
├── shipui/
│   ├── SKILL.md                              # Manifesto + 10-step workflow + router (created)
│   └── references/
│       └── pre-delivery-checklist.md         # Non-negotiable QA gates (created)
├── README.md                                  # Public-facing pitch (created)
├── LICENSE                                    # MIT (created)
├── .gitignore                                 # Standard ignores (created)
└── docs/
    └── superpowers/
        ├── specs/2026-05-27-shipui-design.md  # (already exists from brainstorming)
        └── plans/2026-05-27-shipui-foundation.md  # (this file)
```

Each file's responsibility:

- **`shipui/SKILL.md`** — The entry point Claude loads when the skill is invoked. Contains the manifesto, the opinionated stack, the 10-step workflow with "load reference X at step Y" pointers, and tooling notes. Must be self-contained for v0.1 — references that don't exist yet are mentioned but the workflow steps still describe their intent.
- **`shipui/references/pre-delivery-checklist.md`** — The QA gate referenced by step 9. The one reference file that ships in v0.1 because it's the most actionable and the least dependent on the others.
- **`README.md`** — Public-facing repo pitch. What shipui is, who it's for, how to install, what makes it different from `frontend-design`.
- **`LICENSE`** — MIT, 2026, Felipe Arias.
- **`.gitignore`** — Standard ignores for a docs/skill repo (`.DS_Store`, `node_modules/`, IDE files).

---

## Task 1: Create the directory skeleton

**Files:**
- Create: `/Users/feli24a/Desktop/Proyectos/skills/shipui/`
- Create: `/Users/feli24a/Desktop/Proyectos/skills/shipui/references/`

- [ ] **Step 1: Confirm working directory exists and is empty besides docs/**

Run:
```bash
ls -la /Users/feli24a/Desktop/Proyectos/skills/
```

Expected: Should show only `docs/` (from brainstorming output). No `shipui/`, no `README.md`, no `LICENSE` yet.

- [ ] **Step 2: Create the shipui skill folder and its references subfolder**

Run:
```bash
mkdir -p /Users/feli24a/Desktop/Proyectos/skills/shipui/references
```

- [ ] **Step 3: Verify structure**

Run:
```bash
find /Users/feli24a/Desktop/Proyectos/skills/shipui -type d
```

Expected output:
```
/Users/feli24a/Desktop/Proyectos/skills/shipui
/Users/feli24a/Desktop/Proyectos/skills/shipui/references
```

No commit yet — empty folders aren't tracked by git. Commit happens after Task 2 writes the first file.

---

## Task 2: Write SKILL.md (manifesto + 10-step workflow)

**Files:**
- Create: `/Users/feli24a/Desktop/Proyectos/skills/shipui/SKILL.md`

- [ ] **Step 1: Write SKILL.md with the full content below**

Write this exact content to `/Users/feli24a/Desktop/Proyectos/skills/shipui/SKILL.md`:

````markdown
---
name: shipui
description: Opinionated web design and frontend skill — ships production-grade interfaces with Next.js + Tailwind v4 + shadcn/ui + Motion. Enforces a 10-step workflow (brief, aesthetic direction, brand inspiration, design tokens, component scout, contract, implementation, motion, QA, polish). Use when building, designing, reviewing, or refactoring web UI — landing pages, dashboards, components, SaaS, e-commerce, admin panels, portfolios, blogs. Web-only — for mobile UI, use platform-specific skills.
---

# shipui

> **shipui ships production-grade web interfaces.** Every design decision is intentional. Every value comes from a token. Every component has a contract. Every animation has a reason. Every interface is accessible by default. We don't ship "AI-generated" aesthetics — we ship interfaces that someone will remember.
>
> If you can't answer "why this color, why this spacing, why this animation," you're not ready to ship. Go back one step.

---

## The Stack (non-negotiable)

| Layer | Choice |
|-------|--------|
| Framework | Next.js (App Router) |
| UI runtime | React 19 |
| Styling | Tailwind CSS v4 (tokens via `@theme`) |
| Components | shadcn/ui (built on Radix) |
| Motion | Motion (motion.dev — successor to framer-motion) |
| Icons | Lucide React |
| Forms | React Hook Form + Zod |
| Data | Supabase |
| Hosting | Vercel |
| Fonts | next/font + Google Fonts |

If the user's existing project uses a different stack (Vue, Svelte, Remix, etc.), respect it but warn that shipui's guarantees do not apply — fall back to a stack-appropriate skill.

---

## The 10-Step Workflow

Follow these in order. Each step has a reference file with depth — load it when you reach the step, not before. Until a reference file exists in `references/`, follow the inline guidance below.

### 1. Brief

Extract from the user's request:
- **Product type:** SaaS, e-commerce, landing page, dashboard, portfolio, blog, marketing site, admin panel
- **Audience:** consumers, prosumers, enterprise, technical, mass-market
- **Tone keywords:** minimal, bold, playful, professional, elegant, brutal, soft, premium, industrial
- **Technical constraints:** must support X browsers, dark mode required, SEO-critical, etc.

Output: three sentences max. If the user gave only a vague brief, ask one clarifying question — never assume.

### 2. Aesthetic direction
**Load:** `references/01-aesthetic-direction.md` *(coming in shipui-aesthetic plan)*

Commit to ONE bold direction. Examples: brutally minimal, maximalist chaos, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian.

The "AI slop" anti-patterns are non-negotiable: no overused fonts (Inter/Roboto/Arial as the only choice), no clichéd purple-gradient-on-white, no predictable layouts, no cookie-cutter component patterns.

### 3. Brand inspiration
**Load:** `references/02-brand-inspiration.md` *(coming in shipui-aesthetic plan)*

Pick one of the 58 brand references (Linear, Vercel, Stripe, Apple, Notion, Pinterest, Cursor, Raycast, etc.) that matches the aesthetic direction, OR justify why this project goes from scratch. "From scratch" requires a strong reason.

### 4. Design tokens
**Load:** `references/03-design-tokens.md` *(coming in shipui-stack-foundation plan)*

Define the **full token set BEFORE writing any component code**:
- Color palette (50–950 scales for each, with semantic aliases: primary, accent, destructive, muted, foreground, background)
- Dark mode mirror
- Typography scale (display, h1–h6, body, caption — with line-height)
- Spacing scale (4pt grid: 4, 8, 12, 16, 24, 32, 48, 64, 96, 128)
- Shadow elevation scale (sm, md, lg, xl, 2xl)
- Radius scale (sm, md, lg, xl, full)
- Motion duration tokens (instant 100ms, fast 200ms, base 300ms, slow 500ms)
- Motion easing tokens (ease-out for enter, ease-in for exit, ease-in-out for emphasis)

Tokens live in `app/globals.css` inside `@theme` (Tailwind v4 syntax). No hardcoded values anywhere else.

### 5. Component scout
**Load:** `references/04-component-scout.md` *(coming in shipui-stack-foundation plan)*

**Search order before building from scratch:**
1. `mcp__21st-dev-magic__21st_magic_component_builder` / `_inspiration` (if MCP available)
2. shadcn/ui — [ui.shadcn.com/components](https://ui.shadcn.com/components)
3. Radix UI primitives (headless, accessible)
4. Aceternity UI (animated, modern)
5. Magic UI (effects, animations)
6. Build from scratch — ONLY if none of the above is ≥80% of what's needed

The 80% rule: if an existing component covers 80% or more of the requirement, adapt it. Adapting means tweaking styles, adding a prop, or composing two existing components. It does NOT mean rewriting the core logic.

### 6. Component contracts
**Load:** `references/05-component-contract.md` *(coming in shipui-stack-foundation plan)*

For **every new component**, write a contract comment block at the top of the file BEFORE writing any implementation:

```
// Contract: ComponentName
// Props: [list each prop with type and required/optional]
// Variants: [all visual variants — e.g., size: sm | md | lg]
// States: default | hover | focus | active | disabled | loading | error | empty
// Accessibility: ARIA role, keyboard interaction, contrast requirement
// Responsive: behavior at sm (640) / md (768) / lg (1024) / xl (1280) breakpoints
```

All states must be accounted for — a missing state is a bug. Accessibility is part of the contract, not a post-implementation checkbox.

### 7. Implementation
**Load:** `references/06-tailwind-shadcn.md` *(coming in shipui-stack-foundation plan)*

Build with Tailwind v4 + shadcn idioms:
- Server Components by default — Client Components only when needed (state, effects, browser APIs, event handlers)
- Zero hardcoded values — every property references a token (`bg-primary`, `text-muted-foreground`, `p-4`, `rounded-lg`)
- Tailwind utilities for layout/spacing — `@apply` only when extracting reusable patterns
- shadcn primitives extended via composition, not forked
- Dark mode via `data-theme` or `class` strategy — set in tokens, used via semantic colors

### 8. Motion layer
**Load:** `references/07-motion.md` *(coming in shipui-quality plan)*

Before adding any animation, answer:
1. **Why?** Feedback, transition, or emphasis. If none, don't animate.
2. **How long?** Micro (100–200ms), standard (200–400ms), complex (400–600ms).
3. **Reduced motion?** Gate with `useReducedMotion()` from Motion or `@media (prefers-reduced-motion)`.

Animate only `transform` and `opacity`. Never `width`, `height`, `margin`, `padding`, `top`, `left` — they trigger layout reflow. Linear easing is forbidden (mechanical). Use `ease-out` for enter, `ease-in` for exit.

### 9. QA pass
**Load:** `references/pre-delivery-checklist.md`

Run the checklist. **Every box must be checked.** If any item fails, go back to the relevant workflow step. No exceptions.

The checklist covers: visual quality, design token enforcement, light/dark mode, responsive behavior, interaction feedback, motion, WCAG AA accessibility, performance (Core Web Vitals).

### 10. Polish
**Load:** `references/10-styles-catalog.md` *(coming in shipui-aesthetic plan)*

Add the distinctive details that make the interface memorable: a custom cursor, a noise texture overlay, a typographic flourish, a scroll-triggered choreography, an unexpected micro-interaction. One memorable detail beats five forgettable ones.

---

## When to skip steps

**Never skip:** 4 (tokens), 5 (scout), 6 (contracts), 8 (motion check), 9 (QA). These are non-negotiable gates.

Steps 1–3 can be compressed to 3 lines each for small additions to an existing project with established brand and direction.

Step 10 (polish) is the only fully optional step — skip for internal tools where memorability doesn't matter.

---

## Tooling

*(Coming in shipui-tooling plan — Phase 8 of the spec)*

When `scripts/search.py` and `scripts/check.py` exist, the workflow gains:

```bash
# Get a starter design system for a brief
python3 scripts/search.py --design-system "wellness spa" --industry beauty

# Search the curated catalogs
python3 scripts/search.py --palette --vibe minimal --industry saas
python3 scripts/search.py --fonts --vibe editorial
python3 scripts/search.py --style glassmorphism

# Lint the working tree before delivery
python3 scripts/check.py ./src
```

Until those exist, run the workflow manually and use the checklist in step 9 as the lint.

---

## Out of scope

shipui is **web-only**. It does not produce code for:
- iOS / SwiftUI / UIKit / Liquid Glass — use platform-specific skills
- Android / Jetpack Compose
- React Native or Flutter
- Vue, Svelte, Solid, Qwik (the stack is opinionated to React/Next.js)
- CSS-in-JS (styled-components, emotion) — Tailwind only
- Backend, database, API design — use `backend-patterns`, `postgres-patterns`, etc.

---

## Companion skills

- `frontend-design` (the official plugin) — pair with shipui for additional aesthetic depth when designing from scratch. shipui is the production playbook; `frontend-design` is the aesthetic muse.
- `awesome-design-md` — the source of the 58 brand references shipui's step 3 draws from.
- `awesome-design-md`'s files at `~/.claude/references/awesome-design-md/design-md/<brand>/DESIGN.md` are the authoritative brand specs.
````

- [ ] **Step 2: Verify the file was written correctly**

Run:
```bash
head -20 /Users/feli24a/Desktop/Proyectos/skills/shipui/SKILL.md
```

Expected: First lines show `---`, `name: shipui`, `description: ...`, the `---`, blank line, then `# shipui`.

- [ ] **Step 3: Verify YAML frontmatter is parseable**

Run:
```bash
python3 -c "import yaml, re; content = open('/Users/feli24a/Desktop/Proyectos/skills/shipui/SKILL.md').read(); fm = re.match(r'^---\n(.*?)\n---', content, re.DOTALL); print(yaml.safe_load(fm.group(1)))"
```

Expected: Prints a dict with `name` and `description` keys, no errors.

If `yaml` module is missing: `pip3 install pyyaml` then retry.

- [ ] **Step 4: Verify no placeholders remain**

Run:
```bash
grep -nE 'TBD|TODO|FIXME|\.\.\.\.|\[placeholder\]' /Users/feli24a/Desktop/Proyectos/skills/shipui/SKILL.md
```

Expected: No output (no placeholders). The phrase `*(coming in shipui-* plan)*` is intentional and is not a placeholder — it's a roadmap reference.

- [ ] **Step 5: Commit**

```bash
cd /Users/feli24a/Desktop/Proyectos/skills && git init 2>/dev/null; git add shipui/SKILL.md docs/ && git commit -m "feat: add shipui SKILL.md with 10-step workflow"
```

If the directory is not yet a git repo, `git init` runs first. If it already is, init is a no-op.

---

## Task 3: Write pre-delivery-checklist.md

**Files:**
- Create: `/Users/feli24a/Desktop/Proyectos/skills/shipui/references/pre-delivery-checklist.md`

- [ ] **Step 1: Write the checklist file with the full content below**

Write this exact content to `/Users/feli24a/Desktop/Proyectos/skills/shipui/references/pre-delivery-checklist.md`:

````markdown
# Pre-Delivery Checklist

The non-negotiable QA gates before declaring a UI "done". **Every box must be checked.** If any item fails, return to the relevant workflow step in `SKILL.md` and fix it.

This is referenced by step 9 of the shipui workflow.

---

## Visual quality

- [ ] No emoji used as an icon — use SVG (Lucide React first, Heroicons as fallback)
- [ ] All icons drawn from a single consistent set (no mixing Lucide with Heroicons in the same project)
- [ ] Brand logos verified from [Simple Icons](https://simpleicons.org/) — no guessed paths or wrong colors
- [ ] No layout-shifting hover states (use color/opacity/border changes, not `scale` that pushes neighbors)
- [ ] Theme colors used directly (`bg-primary`, `text-foreground`), not wrapped in `var()` arbitrary values
- [ ] Consistent icon sizing — fixed viewBox 24×24, sized with `size-4` / `size-5` / `size-6`

## Design tokens (the pixel-enforcer rule)

- [ ] No `#[0-9a-fA-F]{3,8}` (hex colors) in component files — only in the token file
- [ ] No `rgb(`, `rgba(`, `hsl(`, `hsla(` in component files
- [ ] No hardcoded `px` / `rem` values in `style={{}}` props
- [ ] No magic spacing — every margin/padding/gap comes from the 4pt scale (`4, 8, 12, 16, 24, 32, 48, 64, 96, 128`)
- [ ] New colors are added to `@theme` in `app/globals.css` BEFORE being referenced
- [ ] No inline styles for anything that has a Tailwind utility — `style={{}}` is reserved for dynamic computed values only

## Light / dark mode

- [ ] Both modes tested visually
- [ ] Text contrast ≥ 4.5:1 in both modes (verified with browser DevTools or Stark)
- [ ] Glass / transparent elements remain visible in light mode (`bg-white/80` minimum, never `bg-white/10`)
- [ ] Borders visible in both modes (`border-border` token, not `border-white/10`)
- [ ] Dark mode has its own intentional palette — it's not just inverted colors
- [ ] Muted text passes contrast: light uses `#475569` (slate-600) minimum, never `gray-400`

## Responsive

- [ ] Tested at viewports: 375px (mobile), 768px (tablet), 1024px (laptop), 1440px (desktop)
- [ ] No horizontal scroll at any tested viewport
- [ ] Touch targets ≥ 44×44px on mobile
- [ ] Floating navbars have edge spacing (`top-4 left-4 right-4`), not flush against the viewport
- [ ] Content has padding accounting for fixed/floating navbar height
- [ ] Fixed elements account for iOS safe areas (notch, dynamic island, home indicator)
- [ ] Consistent `max-width` containers across pages — no mixing `max-w-6xl` here and `max-w-7xl` there

## Interaction

- [ ] All clickable elements have `cursor-pointer` (cards, custom buttons, anything that responds to click)
- [ ] Hover states provide visual feedback — color, shadow, border, or opacity change
- [ ] Focus rings visible on keyboard navigation — never `outline-none` without a custom focus style
- [ ] Transitions are 150–300ms — never instant, never >500ms
- [ ] Buttons disabled and show loading state during async operations
- [ ] Error messages appear near the problem field, in plain language (not "Error 400")
- [ ] Forms preserve user input on validation failure — never wipe filled fields

## Motion

- [ ] Every animation has a documented reason: feedback, transition, or emphasis
- [ ] Only `transform` and `opacity` are animated — no `width`, `height`, `margin`, `padding`, `top`, `left`
- [ ] `prefers-reduced-motion` respected — gated via `useReducedMotion()` from Motion, or CSS `@media (prefers-reduced-motion: reduce)`
- [ ] Easing matches direction: `ease-out` for elements entering, `ease-in` for elements leaving, `ease-in-out` for emphasis
- [ ] No linear easing on UI motion (mechanical/cheap feeling)
- [ ] No animation longer than 600ms — except a single choreographed page-load sequence
- [ ] No motion fatigue: not everything moves. Animation is reserved for high-impact moments

## Accessibility (WCAG AA)

- [ ] All meaningful images have descriptive `alt` text; decorative images use `alt=""`
- [ ] All form inputs have an associated `<label htmlFor="...">` — placeholder is not a label
- [ ] Icon-only buttons have `aria-label` or `<span className="sr-only">`
- [ ] Tab order matches visual reading order
- [ ] Color is never the only indicator — also use icon, text, position, or pattern
- [ ] Focus visible on every interactive element (including custom-styled components)
- [ ] Headings are semantic and in order (`h1` → `h2` → `h3`, no skipping)
- [ ] Modals trap focus while open and restore it to the trigger on close
- [ ] Dynamic content announces to screen readers via `aria-live="polite"` or `aria-live="assertive"`
- [ ] Skip-to-content link present on long pages

## Performance (Core Web Vitals)

- [ ] All images use `next/image` with explicit `width` and `height` (prevents CLS)
- [ ] All fonts use `next/font` from Google Fonts — never `<link>` tags
- [ ] Heavy components lazy-loaded via `next/dynamic` or `React.lazy()` + `Suspense`
- [ ] Server Components used by default — Client Components only when needed (`'use client'` justified by state, effects, or browser APIs)
- [ ] No unused dependencies — run `npx depcheck` and remove anything unused
- [ ] LCP < 2.5s, INP < 200ms, CLS < 0.1 (measured via Lighthouse or `web-vitals` package)
- [ ] Bundle size budget respected — Next.js page bundle < 200kb gzipped for marketing pages

## Final smoke test

- [ ] Run production build locally: `pnpm build && pnpm start`
- [ ] Click every interactive element on every page
- [ ] Submit every form: happy path AND error path
- [ ] Open in Chrome, Safari, Firefox at minimum
- [ ] Run Lighthouse — score ≥ 95 in Performance, Accessibility, Best Practices, SEO

---

**If ANY box is unchecked, the work is not done.** Return to the relevant step in `SKILL.md` and fix the underlying issue. Do not "TODO" your way past a failing check.
````

- [ ] **Step 2: Verify file written**

Run:
```bash
wc -l /Users/feli24a/Desktop/Proyectos/skills/shipui/references/pre-delivery-checklist.md
```

Expected: ~95 lines (give or take a few).

- [ ] **Step 3: Verify no placeholders**

Run:
```bash
grep -nE 'TBD|TODO|FIXME|\.\.\.\.|\[placeholder\]' /Users/feli24a/Desktop/Proyectos/skills/shipui/references/pre-delivery-checklist.md
```

Expected: No output.

- [ ] **Step 4: Verify all checklist items have actionable rules (no vague "ensure good quality" items)**

Manually scan the file. Every `- [ ]` item should describe a specific, verifiable rule. Reject anything like "ensure quality is good" or "make sure it looks nice".

- [ ] **Step 5: Commit**

```bash
cd /Users/feli24a/Desktop/Proyectos/skills && git add shipui/references/pre-delivery-checklist.md && git commit -m "feat: add pre-delivery checklist (step 9 QA gate)"
```

---

## Task 4: Write README.md (public-facing pitch)

**Files:**
- Create: `/Users/feli24a/Desktop/Proyectos/skills/README.md`

- [ ] **Step 1: Write README.md with the content below**

Write this exact content to `/Users/feli24a/Desktop/Proyectos/skills/README.md`:

````markdown
# shipui

> An opinionated web design and frontend skill for [Claude Code](https://claude.com/claude-code). Ships production-grade interfaces with Next.js + Tailwind v4 + shadcn/ui + Motion.

shipui is the **production playbook**: a 10-step workflow that takes a brief from "build me a landing page" to "shipped, accessible, performant, and memorable."

If [`frontend-design`](https://github.com/anthropics/claude-code) is the aesthetic muse that says *"commit to a bold direction"*, shipui is the playbook that says *"now ship it with tokens, contracts, motion discipline, and a QA gate you can't skip."*

---

## What you get

**A 10-step workflow** enforced every time the skill is invoked:

1. **Brief** — extract product, audience, tone, constraints
2. **Aesthetic direction** — commit to one bold direction (no hedging)
3. **Brand inspiration** — pick from 58 curated brand specs
4. **Design tokens** — full token set BEFORE any component code
5. **Component scout** — search shadcn / Radix / 21st.dev / Aceternity before building
6. **Component contracts** — props, states, a11y, responsive defined upfront
7. **Implementation** — Tailwind v4 + shadcn idioms, zero hardcoded values
8. **Motion layer** — purposeful animations with reduced-motion fallbacks
9. **QA pass** — non-negotiable pre-delivery checklist
10. **Polish** — distinctive details that make it memorable

**An opinionated stack** — Next.js (App Router), React 19, Tailwind v4, shadcn/ui, Motion (motion.dev), Lucide React, React Hook Form + Zod, Supabase, Vercel. shipui doesn't ask "what framework?" — it ships.

**A pre-delivery checklist** that covers visual quality, design tokens, light/dark mode, responsive behavior, interaction feedback, motion discipline, WCAG AA accessibility, and Core Web Vitals performance.

---

## Who it's for

- Freelancers shipping client web work who want a consistent, high-quality output without re-deciding the stack every project.
- Solo founders building SaaS / e-commerce / landing pages who want production-grade UI without a designer.
- Agencies wanting a shared playbook so every developer ships the same caliber of work.
- Anyone tired of "AI-generated" aesthetics that all look the same.

If you want to use Vue, Svelte, Remix, or any non-React stack — shipui is not for you. The opinion is the product.

---

## Install

### Option 1 — Copy into your Claude Code skills

```bash
cp -r shipui ~/.claude/skills/
```

Restart Claude Code. Invoke with: *"use the shipui skill to build a landing page for X"*.

### Option 2 — Install as a plugin

*(Coming soon)*

---

## Status

**v0.1 — Foundation.** Installable. SKILL.md with full 10-step workflow. Pre-delivery checklist gate.

**Coming next:**
- v0.2 — Design tokens + component scout + component contract references
- v0.3 — Motion + accessibility + performance references
- v0.4 — Aesthetic direction + brand inspiration + styles catalog references
- v0.5 — Python search & lint tooling (`scripts/search.py`, `scripts/check.py`)
- v1.0 — Plugin packaging, public release

See `docs/superpowers/specs/2026-05-27-shipui-design.md` for the full design spec.

---

## License

MIT
````

- [ ] **Step 2: Verify file written**

Run:
```bash
head -10 /Users/feli24a/Desktop/Proyectos/skills/README.md
```

Expected: Shows `# shipui` followed by the tagline blockquote.

- [ ] **Step 3: Commit**

```bash
cd /Users/feli24a/Desktop/Proyectos/skills && git add README.md && git commit -m "docs: add README with public-facing pitch and install instructions"
```

---

## Task 5: Write LICENSE (MIT)

**Files:**
- Create: `/Users/feli24a/Desktop/Proyectos/skills/LICENSE`

- [ ] **Step 1: Confirm copyright holder name with the user**

Ask the user (in chat, before writing):

> "For the MIT LICENSE I'm going to put `Copyright (c) 2026 Felipe Arias` — based on your email `feli24arias06@gmail.com`. If that's not your full legal name, tell me the right one before I write the file."

Wait for user response. Use whatever name they confirm.

- [ ] **Step 2: Write LICENSE with the confirmed name**

Write this content to `/Users/feli24a/Desktop/Proyectos/skills/LICENSE`, replacing `<NAME>` with the confirmed name from Step 1:

```
MIT License

Copyright (c) 2026 <NAME>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

- [ ] **Step 3: Verify file content**

Run:
```bash
head -3 /Users/feli24a/Desktop/Proyectos/skills/LICENSE
```

Expected: Shows `MIT License`, blank line, `Copyright (c) 2026 <confirmed name>`.

- [ ] **Step 4: Commit**

```bash
cd /Users/feli24a/Desktop/Proyectos/skills && git add LICENSE && git commit -m "chore: add MIT LICENSE"
```

---

## Task 6: Add .gitignore

**Files:**
- Create: `/Users/feli24a/Desktop/Proyectos/skills/.gitignore`

- [ ] **Step 1: Write .gitignore**

Write this content to `/Users/feli24a/Desktop/Proyectos/skills/.gitignore`:

```
# macOS
.DS_Store
.AppleDouble
.LSOverride

# Editors
.vscode/
.idea/
*.swp
*.swo
*~

# Python (for future scripts/)
__pycache__/
*.py[cod]
*$py.class
.venv/
venv/
.pytest_cache/

# Node (for future plugin packaging)
node_modules/
npm-debug.log
yarn-debug.log
yarn-error.log
.pnpm-debug.log

# Build outputs
dist/
build/
.next/

# Environment
.env
.env.local
.env.*.local
```

- [ ] **Step 2: Verify**

Run:
```bash
wc -l /Users/feli24a/Desktop/Proyectos/skills/.gitignore
```

Expected: ~30 lines.

- [ ] **Step 3: Commit**

```bash
cd /Users/feli24a/Desktop/Proyectos/skills && git add .gitignore && git commit -m "chore: add .gitignore"
```

---

## Task 7: Smoke test — install shipui and verify it loads

**Files:**
- No files created in this task — only verification.

- [ ] **Step 1: Check the final repo structure**

Run:
```bash
find /Users/feli24a/Desktop/Proyectos/skills -type f -not -path '*/.git/*' | sort
```

Expected output:
```
/Users/feli24a/Desktop/Proyectos/skills/.gitignore
/Users/feli24a/Desktop/Proyectos/skills/LICENSE
/Users/feli24a/Desktop/Proyectos/skills/README.md
/Users/feli24a/Desktop/Proyectos/skills/docs/superpowers/plans/2026-05-27-shipui-foundation.md
/Users/feli24a/Desktop/Proyectos/skills/docs/superpowers/specs/2026-05-27-shipui-design.md
/Users/feli24a/Desktop/Proyectos/skills/shipui/SKILL.md
/Users/feli24a/Desktop/Proyectos/skills/shipui/references/pre-delivery-checklist.md
```

- [ ] **Step 2: Install shipui into Claude Code skills**

Run:
```bash
ln -sf /Users/feli24a/Desktop/Proyectos/skills/shipui /Users/feli24a/.claude/skills/shipui
```

This creates a symlink so edits to the source repo are immediately reflected in the installed skill. (If the user prefers a copy instead of a symlink, use `cp -r` — but symlink is recommended during active development.)

- [ ] **Step 3: Verify install**

Run:
```bash
ls -la /Users/feli24a/.claude/skills/shipui/
```

Expected: Shows `SKILL.md` and `references/` accessible via the symlink.

- [ ] **Step 4: Verify SKILL.md is parseable as a skill**

Run:
```bash
python3 -c "
import yaml, re, sys
content = open('/Users/feli24a/.claude/skills/shipui/SKILL.md').read()
fm_match = re.match(r'^---\n(.*?)\n---', content, re.DOTALL)
if not fm_match:
    sys.exit('FAIL: no frontmatter')
fm = yaml.safe_load(fm_match.group(1))
assert 'name' in fm, 'FAIL: missing name'
assert 'description' in fm, 'FAIL: missing description'
assert fm['name'] == 'shipui', f'FAIL: name is {fm[\"name\"]}, expected shipui'
assert len(fm['description']) > 50, 'FAIL: description too short'
print('PASS: shipui SKILL.md is valid')
print(f'  name: {fm[\"name\"]}')
print(f'  description length: {len(fm[\"description\"])} chars')
"
```

Expected output:
```
PASS: shipui SKILL.md is valid
  name: shipui
  description length: <some number> chars
```

- [ ] **Step 5: Manual verification — invoke the skill in a fresh Claude Code session**

Open a new Claude Code session and type:

> "Use the shipui skill to plan a landing page for a wellness spa called Serenity."

Expected behavior: Claude loads `shipui/SKILL.md`, announces it's using shipui, then walks through steps 1–4 of the workflow (brief, aesthetic direction, brand inspiration, design tokens) at minimum, mentioning that the deeper reference files are coming in future plans.

If Claude doesn't pick up shipui automatically, the user can prompt: *"You should have a skill called shipui — use it."*

- [ ] **Step 6: Final commit (this plan + any cleanup)**

```bash
cd /Users/feli24a/Desktop/Proyectos/skills && git add docs/superpowers/plans/2026-05-27-shipui-foundation.md && git commit -m "docs: add foundation implementation plan"
```

- [ ] **Step 7: Verify git log shows a clean history**

Run:
```bash
cd /Users/feli24a/Desktop/Proyectos/skills && git log --oneline
```

Expected: 6–7 commits, one per task, in order. Each commit message starts with `feat:`, `docs:`, or `chore:`.

---

## What this plan does NOT do

- Does NOT write the 9 deep reference files (`01-aesthetic-direction.md` through `10-styles-catalog.md`). Those come in follow-up plans.
- Does NOT write the Python scripts (`scripts/search.py`, `scripts/check.py`).
- Does NOT create the data JSON files (`palettes.json`, `fonts.json`, etc.).
- Does NOT package shipui as a Claude Code plugin.
- Does NOT push to GitHub or publish.

After this plan, shipui is **installable and usable** with the 10-step workflow guidance inline in `SKILL.md` + the pre-delivery checklist as the QA gate. The deeper references will be added incrementally without breaking the installed skill.

---

## Next plan after this one

`docs/superpowers/plans/<date>-shipui-stack-foundation.md` — adds the three references that unlock the bare-minimum "ship a real component" capability:
- `references/03-design-tokens.md` — full token system specification
- `references/04-component-scout.md` — search-before-build playbook
- `references/05-component-contract.md` — contract-before-implementation playbook
