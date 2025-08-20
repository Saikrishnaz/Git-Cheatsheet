# Git Initial Setup

This guide explains the basic Git configuration commands used during the initial setup.

---

## 1. Set User Details

```bash
git config --global user.name "Username"
git config --global user.email "something@gmail.com"
```

- **Purpose:** Sets your name and email, which Git uses to identify you as the author of commits.  
- **Why important:** Every commit stores author information. Without this, commits may appear anonymous or incorrect.  
- **`--global`:** Applies these settings system-wide. For project-specific details, omit `--global` and run the command inside the repo.

---

## 2. Set Default Editor

```bash
git config --global core.editor "code --wait"
```

- **Purpose:** Makes **Visual Studio Code** the default editor Git opens when a commit message or conflict resolution is required.  
- **Why `--wait`:** Ensures Git waits until VS Code is closed before continuing.  
- **Why useful:** Avoids Git opening editors like Vim, making it easier to write commit messages.

---

## 3. Handle Line Endings Across OS

```bash
git config --global core.autocrlf true    # Windows
git config --global core.autocrlf input   # macOS/Linux
```

- **Purpose:** Keeps line endings consistent across operating systems.  
- **Why important:** Prevents unnecessary file changes caused by Windows (`CRLF`) vs Linux/macOS (`LF`) differences.  
- **Options:**  
  - `true` → Converts LF to CRLF on checkout (Windows).  
  - `input` → Commits as LF, keeps LF on checkout (Linux/macOS).  
  - `false` → No automatic conversion.

---

✅ With this setup:  
1. Commits are correctly attributed to you.  
2. VS Code opens for editing commit messages/conflicts.  
3. Cross-platform line ending issues are minimized.


## 4. Edit Global Git Configuration

```bash
git config --global -e
```

- **Purpose:** Opens the global Git configuration file (`~/.gitconfig`) in your default editor.  
- **Why useful:**  
  - Lets you view and edit all global Git settings in one place.  
  - Useful for quickly changing your name, email, editor, aliases, or line-ending preferences.  
- **Example:**  
  You might see something like:

  ```ini
  [user]
      name = YourName
      email = you@example.com
  [core]
      editor = code --wait
      autocrlf = true
  ```

---

✅ With this setup:  
1.  You can easily manage all Git settings from one place.


## 5. Initialize a New Git Repository

You can initialize Git for a new project in two ways:

### a) From the Console

```bash
git init
```

- **Purpose:** Creates a new Git repository in the current directory.  
- **What happens:** A hidden `.git` folder is created, where Git stores all version history and configuration for the project.  
- **When to use:** Run this once in the root folder of your project to start tracking files with Git.

---

### b) From VS Code Source Control

1. Open your project in **VS Code**.  
2. Go to the **Source Control tab** (left sidebar with a branch icon).  
3. If the folder is not yet a Git repository, you’ll see a **"Initialize Repository"** button.  
4. Click it → VS Code will run `git init` in the background.  

- **Why useful:** Allows you to initialize Git without leaving the editor.  
- **Tip:** After initializing, you can stage/commit files directly from the Source Control panel.

---

✅ With this setup:  
1. Repositories can be initialized from either the terminal or directly from VS Code.

## 6. Add, Stage, and Commit Files

Once a repository is initialized, you need to add and commit files.

### a) From the Console

```bash
git add file1.txt file2.txt     # Stage specific files
git add .                       # Stage all files in the directory
git status                      # Check which files are staged/unstaged
git commit -m "Initial commit"  # Commit staged changes with a message
```

* **`git add`:** Moves files into the staging area (prepares them for commit).
* **`git commit`:** Saves a snapshot of staged changes to the repository history.
* **`git status`:** Shows the state of working directory and staging area.

---

### b) From VS Code Source Control

1. Open the **Source Control tab**.
2. You will see all **untracked/modified files** listed.
3. Click the **`+` (plus)** icon next to a file to **stage** it.

   * Or click the **`+`** at the top to stage all files.
4. Enter a **commit message** in the text box at the top.
5. Click the **✔ Commit** button (or press **Ctrl+Enter** / **Cmd+Enter**).

