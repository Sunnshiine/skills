---
name: emil
description: Routes to the right Emil Kowalski skill. Use when building, animating, reviewing, or polishing UI; for color, type, surfaces, forms, or marketing pages; before a UI launch; for naming a UI concept; for a full design-to-release workflow; or when the user names Emil.
---

Skills live in two places:

- Every `emil-*` skill except `emil-design-eng` comes from Emil's course and installs separately through `tools/install-course-skills`. Read it at `~/.claude/skills/<name>/SKILL.md` or `~/.codex/skills/<name>/SKILL.md`.
- Every other skill is at `../<name>/SKILL.md` from this file.

Skip any that are not installed. Read each chosen skill's SKILL.md in full.

For a whole app or product, run the Workflow. For a single task, pick every skill whose entry matches it. If two entries both match and you can't choose, or you need their order, read **emil-ask-emil**.

## Workflow

Run the passes in order, and meet each pass's criterion before starting the next. In each pass, read every named skill before working, and skip one only when its entry below doesn't apply to this project, naming the skip in your report. Translate web-specific guidance to the target platform by keeping the principle and swapping the mechanism.

1. **Design pass.** Decide the direction and write `DESIGN.md`: palette, type, shapes, surfaces, motion, and voice.
   - Skills: `emil-product-thinking`, `emil-get-creative`, `emil-prototype`, `emil-design-eng`, `emil-design-foundations`, `emil-typography`, `emil-color`, `emil-surfaces`, `apple-design`, `pick-ui-library`, `emil-design-system-docs`
   - Done when every later screen can take its tokens from `DESIGN.md`, and every text and background color pair passes a contrast check in each theme.
2. **Vertical slice.** Build one core flow end to end, with real data and persistence.
   - Skills: `write-swift`, `emil-component-design`, `emil-forms-and-inputs`, `emil-build-a-tool`, `emil-animations`, `animate`, `animate-expo`
   - Done when the flow works on the target platform and its data survives a restart.
3. **Full app.** Build every remaining screen, behavior, and empty state.
   - Skills: `emil-design-foundations`, `emil-marketing-pages`, `emil-mobile-native`, `ask-sonner`, `find-animation-opportunities`, `animate`, `choreograph`
   - Done when every required behavior works on the target platform and the data model has passing tests.
4. **Craft pass.** Apply each skill to every screen and fix every finding.
   - Skills: `emil-ui-polish`, `emil-ui-review`, `emil-unslop-design`, `emil-touch-and-accessibility`, `emil-animations`, `review-animations`, `improve-animations`, `remove-animations`, `emil-ask-lapse`
   - Done when you have reviewed screenshots of every screen in each theme and at the largest text size, and fixed what you found.
5. **Stress pass.** Test with no data, one item, the largest expected data set, very long text, and emoji and non-Latin text.
   - Skills: `break-ui`, `emil-performance`, `animation-performance`
   - Done when no layout breaks and scrolling and motion stay smooth with the largest data set.
6. **Release prep.** Sweep the whole app, then clean the code and copy that ship with it.
   - Skills: `emil-prep-for-prod`, `emil-unslop-code`, `emil-unslop-writing`
   - Done when a release build succeeds with no demo data, debug UI, or placeholder copy. Stop before publishing, and report the build, the screenshots, the test results, and the steps that need the user.

In any pass:

- `animation-vocabulary`, `emil-design-vocabulary`, `emil-engineering-vocabulary` when you lack the exact term for something.
- `emil-ask-emil` when you can't tell which skill applies.
- `emil-borrow-a-brain` when the work should follow someone's published thinking.
- `emil-writing-skills` when a convention from this work should become a skill.

## Foundation

- **emil-design-foundations.** The layout or hierarchy is wrong: spacing, alignment, button hierarchy, empty states, microcopy.
- **emil-typography.** The text itself: fonts, type scales, line length, wrapping, truncation.
- **emil-color.** Picking or auditing color values: OKLCH palettes, scales, dark-mode values, contrast.

## Build

- **animate.** Building new web motion.
- **animate-expo.** Any motion in React Native or Expo: gestures, haptics.
- **choreograph.** Several elements moving together: staggers, sequences, hero entrances, view swaps.
- **apple-design.** Apple-style fluid UI: springs, gestures, materials, typography.
- **emil-surfaces.** Shadows, borders, gradients, elevation, and their dark-mode versions.
- **emil-component-design.** The props API of a reusable React component.
- **emil-forms-and-inputs.** Forms, inputs, buttons, validation, submit behavior.
- **emil-marketing-pages.** Landing pages, blogs, docs sites, changelogs.
- **emil-mobile-native.** A web app that must feel installed on a phone: 100vh, input zoom, tap highlights, the notch, the software keyboard, PWAs. Without the course, use **mobile-native**.
- **emil-prototype.** Several versions of a UI piece to flip between, before the design is decided. Without the course, use **prototype**.
- **emil-get-creative.** Only a mood or vibe, no spec: research the visual language, then build a generator.
- **emil-build-a-tool.** Re-prompting keeps missing an artifact: build the small tool that produces it.
- **ask-sonner.** Setting up or troubleshooting Sonner toasts.
- **pick-ui-library.** Choosing a library for a frontend job.
- **write-swift.** Writing, reviewing, or migrating Swift.
- **emil-design-system-docs.** Writing a DESIGN.md so agents pick the right component, variant, and token.

## Review and fix

- **emil-design-eng.** The general taste reference for UI craft.
- **emil-ui-polish.** The layout is right but feels unfinished: rendering, states, hit areas, layout shift. Fixes it.
- **emil-ui-review.** Findings on a UI diff or generated component, ranked by harm. Reports only.
- **emil-animations.** Motion that looks wrong: whether to animate, easing, duration, springs, enter and exit.
- **review-animations.** Reviewing a diff or file of animation code.
- **remove-animations.** The interface has too much motion. Only subtracts.
- **emil-ask-lapse.** Seeing what an animation does frame by frame with Lapse.
- **animation-performance.** Motion that drops frames.
- **emil-performance.** Slow UI beyond motion: long lists, loading, fonts and images, re-renders, layout shift.
- **emil-touch-and-accessibility.** Someone is locked out: tap targets, focus, keyboard, screen readers, reduced motion.
- **emil-unslop-design.** A screen that looks AI-generated or generic.
- **break-ui.** Stress-testing one component with worst-case data.

## Audit

- **improve-animations.** Auditing a whole codebase's motion. Read-only.
- **find-animation-opportunities.** Finding places that don't animate but should. Read-only.
- **emil-prep-for-prod.** Sweeping the whole app before a launch, then fixing what a diff can fix.

## Vocabulary

- **animation-vocabulary.** The name of a motion effect.
- **emil-design-vocabulary.** The name of something you can see, or the right word between near-synonyms.
- **emil-engineering-vocabulary.** The name of a frontend behavior or pattern.

## Beyond the interface

- **emil-unslop-code.** Code that reads as AI-generated.
- **emil-unslop-writing.** Prose that reads as AI-written.
- **emil-writing-skills.** Writing a SKILL.md, or fixing one agents ignore.
- **emil-borrow-a-brain.** Turning someone's published work into a skill that answers as they would.
- **emil-product-thinking.** Whether a product idea deserves building, tested by interview.
