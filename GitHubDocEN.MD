**✅ Complete Professional Git + GitHub Documentation (2026 version)**
This document is designed for learning Git and GitHub workflows **without skipping any details**, using the **terminal, VS Code, WebStorm, PyCharm, or any other IDE**.

### Table of Contents

1.  Introduction and Terminology
2.  Installation and Initial Configuration
3.  Creating a Local Repository
4.  Uploading a Project to GitHub for the First Time (full step-by-step)
5.  Cloning an Existing Project from GitHub
6.  Most Commonly Used Commands (Cheat Sheet)
7.  Branching and Pull Requests (PR)
8.  Synchronizing Changes (Push / Pull / Fetch)
9.  Resolving Conflicts
10. .gitignore and File Management
11. Git in VS Code + IDEs (the easiest way)
12. GitHub CLI (`gh`) – The fastest way in 2026
13. SSH Setup (recommended)
14. Best Practices and Security
15. Frequently Asked Questions and Solutions

---

### 1. Introduction and Terminology

-   **Git** – local version control system (runs on your computer)
-   **GitHub** – remote server – stores your code, allows for team collaboration
-   **Repository (Repo)** – project folder
-   **Main / Master** – the primary branch (**main** is the standard in 2026)
-   **Commit** – a "snapshot" of changes
-   **Push** – sending local changes to GitHub
-   **Pull** – bringing changes from GitHub to your local computer

---

### 2. Installation and Initial Configuration (done once)

**In the Terminal (Git Bash, PowerShell, Terminal, VS Code Terminal):**

```bash
# Check if Git is installed
git --version

# User information (mandatory!)
git config --global user.name "Your Name Surname"
git config --global user.email "youremail@gmail.com"

# Set the default branch to main
git config --global init.defaultBranch main

# Editor choice (if you use VS Code)
git config --global core.editor "code --wait"
```

**In VS Code**:

-   `Ctrl + Shift + P` → Search for "Git: Enable" → activate it.

---

### 3. Creating a Local Repository

```bash
cd /path/to/your/project
git init                  # creates a new repo
git status                # check status
```

---

### 4. Uploading a Project to GitHub for the First Time (Most Detailed Step-by-Step)

#### Step 1: Create a repo on GitHub

1.  github.com → New repository
2.  Repository name: `my-awesome-project`
3.  Description (optional)
4.  Choose **Public / Private**
5.  **Add a README file** → **DO NOT CHECK THIS!**
6.  **Create repository**

#### Step 2: In the Terminal

```bash
cd my-awesome-project

git init
git add .                    # add all files (or git add -A)
git commit -m "Initial commit"

# Add remote (HTTPS)
git remote add origin https://github.com/username/my-awesome-project.git

# If the branch is not main
git branch -M main

# First push
git push -u origin main
```

**Easier with SSH (recommended):**

```bash
git remote set-url origin git@github.com:username/my-awesome-project.git
git push -u origin main
```

---

### 5. Cloning an Existing Project from GitHub

```bash
git clone https://github.com/username/project-name.git
# or SSH
git clone git@github.com:username/project-name.git
```

---

### 6. Most Commonly Used Commands (Cheat Sheet)

