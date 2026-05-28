---
name: using-shipui
description: Use when starting any conversation that involves web UI, frontend, design, landing pages, dashboards, components, SaaS, e-commerce, .tsx, .html, Next.js, React, Tailwind, shadcn, Motion — primes Claude to reach for the shipui:shipui workflow automatically. Auto-injected at session start via SessionStart hook.
---

<SUBAGENT-STOP>
If you were dispatched as a subagent to execute a specific task, skip this skill.
</SUBAGENT-STOP>

<EXTREMELY-IMPORTANT>
You have access to **shipui** — an opinionated production playbook for shipping web interfaces.

**If there is even a 1% chance the user's request involves building, designing, reviewing, refactoring, or shipping any web UI, you ABSOLUTELY MUST invoke `shipui:shipui` via the Skill tool BEFORE writing a single line of code.**

This is not negotiable. This is not optional. You cannot rationalize your way out of this.
</EXTREMELY-IMPORTANT>

## When shipui applies

ALWAYS reach for `shipui:shipui` when the user asks for any of:

- Landing page, marketing site, dashboard, admin panel, SaaS, e-commerce, portfolio, blog
- UI component (button, modal, navbar, sidebar, card, table, form, chart, hero, footer)
- Frontend in `.tsx`, `.jsx`, `.html`, Next.js, React, Tailwind, shadcn/ui, Motion
- Anything containing the words: design, ship, build, redesign, refactor UI, improve UI, fix UI
- Reviews of frontend code that needs to be production-grade

When in doubt: **invoke shipui**. It's faster to invoke and bail out than to produce AI-slop without it.

## When shipui does NOT apply

- iOS / SwiftUI / UIKit / Liquid Glass → use platform skills instead
- Android / Jetpack Compose → use Compose skills
- React Native / Flutter → use mobile skills
- Vue / Svelte / Solid / Qwik (shipui is opinionated to React/Next.js)
- Pure backend / database / API / DevOps work

For these cases, you may proceed normally without shipui.

## The shipui workflow at a glance

When you invoke `shipui:shipui` you get a 10-step workflow:

1. **Brief** — product, audience, tone, constraints
2. **Aesthetic direction** — commit to ONE bold direction (no AI-slop)
3. **Brand inspiration** — 58 brand specs or justify from scratch
4. **Design tokens** — color, type, spacing, motion BEFORE any component code ★
5. **Component scout** — shadcn → Radix → 21st.dev → Aceternity → scratch ★
6. **Component contracts** — props, states, a11y, responsive pinned upfront ★
7. **Implementation** — Tailwind v4 + shadcn. Server Components default. Zero hardcoded values.
8. **Motion layer** — why, how long, reduced-motion. Only transform & opacity. ★
9. **QA pass** — 61-rule pre-delivery checklist. Every box must check. ★
10. **Polish** — one memorable detail beats five forgettable

★ = non-negotiable. Skipping any of these means the work is NOT shipui.

## How to use this skill

1. **First**, on any web-UI request, call the Skill tool with `shipui:shipui` to load the full workflow.
2. Follow the workflow in order. Use the reference files when each step says to load them.
3. Run the pre-delivery checklist at step 9. **No work ships without all checkboxes green.**

## Red flags — these thoughts mean STOP

| Thought | Reality |
|---|---|
| "This is just a quick component" | Quick components still need contracts. Invoke shipui. |
| "I'll just use a card grid" | That's the AI-slop pattern. Pick a real aesthetic direction. |
| "Inter is fine" | Inter is the AI-slop default. Use a distinctive font. |
| "I'll add a11y later" | Retrofitting a11y is always harder. It's part of the contract. |
| "Hardcoded `#fff` just this once" | No. Add the token first, then reference it. |
| "The user didn't say 'use shipui'" | Doesn't matter. If it's web UI, you invoke shipui. |

## Companion skills

- `frontend-design` (Anthropic plugin) — the aesthetic muse, pair with shipui's playbook
- `awesome-design-md` — the 58 brand specs shipui draws from at step 3
- `motion-design`, `motion-references:*` — extra depth for step 8
- `component-contract`, `pixel-enforcer`, `ui-scout` — the disciplines shipui consolidates
