---
name: emil
description: Routes to the right Emil Kowalski skill. Use when building, animating, reviewing, or polishing UI; for color, type, surfaces, forms, or marketing pages; before a UI launch; for naming a UI concept; or when the user names Emil.
---

Each skill lives at `../<name>/SKILL.md` from this file. Pick every skill whose entry matches the task, and read each one's SKILL.md in full.

Each entry carries its platform:

- **web**: the browser, phone browsers and PWAs included.
- **native**: native mobile apps (Swift, React Native, Expo).
- **any**: platform-agnostic.

`mobile-native`, `touch-and-accessibility`, and `apple-design` are web. A native app routes to `animate-expo` or `write-swift`, plus the **any** entries.

## Foundation

- **design-foundations** (any). The layout or hierarchy is wrong: spacing, alignment, button hierarchy, empty states, microcopy.
- **typography** (web). The text itself: fonts, type scales, line length, wrapping, truncation.
- **color** (web). Picking or auditing color values: OKLCH palettes, scales, dark-mode values, contrast.

## Build

- **animate** (web). Building new web motion.
- **animate-expo** (native). Any motion in React Native or Expo: gestures, haptics.
- **apple-design** (web). Apple-style fluid UI: springs, gestures, materials, typography.
- **surfaces** (web). Shadows, borders, gradients, elevation, and their dark-mode versions.
- **component-design** (web). The props API of a reusable React component.
- **forms-and-inputs** (web). Forms, inputs, buttons, validation, submit behavior.
- **marketing-pages** (web). Landing pages, blogs, docs sites, changelogs.
- **mobile-native** (web). A web app that must feel installed on a phone: 100vh, input zoom, tap highlights, the notch, PWAs.
- **prototype** (web). Several versions of a UI piece to flip between, before the design is decided.
- **ask-sonner** (web). Setting up or troubleshooting Sonner toasts.
- **pick-ui-library** (web). Choosing a library for a frontend job.
- **write-swift** (native). Writing, reviewing, or migrating Swift.
- **design-system-docs** (any). Writing a DESIGN.md so agents pick the right component, variant, and token.

## Review and fix

- **emil-design-eng** (web). The general taste reference for UI craft.
- **ui-polish** (web). The layout is right but feels unfinished: rendering, states, hit areas, layout shift. Fixes it.
- **ui-review** (web). Findings on a UI diff or generated component, ranked by harm. Reports only.
- **animations** (web). Motion that looks wrong: whether to animate, easing, duration, springs, enter and exit.
- **review-animations** (web). Reviewing a diff or file of animation code.
- **ask-lapse** (web). Seeing what an animation does frame by frame with Lapse.
- **animation-performance** (web). Motion that drops frames.
- **performance** (web). Slow UI beyond motion: long lists, loading, fonts and images, re-renders, layout shift.
- **touch-and-accessibility** (web). Someone is locked out: tap targets, focus, keyboard, screen readers, reduced motion.
- **unslop-design** (web). A screen that looks AI-generated or generic.
- **break-ui** (web). Stress-testing one component with worst-case data.

## Audit

- **improve-animations** (web). Auditing a whole codebase's motion. Read-only.
- **find-animation-opportunities** (web). Finding places that don't animate but should. Read-only.
- **prep-for-prod** (web). Sweeping the whole app before a launch, then fixing what a diff can fix.

## Vocabulary

- **animation-vocabulary** (web). The name of a motion effect.
- **design-vocabulary** (any). The name of something you can see, or the right word between near-synonyms.
- **engineering-vocabulary** (web). The name of a frontend behavior or pattern.
