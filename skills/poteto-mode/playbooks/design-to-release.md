### Design to release

Read the **emil** skill first. It says where each skill below lives and when each applies, including the manual-only ones, which you read by path.

Run the passes in order, and meet each pass's criterion before starting the next. In each pass, read every named skill before working, and skip one only when its **emil** entry doesn't apply to this project. Translate web-specific guidance to the target platform by keeping the principle and swapping the mechanism.

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
   - Done when a release build succeeds with no demo data, debug UI, or placeholder copy. Stop before publishing.
7. Run **Opening a PR**.

In any pass:

- `animation-vocabulary`, `emil-design-vocabulary`, `emil-engineering-vocabulary` when you lack the exact term for something.
- `emil-ask-emil` when you can't tell which skill applies.
- `emil-borrow-a-brain` when the work should follow someone's published thinking.
- `emil-writing-skills` when a convention from this work should become a skill.

**Reply:** the build, the screenshots, the test results, the skills skipped and why, and the steps that need the user.
