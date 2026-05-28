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
