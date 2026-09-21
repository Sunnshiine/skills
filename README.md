# skills

My personal agent skills. Most of them start as copies of other people's skill repos. I edit the copies in place, and `tools/sync` merges upstream updates without losing my edits.

## Sources

`sources.json` lists every upstream repo, the ref to follow, the directory its copy lives in, and which upstream paths to carry.

| Source | Upstream | Carried | Lives in |
| --- | --- | --- | --- |
| `pstack-claude` | [michael-denyer/pstack-claude](https://github.com/michael-denyer/pstack-claude) | the whole repo | `sources/pstack-claude` |
| `mattpocock` | [mattpocock/skills](https://github.com/mattpocock/skills) | 8 skills | `sources/mattpocock` |

The `mattpocock` skills are `improve-codebase-architecture`, `grill-with-docs`, `writing-for-agents`, `pr`, and `retro`, plus the three skills they call (`codebase-design`, `domain-modeling`, `grilling`).

Both upstreams are MIT licensed. Their license and notice files are kept inside each source directory.

## Install in Claude Code

```shell
/plugin marketplace add Sunnshiine/skills
/plugin install pstack@sunny-skills
/plugin install mattpocock@sunny-skills
```

Uninstall the original `pstack` and Matt Pocock plugins first. Two installed copies of the same skill names collide.

## How syncing works

Each source has a branch named `vendor/<source>`. That branch holds only unmodified upstream snapshots, at the same paths the files have on `main`. `tools/sync` commits a new snapshot to the vendor branch, then merges the vendor branch into your current branch.

Because the vendor branch is the merge base, git's three-way merge keeps your edits and applies upstream's. Git reports a conflict only where you and upstream changed the same lines.

## Pull upstream changes

Requires `git` 2.42 or later, `jq`, and `tar`.

1. Start a branch, so that the update arrives as a pull request you can review.

   ```shell
   git switch -c sync/pstack-claude
   ```

2. Run the sync. The second argument is optional and pins a branch, tag, or commit SHA.

   ```shell
   tools/sync pstack-claude
   ```

3. If git reports conflicts, resolve them, then run `git add` and `git commit`. To back out, run `git merge --abort`.

4. To reject part of an upstream change, revert those lines on the sync branch and commit. Later syncs leave your version alone until upstream changes the same lines again.

5. If the source is `pstack-claude`, regenerate its stamped files and run its tests.

   ```shell
   cd sources/pstack-claude && bun tools/generate.mjs && bun test tests/
   ```

6. Push the branch and open a pull request.

To see what upstream changed before you merge anything, run `tools/sync <source> --no-merge`, then `git diff HEAD...vendor/<source>`.

## See your modifications

```shell
git diff vendor/pstack-claude main -- sources/pstack-claude
git diff vendor/mattpocock main -- sources/mattpocock
```

## Add a source or a skill

1. Add an entry to `sources.json`, or add a path to an existing entry's `paths`. A path that does not exist upstream makes the sync fail and name the path. The same failure tells you when upstream renames or moves a skill you carry.
2. Run `tools/sync <source>`.
3. List any new skill in `.claude-plugin/marketplace.json`.

## Test the sync tool

`tools/sync.test` builds throwaway repos in a temp directory and needs no network.

```shell
tools/sync.test
```
