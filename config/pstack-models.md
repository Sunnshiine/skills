# pstack model configuration. One line per role. Delete a line to fall back to the skill default.
# `inherit-parent` or `auto` as a value: the role runs on the parent chat model (omit the subagent `model`). Alias entries in a panel list still count toward its fan-out.
# Policy: Opus at medium for most roles. Fable at xhigh only for the hardest tasks. Synthesizers, judges, reviewers, and perf at high. Panels keep one Fable seat and one Sonnet seat (both high) for a second perspective.
# On Claude Code, pass the alias to the Agent tool: claude-opus-5-5 is `opus`, claude-sonnet-5-5 is `sonnet`, claude-fable-5-2 is `fable`. Pass the slug's effort suffix as the Agent `effort`.
# budget: small (medium)
feature, refactoring: claude-opus-5-5-medium
bug-fix: claude-opus-5-5-medium
perf-issue: claude-opus-5-5-high
hillclimb: claude-opus-5-5-medium
judgment and prose: claude-opus-5-5-medium
hardest tasks: claude-fable-5-2-xhigh
how explorer: claude-opus-5-5-medium
how explainer: claude-opus-5-5-medium
why investigators: claude-opus-5-5-medium
why synthesizer: claude-opus-5-5-high
reflect tooling: claude-opus-5-5-medium
reflect judgment, divergent, synthesizer: claude-opus-5-5-high
arena runners: claude-opus-5-5-medium, claude-fable-5-2-high, claude-sonnet-5-5-high
arena cross-judge pool: claude-opus-5-5-high, claude-fable-5-2-high
swarm workers: claude-opus-5-5-medium
architect runners: claude-opus-5-5-medium, claude-fable-5-2-high, claude-sonnet-5-5-high
interrogate reviewers: claude-opus-5-5-high, claude-fable-5-2-high
