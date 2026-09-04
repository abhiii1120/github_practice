# Git Cheatsheet

A quick reference for essential Git commands, states, and workflows.

---

## Getting Started

### `git init`
Initializes a new Git repository in the current folder. This is the entry point — it creates a hidden `.git` directory that tracks all changes.

```bash
git init
```

---

## File States

Every file in a Git repo moves through these stages:

| Stage | Symbol | Meaning |
|-------|--------|---------|
| Untracked | `U` | File exists but Git isn't tracking it yet |
| Added (Staged) | `A` | File has been added to the staging area, ready to commit |
| Modified | `M` | A tracked file has been changed since the last commit |
| Commit | ✅ | A saved checkpoint/snapshot of staged changes |

**Flow:** `Untracked → Added (staged) → Committed → Modified → Added → Committed ...`

---

## Basic Workflow Commands

### `git add`
Stages changes so they're ready to be committed.

```bash
git add .              # stage all changed files
git add filename.js    # stage a specific file
```

### `git commit`
Saves a checkpoint of staged changes with a message describing what changed.

```bash
git commit -m "Add login functionality"
```

### `git status`
Shows the current state of your working directory — which files are staged, modified, or untracked.

```bash
git status
```

### `git log`
Displays the commit history.

```bash
git log             # full details (author, date, message)
git log --oneline   # compact, one line per commit
```

---

## Connecting to a Remote Repository

### `git remote add`
Links your local repo to a remote repository (e.g., on GitHub).

```bash
git remote add origin https://github.com/username/repo.git
```

### `git branch -M main`
Renames the current branch to `main`.

```bash
git branch -M main
```

### `git push`
Uploads local commits to the remote repository.

```bash
git push -u origin main   # first push: sets upstream tracking
git push                  # subsequent pushes
```

---

## Branching

### `git branch`
Lists, creates, or manages branches.

```bash
git branch                # list all branches
git branch branch-name    # create a new branch
```

### `git switch`
Switches to a different branch.

```bash
git switch branch-name
```

> Tip: `git checkout branch-name` does the same thing, but `switch` is the newer, clearer command dedicated to branch switching.

---

## Stashing Changes

Stashing temporarily saves uncommitted changes so you can work on something else, then bring them back later.

### `git stash`
Saves your current changes without committing them.

```bash
git stash
```

### `git stash list`
Shows all saved stashes.

```bash
git stash list
```

### `git stash pop`
Re-applies the most recent stash and removes it from the stash list.

```bash
git stash pop
```

### `git stash pop` (specific stash)
Re-applies a specific stash from the list.

```bash
git stash pop stash@{0}
```

---

## Syncing with Remote

### `git fetch`
Downloads commits from a remote branch without merging them into your local branch.

```bash
git fetch origin branchName
```

### Compare local vs remote
Shows commits that exist on the remote branch but not yet in your local `HEAD`.

```bash
git log HEAD..origin/branchName
```

---

## Advanced Commands

### `git rebase`
Reapplies your commits on top of another base branch, creating a cleaner, linear history (as an alternative to merging).

```bash
git rebase main
```

### `git reflog`
Shows a log of everywhere `HEAD` has pointed — useful for recovering "lost" commits after a reset or rebase.

```bash
git reflog
```

### `git cherry-pick`
Applies a specific commit from one branch onto another, without merging the whole branch.

```bash
git cherry-pick <commit-hash>
```

---

## Note on "Fork"

`git fork` isn't an actual Git command — **forking** is a GitHub/GitLab/Bitbucket platform feature (not part of core Git) that creates your own copy of someone else's repository under your account. You fork on the platform's website/UI, then `git clone` your fork locally:

```bash
git clone https://github.com/your-username/forked-repo.git
```

---

## Quick Reference Table

| Command | Purpose |
|---------|---------|
| `git init` | Initialize a repo |
| `git add .` | Stage all changes |
| `git commit -m "msg"` | Commit staged changes |
| `git status` | Check current state |
| `git log --oneline` | View compact history |
| `git remote add origin <url>` | Link to remote repo |
| `git push -u origin main` | Push and set upstream |
| `git branch` | List/create branches |
| `git switch <branch>` | Switch branches |
| `git stash` | Save uncommitted changes |
| `git stash pop` | Restore stashed changes |
| `git fetch origin <branch>` | Download remote commits |
| `git rebase <branch>` | Reapply commits on new base |
| `git reflog` | View HEAD history log |
| `git cherry-pick <hash>` | Apply a specific commit |
