# shipui — Design Spec

**Status:** Approved
**Date:** 2026-05-27
**Author:** feli24arias06@gmail.com
**Location:** `/Users/feli24a/Desktop/Proyectos/skills/`

---

## 1. Purpose

**shipui** is an opinionated, web-only design and frontend skill for Claude Code. It consolidates the practical content of ~15 existing fragmented skills (`ui-ux-pro-max`, `frontend-patterns`, `motion-design`, `awesome-design-md`, `component-contract`, `pixel-enforcer`, `ui-scout`, `frontend-design`, `motion-references:*`, `video-to-website`, `frontend-slides`, `coding-standards`, etc.) into a single, coherent product that ships production-grade web interfaces.

It is the **production playbook** to complement `frontend-design`'s **aesthetic muse**. Where `frontend-design` says *"commit to a bold direction"*, shipui says *"now ship it with Next.js + Tailwind + shadcn + Motion, with no hardcoded values, full a11y, and a polished motion layer."*

### Success Criteria

- A non-technical user can say "build me a landing page for a wellness spa" and Claude produces a production-grade Next.js + Tailwind + shadcn implementation following shipui's 10-step workflow.
- Every implementation uses design tokens (no hardcoded colors, spacing, or typography values).
- Every component has an explicit contract (props, states, accessibility, responsive behavior) before implementation.
- Every animation has a purpose, a duration justified against the motion guide, and a `prefers-reduced-motion` fallback.
- The skill is publishable and shareable as a standalone repository (not coupled to the user's `~/.claude/`).

### Non-Goals

- iOS / SwiftUI / UIKit / Liquid Glass content (web-only).
- Android / Compose / Jetpack content.
- React Native / Flutter / cross-platform mobile.
- Replacing the existing 15 skills — they remain installed and untouched. shipui is a parallel, standalone product.

---

## 2. Audience

- **Primary:** The skill author (non-technical owner) using Claude Code to ship freelance web work.
- **Secondary:** Other Claude Code users who install shipui as a community skill and want an opinionated web-first design playbook.

---

## 3. Opinionated Stack

This is the **only** stack shipui produces. The skill does not present alternatives unless the user explicitly says "use X instead":

| Layer | Choice | Why |
|-------|--------|-----|
| Framework | Next.js (App Router) | SSR, RSC, image/font optimization, file-based routing, deployed via Vercel |
| UI runtime | React 19 | Server Components + transitions + use() |
| Styling | Tailwind CSS v4 | Token-driven, zero runtime CSS-in-JS, design tokens in `@theme` |
| Component library | shadcn/ui | Copy-paste primitives over Radix, full control, accessibility built in |
| Motion | Motion (motion.dev) | Successor to framer-motion, smaller bundle, better performance |
| Icons | Lucide React | Default for shadcn, consistent, tree-shakeable |
| Forms | React Hook Form + Zod | Accessible, type-safe, performant |
| Data | Supabase | Database, auth, storage, realtime (user's default backend) |
| Hosting | Vercel | Optimized for Next.js |
| Fonts | next/font with Google Fonts | Self-hosted, no FOIT, zero layout shift |

If a user's existing project uses a different stack (e.g., Vue, Svelte, Remix), shipui respects it but does not actively support it — the user should fall back to the relevant existing skill.

---

## 4. Architecture

shipui follows the **thin router + modular references + data + scripts** pattern proven by `ui-ux-pro-max`, `awesome-design-md`, and `frontend-design`.

### File Layout

```
shipui/
├── SKILL.md                          # ~200 lines: manifesto + 10-step workflow + router
├── README.md                         # Public-facing description for the repo
├── LICENSE                           # MIT
├── references/
│   ├── 01-aesthetic-direction.md     # Choosing a bold visual direction
│   ├── 02-brand-inspiration.md       # Using awesome-design-md brands as reference
│   ├── 03-design-tokens.md           # Color, type, spacing, shadow, radius, motion token system
│   ├── 04-component-scout.md         # Search shadcn → 21st.dev → Radix → Aceternity before building
│   ├── 05-component-contract.md      # Define props/states/a11y/responsive before implementing
│   ├── 06-tailwind-shadcn.md         # The stack: Tailwind v4 + shadcn idioms, theming, dark mode
│   ├── 07-motion.md                  # Motion lib + reduced-motion + scroll-triggered + page transitions
│   ├── 08-accessibility.md           # WCAG AA, keyboard nav, focus management, ARIA, contrast
│   ├── 09-performance.md             # Core Web Vitals, image opt, font loading, code splitting
│   ├── 10-styles-catalog.md          # 60+ named styles (glassmorphism, brutalist, minimal, etc)
│   └── pre-delivery-checklist.md     # Non-negotiable QA gates before declaring "done"
├── data/
│   ├── palettes.json                 # Curated palettes indexed by industry/vibe
│   ├── fonts.json                    # Display/body font pairings from Google Fonts
│   ├── styles.json                   # Style catalog metadata (when to use, anti-patterns)
│   └── tokens-template.json          # Starter token set for a new project
└── scripts/
    ├── search.py                     # CLI to query data/ (palettes, fonts, styles) by keyword
    └── check.py                      # Pre-delivery checker (greps for hardcoded values, emoji icons, etc)
```

### Loading Strategy

- **Always loaded:** `SKILL.md` only (~200 lines, ~3k tokens).
- **Loaded on demand:** Claude reads a specific `references/NN-*.md` when the workflow step requires it.
- **Queried by CLI:** `data/*.json` is never read directly — Claude calls `scripts/search.py` to retrieve only the matching subset.

This keeps Claude's context lean: the full skill content (~3000 lines across all files) is never simultaneously in context.

---

## 5. The 10-Step Workflow (Core Contribution)

This is the workflow `SKILL.md` enforces every time the user requests UI work. Each step maps to a reference file.

| # | Step | Reference | Output |
|---|------|-----------|--------|
| 1 | **Brief** | (in SKILL.md) | Product type, audience, tone keywords, constraints |
| 2 | **Aesthetic direction** | `01-aesthetic-direction.md` | One BOLD committed direction (no hedging) |
| 3 | **Brand inspiration** | `02-brand-inspiration.md` | Pick brand from awesome-design-md OR justify "from scratch" |
| 4 | **Design tokens** | `03-design-tokens.md` | Tokens file: colors, type scale, spacing, shadows, radii, motion |
| 5 | **Component scout** | `04-component-scout.md` | List of shadcn/Radix/21st.dev components to reuse vs build |
| 6 | **Component contracts** | `05-component-contract.md` | For each new component: props/states/a11y/responsive contract |
| 7 | **Implementation** | `06-tailwind-shadcn.md` | Production code, zero hardcoded values |
| 8 | **Motion layer** | `07-motion.md` | Purposeful animations with reduced-motion fallbacks |
| 9 | **QA pass** | `08-accessibility.md` + `09-performance.md` + `pre-delivery-checklist.md` | All checks green |
| 10 | **Polish** | `10-styles-catalog.md` | Distinctive details that make it memorable |

`SKILL.md` describes each step in 2-3 lines and tells Claude which reference to load when. The references contain the depth.

---

## 6. SKILL.md Manifesto (Tone & Voice)

`SKILL.md` opens with a short manifesto (~10 lines) that sets the bar:

> **shipui** ships production-grade web interfaces. Every design decision is intentional. Every value comes from a token. Every component has a contract. Every animation has a reason. Every interface is accessible by default. We don't ship "AI-generated" aesthetics — we ship interfaces that someone will remember.
>
> If you can't answer "why this color, why this spacing, why this animation," you're not ready to ship. Go back one step.

This is the personality. It's slightly stern, very opinionated, and treats shipping as a craft.

---

## 7. Reference File Specs (high-level)

Each reference is 150-400 lines, focused on one topic, with code examples in Next.js/Tailwind/shadcn idiom.

### 01-aesthetic-direction.md
Adapted from `frontend-design`. The 12 named directions (brutally minimal, maximalist chaos, retro-futuristic, organic, luxury, playful, editorial, brutalist, art deco, soft pastel, industrial, etc.). How to pick one. How to commit. Anti-patterns (the "AI slop" list).

### 02-brand-inspiration.md
Lists all 58 brands available in `awesome-design-md`. Maps aesthetic vibes to brands ("minimal dark" → Linear/Vercel; "playful colorful" → Pinterest/Notion). Workflow to extract tokens from a brand spec into the project's `tokens.css`.

### 03-design-tokens.md
The token system. CSS variables in `@theme` (Tailwind v4 syntax). Color palette structure (50-950 scales), semantic colors (primary, accent, destructive, muted), dark mode mirroring, typography scale (display/heading/body/caption), spacing scale (4pt grid), shadow elevation scale, radius scale, motion duration/easing tokens. Forbids hardcoded values (this is the "pixel-enforcer" rule integrated).

### 04-component-scout.md
Adapted from `ui-scout`. Search order: 21st.dev MCP → shadcn/ui → Radix UI → Aceternity → Magic UI → build from scratch. The 80% rule. When to adapt vs rebuild. Attribution comments.

### 05-component-contract.md
Adapted from `component-contract`. The contract template (props, variants, states, a11y, responsive). What counts as a state. Why responsive and a11y are part of the contract.

### 06-tailwind-shadcn.md
The stack manual. Tailwind v4 `@theme` syntax. How to extend shadcn primitives. Dark mode setup. Container queries. Arbitrary value discipline. shadcn theming, custom variants, composition over forking.

### 07-motion.md
Adapted from `motion-design` + `motion-references:*`. The 3 questions (why, how long, reduced motion). Motion lib patterns (entrance, exit, layout, scroll-triggered). Performance rules (only transform/opacity). Page transitions with App Router. Reduced-motion gating with `useReducedMotion()`.

### 08-accessibility.md
WCAG AA baseline. Keyboard navigation patterns. Focus management (modal, dropdown, drawer). ARIA roles cheat sheet for shadcn primitives. Color contrast minimums. Reduced motion. Form labeling.

### 09-performance.md
Core Web Vitals targets (LCP < 2.5s, INP < 200ms, CLS < 0.1). next/image and next/font usage. Lazy loading and Suspense boundaries. Bundle size discipline. Server Components vs Client Components decision tree.

### 10-styles-catalog.md
60+ named visual styles with when-to-use, when-not-to-use, example sites. Glassmorphism, brutalism, neumorphism, claymorphism, bento grid, swiss/grid, editorial, terminal/CLI, magazine, retro Y2K, dark academia, sunset/gradient, monospace, etc. Each style has 2-3 concrete Tailwind snippets.

### pre-delivery-checklist.md
The non-negotiable gates before declaring "done":
- [ ] Visual: no emoji icons, consistent icon set, no incorrect logos, no layout-shifting hover states
- [ ] Tokens: no `#`, `rgb(`, `hsl(` in component files; no hardcoded px in `style={{}}`
- [ ] Light/dark: both modes tested, sufficient contrast (4.5:1+)
- [ ] Responsive: tested at 375, 768, 1024, 1440px; no horizontal scroll on mobile
- [ ] Interaction: cursor-pointer on clickable; hover feedback; focus visible; smooth transitions
- [ ] Motion: every animation has a reason; reduced-motion respected
- [ ] A11y: alt text, form labels, keyboard nav works, screen reader announces correctly
- [ ] Performance: images use next/image, fonts use next/font, no client component without reason

---

## 8. Data Files (data/)

JSON files queried by `scripts/search.py`. Never read directly by Claude.

### palettes.json
~96 palettes. Each entry: `{ name, vibe, industry, light: {...tokens}, dark: {...tokens}, source }`. Vibes: minimal, bold, warm, cool, monochrome, vibrant, earthy, neon, pastel, etc. Industries: SaaS, e-commerce, fintech, healthcare, beauty, gaming, education, etc.

### fonts.json
~57 pairings. Each entry: `{ name, display: {family, weights, source}, body: {family, weights, source}, vibe, when_to_use }`.

### styles.json
~67 styles metadata. Each entry: `{ name, summary, when_to_use, anti_patterns, example_brands, tailwind_snippet_ref }`.

### tokens-template.json
A starter token file for new projects. Color scales, type scale, spacing, shadows, radii — all with safe defaults.

---

## 9. Scripts (scripts/)

### search.py
CLI to query data files without loading them into context.

```bash
python3 shipui/scripts/search.py --palette --industry saas --vibe minimal
python3 shipui/scripts/search.py --fonts --vibe editorial
python3 shipui/scripts/search.py --style glassmorphism
python3 shipui/scripts/search.py --design-system "wellness spa" --industry beauty
```

The `--design-system` mode returns a complete starter pack (palette + fonts + style + checklist) for a given brief — adapted from `ui-ux-pro-max`'s `--design-system` flag.

### check.py
Pre-delivery linter. Greps the working tree for the non-negotiables:

```bash
python3 shipui/scripts/check.py ./src
```

Checks for: hardcoded colors (`#[0-9a-f]{3,8}`, `rgb(`, `hsl(`), inline styles with hardcoded values, emoji in JSX, missing alt attributes, missing form labels, `width:`/`height:` in transitions.

Returns a list of violations grouped by category. Exits non-zero if any found.

---

## 10. Out of Scope (Explicit Non-Goals)

| Excluded | Reason |
|----------|--------|
| iOS / SwiftUI / UIKit / Liquid Glass | Web-only |
| Android / Compose | Web-only |
| React Native / Flutter | Web-only |
| Vue / Svelte / Solid / Qwik | Opinionated stack is Next.js + React |
| CSS-in-JS (styled-components, emotion) | Tailwind only |
| GSAP / lottie / three.js | Motion lib only by default; mention as escape hatch only |
| Video editing, slides, presentations | Separate skills already exist (`frontend-slides`, `video-to-website`) |
| Backend / API design / database | Separate skills (`backend-patterns`, `postgres-patterns`) |
| Build error fixing / TDD / testing | Separate skills (`tdd-workflow`, etc) |

---

## 11. Distribution & Repository

- The skill lives at `/Users/feli24a/Desktop/Proyectos/skills/` — a standalone git repo, not coupled to `~/.claude/`.
- `README.md` is the public-facing pitch: what shipui is, who it's for, how to install (copy to `~/.claude/skills/shipui/` or as a plugin).
- `LICENSE` is MIT.
- Future: package as a Claude Code plugin for one-line install.

---

## 12. Implementation Phases

The implementation plan (next step, via writing-plans) will sequence:

1. **Phase 1 — Skeleton:** SKILL.md, README, LICENSE, empty references/ and data/ folders. shipui is installable but does nothing yet.
2. **Phase 2 — Core workflow:** Write SKILL.md with the 10-step workflow + manifesto. Write `pre-delivery-checklist.md`.
3. **Phase 3 — Stack foundation:** `03-design-tokens.md`, `06-tailwind-shadcn.md`, `tokens-template.json`. These unlock the bare minimum to ship.
4. **Phase 4 — Process gates:** `04-component-scout.md`, `05-component-contract.md`. The discipline layer.
5. **Phase 5 — Motion + a11y:** `07-motion.md`, `08-accessibility.md`. The polish/quality layer.
6. **Phase 6 — Aesthetic depth:** `01-aesthetic-direction.md`, `02-brand-inspiration.md`, `10-styles-catalog.md`. The creative layer.
7. **Phase 7 — Performance:** `09-performance.md`. The shipping layer.
8. **Phase 8 — Data + tooling:** `data/*.json`, `scripts/search.py`, `scripts/check.py`. The discoverability layer.
9. **Phase 9 — Distribution:** README polish, plugin packaging, first release.

---

## 13. Open Questions (for implementation plan)

- Should `scripts/search.py` be replaceable with a shell script + jq for users without Python? (Probably yes — defer to plan.)
- Should `tokens-template.json` be a Tailwind v4 `@theme` block instead of JSON? (Probably both — JSON as source, generates CSS.)
- Source for the 58 brands in `02-brand-inspiration.md`: link to the user's existing `awesome-design-md` references, or vendor copies into shipui's repo? (Vendor — shipui must be self-contained to be famous.)
