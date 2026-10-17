### Animation pass

**You own which moments move. Most candidates should end up not animating.**

Emil Kowalski's chain: **find-animation-opportunities** → **animate** → **review-animations**. Each skill opens with an Initial Response stub that waits for a question. Hand each one its input in the same turn: the surface, then the row, then the diff.

1. Run **find-animation-opportunities** on the surface the user named, or the whole app if they named none. Done when its report has all three parts: opportunities, rejected candidates, verdict. If no row survives, skip to the reply.
2. Build every surviving row with **animate**, one row and one commit at a time. This replaces the finder's `improve-animations plan` handoff. animate re-runs the gate, and a row it rejects is dropped and goes in the reply with its reason. Done when each row is committed or dropped.
3. Review the diff in a fresh `poteto-agent` that reads `review-animations/SKILL.md` and its `STANDARDS.md` in full. The skill is user-invoked, so the agent reads it by path from the skill folders in **Harness**. On Block, fix each finding with **animate**, then send the new diff to another fresh reviewer. Done on Approve, or after three Block rounds. In that case, carry the open findings into the reply.
4. Feel-check each animation on the running surface with the control skill. Play it at 2–5× duration, then again with `prefers-reduced-motion` on. Capture a recording or a frame sequence per row. Done when every row has a capture. Name any feel you couldn't settle from a capture as a check for the user.
5. Run **Opening a PR**.

**Reply:** the rows built, rows rejected by either gate and why, the review verdict and rounds, captures per row, and the feel checks left for the user.
