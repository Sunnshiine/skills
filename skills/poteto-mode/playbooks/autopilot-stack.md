### Autopilot-stack

Run the Autopilot-full playbook, but do not merge.

1. **In place of step 5, stop at verified.** Stop when each PR is verified and green at its current head, then hand the PRs to the operator. After the handoff, nobody pushes without the operator's go. Every loop tick prompt names this file, so each tick sees the no-merge rule.
2. **Stack a PR only when it builds on another PR.** This is the one exception to step 3. Base the PR on the other PR's branch in place of trunk, per **Size and stacks** in `playbooks/opening-a-pr.md`. Each PR runs step 2's `scripts/catchup check --base <parent-branch>`, and the stack root runs it against trunk. Pass `--old-base <old parent tip>` to `check` and `carry` once the parent was rewritten, or the child's copy of the old parent commits reads as a conflict. A new head on the lower PR restacks the PRs above it, and a PR whose `catchup carry` says `carry` keeps its verdict.

**Reply:** list each PR with its verdict, in place of what merged.
