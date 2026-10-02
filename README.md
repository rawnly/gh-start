# gh-start

A small Bash script that starts work on a GitHub issue: it creates (or checks out) a linked feature branch and assigns the issue to you.

## What it does

Given an issue number, `gh-start`:

1. Fetches the issue title and number via `gh`.
2. Builds a branch name `feature/<number>_<title>`. The title is lowercased, spaces become `_`, and non-word characters are stripped.
3. If that branch already exists on `origin`, it fetches it and switches to a local tracking branch.
4. Otherwise it creates the branch with `gh issue develop`, based on the repo's default branch, and checks it out.
5. Assigns the issue to you (`@me`).

Example: issue `42` titled "Fix Login Bug!" gives `feature/42_fix_login_bug`.

## Requirements

- [`gh`](https://cli.github.com/), authenticated (`gh auth login`)
- [`jq`](https://jqlang.github.io/jq/)
- `git`, with an `origin` remote and `refs/remotes/origin/HEAD` set

## Installation

```sh
gh extension install rawnly/gh-start
```

## Usage

Run from inside a clone of the repository:

```sh
gh start <issue-number>
```

## Development

Lint with [mise](https://mise.jdx.dev/) and ShellCheck:

```sh
mise run lint
```