* **Tip:** You can stage multiple files and then commit them all at once.
* **Benefit:** Everything can be done without using the terminal.

---

✅ With this setup:

1. Files can be added, staged, and committed from both console and VS Code Source Control.

---


---

## 7. View Changes with Git Diff

### a) From the Console

```bash
git diff             # Compare working directory with staging area
git diff --staged    # Compare staged changes with last commit
git diff HEAD        # Compare working directory with last commit
```

* **Purpose:** Shows what has changed in your files.
* **When to use:** Always check `git diff` before committing to review changes.

---

### b) From VS Code

1. Go to **Source Control tab**.
2. Click a file under **Changes** or **Staged Changes**.
3. VS Code shows a **side-by-side diff**: old vs new.

---

## 8. Branching Best Practices

### a) Why Use Branches?

* Work on **features, fixes, or experiments** separately.
* Keep the `main` branch always **stable and production-ready**.
* Avoid breaking shared code while developing.

---

### b) How to Create and Switch Branches

```bash
git branch feature-login       # Create a new branch
git checkout feature-login     # Switch to the branch
# OR (shortcut)
git checkout -b feature-login
```

---

### c) Best Practices

1. **Never commit directly to `main`/`master`**

   * Keeps production code clean and stable.
   * Reduces risk of errors reaching deployment.

2. **Use descriptive branch names**

   * `feature/login-auth`
   * `bugfix/payment-error`
   * `hotfix/security-patch`

3. **Sync regularly with main**

   ```bash
   git checkout main
   git pull origin main
   git checkout feature-login
   git merge main
   ```

4. **Keep branches short-lived** → merge them once tested.

5. **Use Pull Requests (PRs)** for reviews and safe merging.

---

✅ With this setup you can:

1. Use `git diff` to review before committing.
5. Follow branching best practices to keep code clean and stable.

---


## 9. Working with Remotes

### a) What is a Remote?

- A **remote** is a reference to a repo hosted elsewhere (e.g., GitHub).  
- Lets you push/pull changes.  

### b) Add a Remote

```bash
git remote add origin https://github.com/username/repo.git
git push -u origin main
```

### c) View Existing Remotes

```bash
git remote -v
```

### d) Change a Remote URL

```bash
git remote set-url origin https://github.com/username/new-repo.git
```

### e) Remove a Remote

```bash
git remote remove origin
```

### f) Reinitialize Remote

```bash
git remote remove origin
git remote add origin https://github.com/username/new-repo.git
```

---

## 10. Ignoring Files with `.gitignore`

### Purpose
- Prevents unnecessary or sensitive files from being tracked by Git.  
- Common for files like logs, build artifacts, environment files, and system files.  

### Example `.gitignore`

```
# Ignore Python cache
__pycache__/

# Ignore VS Code settings
.vscode/

# Ignore environment files
.env

# Ignore build outputs
dist/
*.log
```

### Commands

```bash
echo "__pycache__/" >> .gitignore
git rm -r --cached __pycache__/
git commit -m "Update .gitignore to exclude __pycache__"
```

---

## 11. Going Back to Previous Commits

Sometimes you need to undo changes. Git provides two main commands: **revert** and **reset**.  

### a) `git revert` (Safe)

```bash
git revert <commit_hash>
git revert ee1f523
```

- Creates a **new commit** that undoes changes from the given commit.  
- Keeps history intact.  
- Best for shared branches.  

### b) `git reset` (Dangerous if pushed)

```bash
git reset --soft <commit_hash>   # Keep changes staged
git reset --mixed <commit_hash>  # Default, keep changes unstaged
git reset --hard <commit_hash>   # Discard everything after commit
```
- Moves `HEAD` back to the given commit.  
- Can rewrite history → use carefully!  
```bash
 git reset --soft HEAD~1 
 git reset --mixed HEAD~1
 git reset --mixed b111afc # can aslo jump to a specific commit
 git reset --hard HEAD~1
```

### c) Choosing Between Revert and Reset

- **Use `revert`** when changes are already pushed to a shared branch (keeps history safe).  
- **Use `reset`** for local clean-ups before pushing (rewrites history).  

---
