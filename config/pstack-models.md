# pstack model configuration. One line per role. Delete a line to fall back to the skill default.
# `inherit-parent` or `auto` as a value: the role runs on the parent chat model (omit the subagent `model`). Alias entries in a panel list still count toward its fan-out.
# Policy: Fable only for planning, design, and the hardest tasks. Opus everywhere else. Sonnet may review, so review panels pair one Opus seat with one Sonnet seat.
# On Claude Code, pass the alias to the Agent tool: claude-opus-5-5 is `opus`, claude-sonnet-5-5 is `sonnet`, claude-fable-5-1 is `fable`.
# budget: large (xhigh)
feature, refactoring: claude-opus-5-5
bug-fix: claude-opus-5-5
perf-issue: claude-opus-5-5
hillclimb: claude-opus-5-5
judgment and prose: claude-opus-5-5
hardest tasks: claude-fable-5-1
how explorer: claude-opus-5-5
how explainer: claude-opus-5-5
why investigators: claude-opus-5-5
why synthesizer: claude-opus-5-5
reflect tooling: claude-opus-5-5
reflect judgment, divergent, synthesizer: claude-opus-5-5
arena runners: claude-opus-5-5, claude-sonnet-5-5, claude-sonnet-5-5
arena cross-judge pool: claude-opus-5-5, claude-sonnet-5-5
swarm workers: claude-opus-5-5
architect runners: claude-opus-5-5, claude-fable-5-1, claude-sonnet-5-5
interrogate reviewers: claude-opus-5-5, claude-sonnet-5-5
