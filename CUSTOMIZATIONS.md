# Customizations

## arena
- Cross-judge excludes the parent's model, not its family, so a Claude-only pool still gets a judge.
## council
- Seats the latest Claude Opus, Fable, and Sonnet instead of one model from each of three providers.
- Gives each delegate a different review angle, because one vendor's models can share blind spots.
- Caps the loop at 3 rounds unless the user asks for more, and stops early when a round returns only nits.
- Puts the score table under `## Evidence` from the `pr` template instead of its own `## Council review` section.
## poteto-agent
- Claude Code agent frontmatter: dropped Cursor `is_background`.
- Finds `poteto-mode` in the skill tree at `~/.agents/skills` instead of searching `~/.cursor/plugins`.
- Says "subagent spawn" and "general-purpose agent" instead of Cursor `Task` and `generalPurpose`.
## poteto-mode
- Model-invocable: dropped `disable-model-invocation: true`.
- Authoring-a-skill playbook uses `writing-for-agents` and adds a "ruthlessly prune no-ops" step.
- Adds the Animation pass playbook (`playbooks/animation-pass.md`): Emil's find-animation-opportunities → animate → review-animations chain.
- Adds the Autopilot-design playbook (`playbooks/autopilot-design.md`): design pass → vertical slice → full app → craft pass → stress pass → release prep through Emil's skills, stacking with Autopilot-stack.
- Autopilot-design vertical slice and full-app passes read Emil's `gestures` skill.
- Autopilot-full playbook states Sunny's grant to squash and merge cleared PRs, and owners carry it in their briefs.
- Adds `scripts/catchup` (`check`, `carry`, `radar`) with `scripts/catchup.test`: the one source of rebase and verdict-carry decisions. It fetches a remote-tracking base first, and radar skips ancestor pairs and merges stacked pairs from their own merge base.
- Autopilot-full step 2 drops the code-ready rebase; owners rebase only on a `catchup check` conflict or a trunk-caused CI failure.
- Autopilot-full step 4 carries a rebased verdict with no verifier when `catchup carry` says `carry`, citing its range-diff proof.
- Autopilot-full step 5 drops the merge-prep rebase; the owner tests the merge result on the trunk SHA it lands on and merges with no new head, rechecking if trunk moved before `gh pr merge`.
- Autopilot-full step 6 has the root run `catchup radar` after each merge and message only the owners it names, instead of freezing merges.
- Autopilot-stack step 2 checks and carries through `catchup` instead of an unconditional rebase onto the parent.
- Multi-phase-plan template drops the code-ready and post-verdict rebase boxes for `catchup check` and `catchup carry`.
- Babysit steps 4 and 5 confirm a conflict with `catchup check` before reporting or rebasing.
- Shipping step 3 compares verdicts with `catchup carry` instead of a bare `git patch-id`.
- Orchestrate runs `catchup radar` after each merge and messages only the owners it names.
- Playbooks call `catchup` by its installed path, `~/.claude/skills/poteto-mode/scripts/catchup`.
- `catchup` usage says to push before the `rerecord` line, since `rerecord-snapshots` needs HEAD on origin.
- Harness section covers only T3 Code, Claude Code, and Codex on this machine; Cursor, Pi, and OpenCode mappings dropped.
- Adds `references/t3.md`: T3 tools for spawning (launched threads vs `delegate_task`), kickoffs, supervising, `/loop` as `schedule_task`, and PR watching.
- Drops Cursor cloud agents and VMs everywhere; every worker runs in its own local worktree.
- Drops `cursor-team-kit` attributions; `deslop` is the local skill, `control-ui`/`control-cli` map to Playwright/CDP and tmux in Harness.
- Model defaults are `claude-opus-5-5` (hardest: `claude-fable-5-1`); drops the `grok` defaults, `-fast` slugs, and fast-mode rules.
- Orchestrate keeps state in a worktree `notes.md` and covers a chief-of-staff chat: every request goes to an owner (a T3 thread, else a subagent) that runs the routed playbook or named skill.
- Autopilot-full owners are local worktree workers (T3 launched threads), and trails and agent records live in the root's `notes.md`.
- Harness maps Cursor terms in routed skills (`swarm`, `show-me-your-work`, `ketchup`) to local equivalents.
- `references/t3.md` has owners use `watch_pull_request` instead of babysit's `watch-pr` drive under `/loop`.
- `/loop 1h` heartbeats become "an hourly `/loop`" mapped per harness.
- Orchestrate cuts work into small units, runs broad sweeps alone, and never holds a verified PR to batch it.
- Babysit names the structure fix (one entry per line, `merge=union`) when a conflict lands on an append point.
- Verifiers (Orchestrate, `references/t3.md`), eval judges, and second opinions run on a Claude model other than the author's, per the `# Providers` line in the pstack settings file.
## setup-pstack
- Written rule carries a `# Providers` line: Claude only for every role, Codex reserved for image generation.
## show-me-your-work
- Trail reviewer runs on a Claude model other than the author's, per the `# Providers` line.

<!-- BEGIN renames (generated by tools/sync; edits here are overwritten) -->
## Renamed by sync
- `matt-tdd`: mattpocock skill `tdd`, renamed because pstack has one with that name.
- `matt-teach`: mattpocock skill `teach`, renamed because pstack has one with that name.
<!-- END renames -->
