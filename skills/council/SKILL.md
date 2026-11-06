---
name: council
description: Trigger this if the user says 'council'.
---

# Council

Before an audit, address outstanding PR comments, fix known issues, and run
relevant checks. Give council the updated implementation; do not defer known
fixes until reviews return. If the user wants to discard the implementation
and explore new ideas, skip fixes to code being replaced.

Bring in three delegates to help with the user's request, usually for review
or feedback. Use the latest Claude Opus, Fable, and Sonnet models, at high
reasoning effort. If the user's instructions name council members, use those.

In T3 Code, use `orchestrator_capabilities` to resolve the models, then
`delegate_task` to start one delegate per model in parallel. Elsewhere, use
the harness's subagent tools. If a member is unavailable, report it instead of
substituting.

Give each delegate the request and relevant context. For review or feedback,
keep their work read-only. All three models come from one vendor and can share
blind spots, so give each delegate a different angle: user-facing behavior and
visuals, correctness and regressions, or scope and simplicity. Collect their
responses and summarize the useful findings, disagreements, and recommended
next steps.

For a code review, ask each delegate for a score out of 10.
Count each full review pass as one round.
A fresh review after fixes starts a new round.

If the work ends in a pull request, put the results in the PR description,
under the `## Evidence` section of the `pr` skill's template:

```markdown
**Council review.** Rounds: 2

| Delegate | Round 1 | Round 2 |
| --- | --- | --- |
| Claude Opus | 7/10 | 9/10 |
| Claude Fable | 8/10 | 10/10 |
| Claude Sonnet | 7/10 | 9/10 |
```

If a delegate gives no score, write `no score`. Do not invent one.
If the PR is open, edit the description. Do not post a comment for this.
If there is no PR, put the same results in the final reply only.

If you agree with their recommendations, make the changes and request a fresh
review after. Continue until all delegates are satisfied with the outcome, for
at most 3 rounds unless the user asks for more. Stop early if a round returns
only nits. If the cap ends the loop, report what is still open. The cap is not
approval.

Do not let repeated reviews result in scope creep. It is your job to fight to
keep scope limited.
