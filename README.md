# skills

The skills and agents I run in Claude Code and Codex, on every machine. Upstream skill repos are merged in nightly without losing my edits.

## Sources

`sources.json` lists the upstreams in precedence order and what to take from each.

| Source | Upstream | Taken |
| --- | --- | --- |
| `pstack` | [backnotprop/pstack](https://github.com/backnotprop/pstack) | every skill, plus the `poteto-agent` and `comment-sicko` agents |
| `cursor-team-kit` | [cursor/plugins](https://github.com/cursor/plugins/tree/main/cursor-team-kit) | `deslop`, `fix-ci`, `get-pr-comments`, `thermo-nuclear-code-quality-review` |
| `emil` | [emilkowalski/skills](https://github.com/emilkowalski/skills) | every skill |
| `humanlayer` | [humanlayer/skills](https://github.com/humanlayer/skills) | `show-me`, `rpi`, and the `rpi` agents |
| `mattpocock` | [mattpocock/skills](https://github.com/mattpocock/skills) | engineering and productivity skills except `prototype` and `to-questionnaire`, plus `chief-of-staff` |

When two sources ship a skill with the same name, the earlier source keeps it and the later one is renamed with its prefix, such as `matt-tdd`. Upstream licenses are in `licenses/`.

## Install on a new machine

Requires `git` 2.42 or later, `jq`, and `bash`.

```shell
git clone https://github.com/Sunnshiine/skills ~/Projects/skills
~/Projects/skills/tools/install
~/Projects/skills/tools/install --launchd
```

`tools/install` symlinks every skill into `~/.agents/skills` (read by Codex) and `~/.claude/skills`, links agents into `~/.claude/agents`, generates their Codex versions in `~/.codex/agents`, and adds the shared instructions in `config/global-instructions.md` to `~/.claude/CLAUDE.md` and `~/.codex/AGENTS.md`. It never overwrites a path it does not manage; it warns and skips it instead. Rerun it at any time.

`--launchd` adds a LaunchAgent that runs `tools/install --update` every six hours: it pulls this repo and reruns `tools/install`, but only while the clone is on `main`. It logs to `~/Library/Logs/skills-sync.log` with a timestamp on each line.

To move from an older setup (plugins, the skills CLI, or hand-copied skills), run `tools/install --clean` to see what it would remove, then `tools/install --clean --yes` to remove it and install. It removes skills the skills CLI copied in, links that are broken or point into a plugin cache, and anything in the way of a path this repo installs. It keeps your other files, directories, and links, and `~/.claude/skills/synced`, which claude.ai manages.

## One-time setup for the nightly sync

The sync workflow resolves conflicts with Claude, which needs a Claude Code OAuth token. It also opens pull requests, which GitHub Actions may do only once the repo allows it ("Allow GitHub Actions to create and approve pull requests"):

```shell
claude setup-token
gh secret set CLAUDE_CODE_OAUTH_TOKEN --repo Sunnshiine/skills
gh api -X PUT repos/Sunnshiine/skills/actions/permissions/workflow \
  -f default_workflow_permissions=read -F can_approve_pull_request_reviews=true
```

## How sync works

Each source has a `vendor/<source>` branch that holds only that source's upstream files, already placed and renamed the way they appear on `main`. `tools/sync <source>` (or `--all`) rewrites the vendor branch from upstream and merges it into the current branch. Because the vendor branch is the merge base, git keeps my edits and applies upstream's, and reports a conflict only where both changed the same lines.

The [sync workflow](.github/workflows/sync.yml) runs nightly and on demand. A clean merge is pushed to `main`. A conflict goes to a Claude resolver and then to an independent Claude checker. An approved resolution lands on `main`; a rejected one becomes a pull request labeled `sync-needs-human`.

## Customizations

[`CUSTOMIZATIONS.md`](CUSTOMIZATIONS.md) lists every way this repo differs from upstream, one line per change. The conflict resolver reads it to know which edits to keep. Agents editing this repo follow [`AGENTS.md`](AGENTS.md).

## Tests

```shell
tools/sync.test
tools/install.test
```
