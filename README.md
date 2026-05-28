# shipui

> A [Claude Code](https://claude.com/claude-code) **plugin** that ships production-grade web interfaces. Next.js + Tailwind v4 + shadcn/ui + Motion. Ten steps, five non-negotiable gates, zero AI-slop aesthetics.

shipui is the **production playbook** for shipping web UI with Claude Code. It auto-activates on any web/UI work — no `/skill` command needed — and walks Claude through a 10-step workflow from brief to ship.

If [`frontend-design`](https://github.com/anthropics/claude-code) is the aesthetic muse that says *"commit to a bold direction"*, shipui is the playbook that says *"now ship it with tokens, contracts, motion discipline, and a QA gate you can't skip."*

---

## What you get

**Two skills** in one plugin:

| Skill | Purpose |
|---|---|
| `shipui:using-shipui` | Auto-injected at session start. Tells Claude when to reach for the workflow. |
| `shipui:shipui` | The full 10-step workflow + 61-rule pre-delivery checklist. |

**A SessionStart hook** that injects the manifesto on every new session — so Claude knows shipui exists and will use it proactively the moment you ask for UI work.

**An opinionated stack**: Next.js (App Router) · React 19 · Tailwind v4 · shadcn/ui · Motion · Lucide · React Hook Form + Zod · Supabase · Vercel · next/font.

**A pre-delivery checklist** covering visual quality, design tokens, light/dark mode, responsive behavior, interaction feedback, motion discipline, WCAG AA accessibility, and Core Web Vitals.

---

## Install

### Recommended — as a Claude Code plugin

```bash
# Inside Claude Code, run:
/plugin marketplace add feli2arias/shipui
/plugin install shipui
```

Restart Claude Code. From the next session, shipui auto-activates on any web/UI request — no explicit invocation needed.

### Alternative — raw git clone

```bash
git clone https://github.com/feli2arias/shipui.git ~/.claude/plugins/shipui
```

Then restart Claude Code. The plugin is discovered automatically.

---

## How it works

When you start a session, the `SessionStart` hook fires and injects the `using-shipui` manifesto into Claude's context. The manifesto tells Claude:

> *If there is even a 1% chance the user's request involves building, designing, reviewing, or shipping any web UI, you MUST invoke `shipui:shipui` before writing a single line of code.*

So when you say *"build me a landing page for X"*, Claude doesn't write generic SaaS-template code. It calls `shipui:shipui`, gets the 10-step workflow, commits to an aesthetic direction, defines tokens, scouts components, writes contracts, implements with Tailwind v4 + shadcn idioms, layers in motion with reduced-motion gates, runs the 61-rule QA checklist — and only then ships.

---

## The 10-step workflow

1. **Brief** — product, audience, tone, constraints (3 sentences max)
2. **Aesthetic direction** — commit to one bold direction; no AI-slop
3. **Brand inspiration** — 58 brand specs or justify going from scratch
4. **Design tokens** — full token set BEFORE any component code ★
5. **Component scout** — shadcn → Radix → 21st.dev → Aceternity → scratch ★
6. **Component contracts** — props · variants · states · a11y · responsive ★
7. **Implementation** — Tailwind v4 + shadcn idioms, zero hardcoded values
8. **Motion layer** — purposeful, with reduced-motion fallbacks ★
9. **QA pass** — 61-rule pre-delivery checklist, no exceptions ★
10. **Polish** — one memorable detail beats five forgettable

★ = non-negotiable

---

## Who it's for

- Freelancers shipping client web work who want consistent, high-quality output without re-deciding the stack every project
- Solo founders building SaaS / e-commerce / landing pages who want production-grade UI without a designer
- Agencies wanting a shared playbook so every developer ships the same caliber
- Anyone tired of "AI-generated" aesthetics that all look the same

If you want Vue / Svelte / Remix / mobile — shipui isn't for you. The opinion is the product.

---

## Status

**v1.0 — Plugin foundation.** SessionStart hook · `using-shipui` manifesto · `shipui` 10-step workflow · pre-delivery checklist. Auto-activation works.

**Coming next:**
- v1.1 — Deep reference files (design tokens spec, component scout, contracts)
- v1.2 — Motion + accessibility + performance references
- v1.3 — Aesthetic direction + brand inspiration + 60+ styles catalog
- v1.4 — Python search & lint tooling
- v2.0 — Marketplace listing, plugin packaging polish

---

## License

MIT