| Command                 | Meaning                               | Frequency        |
| ----------------------- | ------------------------------------- | ---------------- |
| `git status`            | Current state                         | every time       |
| `git add .`             | Stage all changes                     | most frequent    |
| `git add file.txt`      | Stage a single file                   | —                |
| `git commit -m "mesaj"` | Commit changes                        | most frequent    |
| `git commit -am "mesaj"`| add + commit (tracked files)          | frequent         |
| `git push`              | Send to GitHub                        | most frequent    |
| `git pull`              | Fetch from GitHub                     | most frequent    |
| `git fetch`             | See changes, but don't merge          | —                |
| `git log --oneline`     | Commit history                        | —                |
| `git log --graph --all` | Visual history                        | —                |
| `git branch`            | Show branches                         | —                |
| `git branch yeni-ozellik` | Create new branch                     | —                |
| `git checkout yeni-ozellik` | Switch (old)                          | —                |
| `git switch yeni-ozellik` | New command (2026 recommended)        | best practice    |
| `git checkout -b yeni-ozellik`| Create + switch                       | most frequent    |
| `git merge feature-branch`| Merge                                 | —                |
| `git rebase main`       | Rebase (clean history)                | —                |
| `git stash`             | Temporarily save changes              | —                |
| `git stash pop`         | Restore changes                       | —                |
| `git reset --hard HEAD~1`| Delete last commit (use with caution!)| —                |
| `git restore fayl.txt`  | Revert a file to its previous state   | —                |

---

### 7. Branching and Pull Request (PR)

```bash
git switch -c feature/login-page     # new branch
# ... write your code ...
git add .
git commit -m "feat: add login page"
git push -u origin feature/login-page
```

**On GitHub:**

1.  Repo → Pull requests → New pull request
2.  `feature/login-page` → `main`
3.  Review + Merge

---

### 8. Synchronization

```bash
git pull origin main                 # safest
# or
git fetch origin
git merge origin/main
```

---

### 9. Resolving Conflicts

VS Code opens automatically → choose which change to keep → `Accept Current Change` / `Accept Incoming Change`.

In the terminal:

```bash
git mergetool   # or edit manually
git add .
git commit      # without a message (merge commit)
```

---

### 10. .gitignore (important!)

Create a `.gitignore` file in the project directory:

```gitignore
# Node.js
node_modules/
dist/
.env

# Python
__pycache__/
venv/
*.pyc

# VS Code
.vscode/
*.code-workspace

# OS
.DS_Store
Thumbs.db
```

---

### 11. Git in VS Code (The Easiest Way)

-   Left panel → **Source Control** (third icon)
-   Changes appear automatically
-   Stage → Commit → Sync (Pull + Push in one button)
-   `GitLens` extension (must-install!) – history, blame, PR integration

**With VS Code Command Palette (Ctrl+Shift+P)**:

-   `Git: Commit`
-   `Git: Push`
-   `Git: Pull`
-   `Git: Create Branch`
-   `Git: Checkout to...`

---

### 12. GitHub CLI (`gh`) – The fastest in 2026

```bash
# Installation (once)
# Windows: winget install --id GitHub.cli
# Mac: brew install gh
# Linux: sudo apt install gh

gh auth login
gh repo create my-project --public --source=. --remote=origin --push
gh pr create --fill
gh pr merge
```

---

### 13. SSH Setup (Recommended)

```bash
ssh-keygen -t ed25519 -C "youremail@gmail.com"
# Enter → Enter → Enter

cat ~/.ssh/id_ed25519.pub     # copy this

# GitHub → Settings → SSH and GPG keys → New SSH key → paste it
```

---

### 14. Best Practices (Professional Level)

-   Separate branch for each small feature
-   Commit messages: `type: description` (feat:, fix:, docs:, refactor:)
-   **Never** edit the `main` branch directly
-   `git pull` every day
-   Never commit the `.env` file
-   Use `git rebase` (for a clean history)

---

### 15. Frequent Problems and Solutions

| Problem                                     | Solution                                                  |
| ------------------------------------------- | --------------------------------------------------------- |
| `fatal: not a git repository`               | Run `git init` or `cd` to the correct folder              |
| `Permission denied`                         | Use SSH or create a PAT                                   |
| `Updates were rejected`                     | `git pull --rebase` then `git push`                       |
| I want to rename master to main             | `git branch -M main`                                      |
| `Everything up-to-date` but not on GitHub   | `git push -u origin main --force-with-lease` (with caution) |

---

**This documentation is in Markdown format to be "at your fingertips."** You can save it as a `.md` file or open it in VS Code to search through it.

---
