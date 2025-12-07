# Git Town Commands

### Focusing Stacked PR

This guide provides the essential Git Town commands used when working with stacked pull requests. It includes initial setup, branch management, syncing, proposing PRs, and shipping changes.

---

## 1. Initialize Git & Configure Git Town

### **Initialize Git**

```bash
git init
```

### **Configure Git Town Manually (No setup command)**

Git Town settings are configured using `git config`:

```bash
git config git-town.ship-strategy api
git config git-town.forge-type github
git config git-town.github-token <github-token>
```

### **How to Create a GitHub API Token**

1. Go to **GitHub → Settings → Developer settings → Personal access tokens**.
2. Click **“Generate new token (classic)”**.
3. Name it (e.g., `git-town-token`).
4. Enable permission: `repo`.
5. Generate and copy the token.
6. Add it with:

```bash
git config git-town.github-token <github-token>
```

### **View Current Git Town Configuration**

```bash
git town config
```

---

## 2. Create a New Branch from Main

Use when starting a new feature branch.

```bash
git town hack <branch-name>
```

---

## 3. Append a Branch to the Stack

Create a new child branch on top of a parent branch.

```bash
git town append <child-branch>
```

---

## 4. Prepend a Branch Between Parent & Child

Insert a branch in the middle of an existing stack.

```bash
git town prepend <branch-name>
```

---

## 5. View Stack Shape & Switch Branches

### **See visual stack structure**

```bash
git town branch
```

### **Interactive branch switching**

```bash
git town switch
```

---

## 6. Set Parent of Any Branch

Change the parent branch of a stacked branch.

```bash
git town set-parent <branch> <new-parent>
```

---

## 7. Sync Stacked Branches

Rebases all branches in the stack to keep everything up to date.

```bash
git town sync
```

If conflicts occur or after resolving them:

```bash
git town continue
```

---

## 8. Undo the Previously Run Git Town Command

If you made a mistake:

```bash
git town undo
```

---

## 9. Propose a Pull Request

Create a PR for the current branch into its parent branch.

```bash
git town propose
```

---

## 10. Ship a Branch

Merge the current branch into `main` and clean up.

```bash
git town ship
```

This will:

- Merge branch → `main`
- Remove the branch locally
- Re-stack remaining branches automatically

---

Use this reference whenever working with Git Town's stacked PR workflow to keep your branches clean, organized, and efficient.

## 11. Detach a Branch

Detach a branch from its parent and attach it directly to `main`.

```bash
git town detach <branch>
```

This removes the branch from the stack structure.

---

## 12. Compress Commits in a Branch

Squash all commits in the current branch into a single commit.

```bash
git town compress
```

Useful before proposing or shipping a branch to keep history clean.

---

## 13. Merge Current Branch Into Parent

Merge your current branch into its parent branch while keeping the stack structure intact.

```bash
git town merge
```

This will:

- Merge the current branch → parent branch
- Reassign its child branches so their new parent becomes the parent branch

---

## 14. Swap Two Branches

Swap positions of two branches in the stack.

```bash
git town swap <branch-1> <branch-2>
```

Useful to reorder the stack without rewriting history manually.

---
