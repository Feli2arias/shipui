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
