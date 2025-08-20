# Git-Cheatsheet
This Repo has all the Quick summary to understand the basics to advance
---

# Git Setup & Workflow Guide

This guide provides a complete reference for setting up and using Git effectively, whether from the terminal or directly in VS Code.

## 🔹 Initial Setup

* Configure user details (`user.name`, `user.email`) for commit attribution.
* Set VS Code as the default Git editor.
* Handle cross-platform line endings with `core.autocrlf`.
* Edit global configuration easily via `git config --global -e`.

## 🔹 Repository Initialization

* Create a repository with `git init` (console) or **Initialize Repository** in VS Code Source Control.

## 🔹 Working with Files

* **Stage & commit** files using `git add` + `git commit` (console) or Source Control panel in VS Code.
* Use `git status` to track staged/unstaged changes.

## 🔹 Reviewing Changes

* Compare changes with `git diff`, `git diff --staged`, or `git diff HEAD`.
* In VS Code, view side-by-side diffs before committing.

## 🔹 Branching Best Practices

* Always keep `main` stable and production-ready.
* Never commit directly to `main`.
* Use descriptive branch names (`feature/login-auth`, `bugfix/payment-error`).
* Regularly sync with `main`, keep branches short-lived, and merge via PRs.

## 🔹 Working with Remotes

* Add, view, change, or remove GitHub remotes (`git remote add origin <url>`).
* Push changes using `git push -u origin main`.

## 🔹 Ignoring Files

* Use `.gitignore` to exclude unnecessary files (logs, cache, `.env`, `dist/`).
* Example:

  ```gitignore
  __pycache__/
  .vscode/
  .env
  dist/
  *.log
  ```

## 🔹 Undoing Changes

* **Revert** (safe): Creates a new commit to undo changes → best for shared repos.
* **Reset** (risky): Moves `HEAD` to a previous commit → useful for local cleanups before pushing.

---

✅ With this setup, you can confidently initialize projects, manage commits, branch safely, work with remotes, ignore sensitive files, and revert or reset changes when needed.

---

Would you like me to make this **short (2–3 paragraphs)** for a neat README introduction, or keep this **sectioned format** as a reference guide inside the README?
