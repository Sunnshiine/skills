# No /code-review gate in poteto-mode, and no merged code-review skill

Status: accepted, 2026-10-19

PR #4 proposed that poteto-mode run `/code-review` once per patch at code-ready. The lead would triage the findings, fix what it accepts, and never re-review its own fixes. PR #5 proposed folding `thermo-nuclear-code-quality-review` into `/code-review` as one skill.

Before merging either, we ran an eval with a bar set in advance:

- #4 merges only if it improves code quality, statistically proven, and also improves correctness over a control.
- #5 merges only if it improves on #4 or on the control in the same way.

Neither cleared the bar. Both PRs were closed unmerged. poteto-mode keeps no review gate. `/code-review` and `thermo-nuclear-code-quality-review` stay separate skills that a user invokes.

## The eval

- **Tasks:** four real Sunnshiine/workout-app issues (#851, #961, #1033 and #1031). Each was implemented twice per arm by Opus from the same base commit, giving 24 runs.
- **Arms:**
  - Control: the kit before #4. It has no `/code-review`, but `opening-a-pr` already prescribes `interrogate`.
  - Gate: #4, revised so the lead triages the findings.
  - Gate + merged skill: #4 + #5.
- **Quality:** blind pairwise judging of each pair's diffs from base. Each pair got one Opus 5.5 judge and one Fable 5.1 judge, and a pair counted as a win only when both picked the same side. "Proven" means a one-sided sign test at p ≤ 0.05.
- **Correctness:** defects = failed hidden oracle checks + bugs a judge claimed that a blind checker reproduced by running probes on every head and on base.
- **Plan:** the analysis plan was sealed before the first judge ran.

| Comparison | Quality (W–L–T) | p | Defects |
|---|---|---|---|
| Gate vs control | 3–0–5 | 0.125 | 6 vs 10 |
| Gate + merged vs gate | 1–3–4 | 0.94 | 9 vs 6 |
| Gate + merged vs control | 2–3–3 | 0.81 | 9 vs 10 |

The gate's defect win is fragile. Drop the one pair where the control ran its own review through `interrogate`, and the gate is even on correctness: it has fewer defects in 2 pairs and more in 2. Most defects in every arm were bugs already at base that the run left unfixed, not bugs the run introduced.

## Why it didn't work

These findings come from an audit of all 16 gate-arm review transcripts, plus the judges' stated reasons.

1. **Most of the gate's gain came before the review.** Two of its three decisive wins (#1033, both reps) were already in the code-ready commit, before any reviewer ran. Review edits were small. They did improve the run's own diff, and final beat code-ready 6–0 within the gate arm. That gain is too small to show up against the control.
2. **The review comes too late to change the approach.** Nearly every judge's deciding difference was a design choice: which cell to target, where to anchor a suggestion, at what level to merge evidence. Reviewers questioned the design or the reading of the issue in about 9 runs, but only one run changed course. In the rest, the lead added a caveat, deferred the point, or called the reshape "widening the patch".
3. **Leads set the Spec findings aside.** The gate arm deferred or left unaddressed 39 of its 45 Spec findings. The merged-skill arm did the same with 17 of 23.
4. **The merged skill shifted the review toward Standards.** Standards made up 71% of its findings, against 53% for `/code-review` alone. It also raised half as many Spec findings, 23 against 45.
5. **Fixes nobody reviewed introduced defects.** One run's warm-up fix, made in answer to a Spec finding, introduced two confirmed bugs. The lead's reasoning was: "The fix answers the review, so I did not run a second review." Another run's fix broke the CRAP gate in CI, and the run reported every gate clean.
6. **Background reviewers broke the gate.** poteto-mode starts subagents in the background by default. Two merged-skill runs handed back while their reviewers were still running, and both had to be rerun. One rerun hit the concurrent-subagent limit and shipped with no Spec review.

## What would reopen this

- **A spec check before implementation, while the approach is still open.** This targets what actually decided the outcomes. It is untested.
- **A larger eval, set in advance, of the gate against the control.** Because both judges had to agree, about 60% of pairs tied. Proving an effect the size of the gate's lean would take roughly 16 or more pairs. Given finding 1, that alone isn't worth running.
