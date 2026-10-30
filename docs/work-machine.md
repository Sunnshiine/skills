# Install the course skills on a work computer

Emil's course skills install from his server with a personal token, so they never live in this repo. The token grants your course access, and its first half is your email in base64. Treat it like a password. Check that your employer allows a personal credential on the machine before you start.

## Check the network

The installer downloads from npm and fetches skills from `aiforui.vercel.app`, not `aiforui.dev`. Check that the machine reaches both hosts:

```shell
curl -sI https://registry.npmjs.org | head -1
curl -sI https://aiforui.vercel.app | head -1
```

Each command prints an HTTP status line. If either one times out or returns a proxy block page, stop here. The installer cannot work on this network.

## Move the token

Copy the token from a channel that keeps no copy: a personal password manager, or a one-time secret link that expires after one view. Don't send it through Slack, work email, or anything else your employer logs.

## Store the token in Keychain

Run this command and paste the token at the prompt:

```shell
security add-generic-password -a "$USER" -s aiforui-token -w
```

The prompt keeps the token out of your shell history. To replace a stored token, add `-U` to the same command.

## Install

1. Clone this repo and run `tools/install`, as the README describes. The clone needs no GitHub login.
2. Run `tools/install-course-skills`.

The script reads the token from Keychain and runs a pinned version of `@aiforui/install` for every agent it detects. Skills land in `~/.claude/skills` and `~/.codex/skills`, all named `emil-*`.

To check the result, run `ls ~/.claude/skills | grep '^emil-'`. It lists 28 skills, plus `emil-design-eng` from this repo.

To update the skills, rerun `tools/install-course-skills`.

## Know the limits

- The installer accepts the token only as a flag, so the token is visible in the process list while the installer runs.
- `npx` runs code from npm. The script pins the installer version. Read the new `bin/cli.js` before you raise the pin.
- `tools/install --clean` leaves the course skills alone, because they are real directories that this repo does not install.

If the token leaks, ask the course for a new one and store it with `-U`.
