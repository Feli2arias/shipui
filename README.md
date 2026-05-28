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
