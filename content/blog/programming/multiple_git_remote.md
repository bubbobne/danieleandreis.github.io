---
title: "Managing Multiple Git Remotes"
date: 2026-06-05
draft: false
tags: ["git", "programming"]
categories: ["programming"]
---

When collaborating on open-source projects it is common to work with multiple remotes. Typically:

- **upstream**: the original repository maintained by the project owners  
- **origin**: your personal fork of the repository  

This setup allows you to keep your fork synchronized with the original project while developing and contributing changes.

---

## Configuring the Remotes

Suppose you have already forked a project on GitHub.

Check your current remotes:

```bash
git remote -v
```

Example output:

```text
origin    git@github.com:your-user/project.git (fetch)
origin    git@github.com:your-user/project.git (push)
```

Add the upstream remote:

```bash
git remote add upstream git@github.com:original-user/project.git
```

If you cloned the original repository first, you can rename and add your fork:

```bash
git remote rename origin upstream
git remote add origin git@github.com:your-user/project.git
```

---

## Keeping Your Fork Updated

Before starting new work, synchronize your fork with upstream.

Fetch the latest changes:

```bash
git fetch upstream
```

Switch to your main branch (modern command):

```bash
git switch main
```

Merge upstream changes:

```bash
git merge upstream/main
```

Alternative (cleaner history, often preferred):

```bash
git rebase upstream/main
```

Push updates to your fork:

```bash
git push origin main
```

---

## Creating a New Feature Branch

Start from an updated main branch:

```bash
git switch -c add-new-feature
```

Work on your changes and commit them:

```bash
git add .
git commit -m "Add new feature"
```

Push the branch to your fork:

```bash
git push origin add-new-feature
```

---

## Opening a Pull Request

After pushing your branch, open a Pull Request on GitHub.

Flow:

```text
your-fork/add-new-feature
            ↓
original-project/main
```

---

## Useful Commands

Check configured remotes:

```bash
git remote -v
```

See branch tracking information:

```bash
git branch -vv
```

Inspect a remote in detail:

```bash
git remote show origin
git remote show upstream
```

---

## Typical Workflow

```bash
# Update main branch
git fetch upstream
git switch main
git merge upstream/main
git push origin main

# Create feature branch
git switch -c add-new-feature

# Work
git add .
git commit -m "Add new feature"

# Push branch
git push origin add-new-feature

# Open Pull Request
```

---

## Notes

- Prefer `git switch` over `git checkout` for branch operations.
- Consider `rebase` instead of `merge` for a linear history (depending on team policy).
- Always sync from `upstream` before starting new work.
