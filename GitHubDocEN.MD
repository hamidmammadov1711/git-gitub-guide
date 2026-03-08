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

| Command                   | Meaning                               | Frequency        |
| ------------------------- | ------------------------------------- | ---------------- |
| `git status`              | Current state                         | every time       |
| `git add .`               | Stage all changes                     | most frequent    |
| `git add file.txt`        | Stage a single file                   | —                |
| `git commit -m "message"`  | Commit changes                        | most frequent    |
| `git commit -am "message"`| add + commit (tracked files)          | frequent         |
| `git push`                | Send to GitHub                        | most frequent    |
| `git pull`                | Fetch from GitHub                     | most frequent    |
| `git fetch`               | See changes, but don't merge          | —                |
| `git log --oneline`       | Commit history                        | —                |
| `git log --graph --all`   | Visual history                        | —                |
| `git branch`              | Show branches                         | —                |
| `git branch new-feature`  | Create new branch                     | —                |
| `git checkout new-feature`| Switch (old)                          | —                |
| `git switch new-feature`  | New command (2026 recommended)        | best practice    |
| `git checkout -b new-feature`| Create + switch                       | most frequent    |
| `git merge feature-branch`| Merge                                 | —                |
| `git rebase main`         | Rebase (clean history)                | —                |
| `git stash`               | Temporarily save changes              | —                |
| `git stash pop`           | Restore changes                       | —                |
| `git reset --hard HEAD~1` | Delete last commit (use with caution!)| —                |
| `git restore file.txt`    | Revert a file to its previous state   | —                |

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

#### 14.1 Branching Strategy

-   **One feature = one branch** (e.g., `feature/user-auth`, `bugfix/login-timeout`)
-   **Branch naming convention:**
    -   `feature/` – new features
    -   `bugfix/` or `fix/` – bug fixes
    -   `hotfix/` – urgent production fixes (branch from `main`)
    -   `docs/` – documentation updates
    -   `refactor/` – code cleanup, no behavior changes

```bash
# Good branch names
git switch -c feature/dark-mode
git switch -c bugfix/cart-calculation-error
git switch -c hotfix/security-vulnerability

# Avoid
git switch -c my-stuff              # too vague
git switch -c feature123            # no context
git switch -c WIP                   # never use this
```

-   **Protect the `main` branch:**
    -   Require pull request reviews before merge
    -   Require at least 1-2 approvals
    -   Block direct pushes to `main`
    -   Require status checks to pass (CI/CD)

#### 14.2 Commit Discipline

-   **Commit message format** (Conventional Commits):
    ```
    type(scope): description
    
    optional body explaining the *why*
    ```

```bash
# Good commits
git commit -m "feat(auth): add two-factor authentication"
git commit -m "fix(api): resolve timeout on user endpoint"
git commit -m "docs: update installation instructions"
git commit -m "refactor(db): optimize query performance"

# Bad commits
git commit -m "fixes stuff"         # vague
git commit -m "asdfgh"              # meaningless
git commit -m "work in progress"    # incomplete
```

-   **Commit size guideline:**
    -   Small, atomic commits (one logical change per commit)
    -   ~5-10 files per commit maximum
    -   Avoid "big bang" commits with 50+ files

-   **Commit frequency:**
    -   Commit after completing a small task
    -   Aim for 3-5 commits per feature branch
    -   Don't wait until the feature is "done" to commit

```bash
# Break work into logical commits
git add src/auth.js
git commit -m "feat(auth): create login form"

git add src/api.js
git commit -m "feat(auth): add API authentication endpoint"

git add tests/auth.test.js
git commit -m "test(auth): add unit tests for login"
```

#### 14.3 Code Review Process

-   **Pull Request expectations:**
    -   Write a clear PR title and description
    -   Link to related issues: "Closes #123"
    -   Keep PRs small (~300-500 lines max)
    -   Wait for at least 1 approval before merging

```markdown
# PR Description Example

## What does this PR do?
Implements user password reset functionality via email.

## Why?
Closes #456 - Users need a way to recover lost passwords.

## How to test?
1. Go to /forgot-password
2. Enter email address
3. Check email for reset link
4. Follow link and set new password

## Screenshots
[If applicable, add screenshots]
```

-   **Review checklist:**
    -   ✅ Code is readable and follows project style
    -   ✅ No debug logs or commented code left behind
    -   ✅ Tests written and passing
    -   ✅ No breaking changes to public APIs
    -   ✅ Performance impact acceptable

#### 14.4 Security & Secrets

-   **Never commit secrets:**
    ```bash
    # Add to .gitignore
    .env
    .env.local
    *.pem
    *.key
    secrets/
    ```

-   **If you accidentally commit a secret:**
    ```bash
    # Immediately rotate the secret (new password, new API key)
    # Then clean Git history:
    git log --oneline | grep "secret"
    git rebase -i <commit-before-secret>
    # Mark "secret commit" as 'drop'
    # Force push (with caution):
    git push origin feature-branch --force-with-lease
    ```

-   **Use environment variables, not hardcoded values:**
    ```javascript
    // Bad
    const API_KEY = "sk-1234567890abcdef";
    
    // Good
    const API_KEY = process.env.API_KEY;
    ```

-   **Use a secrets manager for teams:**
    -   GitHub Secrets (for CI/CD)
    -   HashiCorp Vault
    -   Azure Key Vault
    -   AWS Secrets Manager

#### 14.5 Collaboration Patterns

-   **Pull before you push:**
    ```bash
    git pull origin main
    git push origin feature-branch
    ```

-   **Sync with main daily** (if working on a long-lived branch):
    ```bash
    git fetch origin
    git rebase origin/main
    # or
    git merge origin/main
    ```

-   **Avoid silos** – communicate via PR descriptions, not Slack
-   **Review merged PRs** – learn from teammates' code
-   **Ask for help early** – use draft PRs for work in progress

```bash
# Create a draft PR (GitHub CLI)
gh pr create --draft
```

#### 14.6 History Hygiene

-   **Rebase before merging** (keep history clean):
    ```bash
    git fetch origin
    git rebase origin/main
    # resolve conflicts if any
    git push origin feature-branch --force-with-lease
    ```

-   **Squash commits if feature has too many** (optional):
    ```bash
    git rebase -i origin/main
    # mark commits as 'squash' or 's'
    # keep first commit as 'pick'
    ```

-   **Delete merged branches:**
    ```bash
    # Locally
    git branch -d feature-branch
    
    # On GitHub
    git push origin --delete feature-branch
    ```

-   **Never use `--force` (use `--force-with-lease` instead):**
    ```bash
    # Good – respects remote changes
    git push --force-with-lease
    
    # Dangerous – overwrites everything
    git push --force
    ```

#### 14.7 Performance Optimization

-   **Monitor repo size:**
    ```bash
    git count-objects -v
    du -sh .git
    ```

-   **Avoid large binary files:**
    -   Use Git LFS (Large File Storage) for binaries
    -   Don't commit node_modules/, venv/, .gradle/
    -   Use `.gitignore` aggressively

-   **Shallow clone for big repos** (if cloning is slow):
    ```bash
    git clone --depth 1 https://github.com/username/huge-repo.git
    ```

-   **Use `.gitattributes` for binary files:**
    ```gitattributes
    *.png binary
    *.jpg binary
    *.zip binary
    ```

#### 14.8 Recovery & Debugging

-   **Use `git reflog`** to recover lost commits:
    ```bash
    git reflog
    git reset --hard HEAD@{n}  # where n is the reflog index
    ```

-   **Find the commit that broke something** with `git bisect`:
    ```bash
    git bisect start
    git bisect bad HEAD          # current version is broken
    git bisect good v1.0.0       # this version was good
    # Git jumps to middle commit
    # Test it... if broken: git bisect bad
    # If working: git bisect good
    # ... repeat until found
    git bisect reset
    ```

-   **See who changed a line** with `git blame`:
    ```bash
    git blame src/app.js
    ```

-   **Find a commit by message:**
    ```bash
    git log --grep="login bug"
    git log --all --oneline | grep -i "auth"
    ```

---

#### 14.9 Extra Professional Tips

-   **Branch lifecycle policy:** keep feature branches alive no longer than 2–4 weeks. Use GitHub Actions to label stale branches automatically.
-   **Pre-commit hooks:** enforce formatting and linting with `husky`, `pre-commit`, or Git hooks; run tests before each commit.
-   **Require CI success before merge:** block merges on failing checks; use `branch protection` settings.
-   **GPG-sign your commits:** add `git config --global commit.gpgSign true` for provenance and security.
-   **Dependency update strategy:** use Dependabot or Renovate bots and review each update on its own PR.
-   **Use issue/PR templates:** include sections such as “What/Why/How” and a checklist to standardize contributions.
-   **Schedule `git gc` and prune:** run monthly on large repos (over 1 GB) or set up a cron job.
-   **Use semantic tags:** tag releases (e.g. `v1.2.0`) and generate changelogs automatically.
-   **Maintain a `QUICKSTART.md` or onboarding guide:** ensure new developers can clone and run in <10 minutes.
-   **Enforce signed pushes on critical branches:** set `require signed commits` and `require signed pushes` in repo settings.


### 15. Frequent Problems and Solutions

#### 🔴 CRITICAL (Data Loss Risk)

These problems can permanently lose commits. Act fast!

**Problem: I force-pushed and deleted my teammate's commits**

```bash
# Your teammate can recover using reflog:
git reflog
# Find the lost commit hash
git reset --hard <lost-commit-hash>
git push origin feature-branch --force-with-lease
```

**Prevention:**
- Use `--force-with-lease` instead of `--force`
- Protect `main` branch (prevent force pushes)
- Use protected branches in GitHub settings

---

**Problem: I accidentally deleted a local branch with unpushed commits**

```bash
# Don't panic! Use reflog to recover
git reflog
# Find the branch tip
git checkout -b feature-branch <commit-hash>
```

**Prevention:**
- Push frequently, don't keep work only locally
- Use `git stash` instead of deleting branches

---

**Problem: I committed a database password / API key in a public repo**

```bash
# IMMEDIATELY rotate the secret (new password, new key)

# Then clean it from Git history:
git filter-branch --force --index-filter \
  'git rm --cached --ignore-unmatch secrets.txt' \
  --prune-empty --tag-name-filter cat -- --all

# Force push
git push origin main --force-with-lease

# Notify your team
```

**Prevention:**
- Add `.env` to `.gitignore` BEFORE first commit
- Use GitHub secret scanning (automatic alerts)
- Use a secrets manager in production

---

#### 🔶 HIGH (Collaboration Blocker)

These block your team from working. Urgent but recoverable.

**Problem: `fatal: not a git repository`**

```bash
# You're not in a Git repo:
cd /path/to/correct/folder

# Or initialize a new one:
git init

# Check you're in the right place:
pwd
ls -la | grep .git
```

**Prevention:**
- Always start with `git clone` or `git init`
- Check your current directory before running commands

---

**Problem: `Permission denied` when pushing**

```bash
# Cause 1: Using HTTPS without saved credentials
# Solution: Use SSH instead
git remote set-url origin git@github.com:username/repo.git
# OR create a Personal Access Token (PAT) in GitHub

# Cause 2: SSH key not loaded
ssh -T git@github.com  # test connection
ssh-add ~/.ssh/id_ed25519

# Cause 3: Wrong repo permissions
# Ask repo owner to add you as collaborator
```

**Prevention:**
- Set up SSH keys once (Section 13)
- Use `ssh -T git@github.com` to verify setup

---

**Problem: `Updates were rejected` – can't push**

```bash
# Your remote is ahead of your local branch
git pull --rebase origin main
# Resolve conflicts if any
git push origin feature-branch
```

**Prevention:**
- Always `git pull` before pushing
- Use `git pull --rebase` by default:
  ```bash
  git config --global pull.rebase true
  ```

---

**Problem: Merge conflict in package.json / requirements.txt**

```bash
# These files have auto-generated content and special merge rules
# Option 1: Keep yours (if you updated dependencies)
git checkout --ours package.json

# Option 2: Keep theirs (if they're more recent)
git checkout --theirs package.json

# Option 3: Manually resolve and run:
npm install  # or pip install -r requirements.txt
git add package.json package-lock.json  # or requirements.txt
git commit -m "chore: resolve dependency conflict"
```

**Prevention:**
- Don't update dependencies simultaneously on different branches
- Use separate PRs for dependency updates

---

**Problem: Detached HEAD – I can't commit**

```bash
# You checked out a commit or tag instead of a branch
git log --oneline | head -1  # see where you are

# Solution: Create a branch from current position
git switch -c feature-branch
# Now you can commit normally

# OR go back to main:
git switch main
```

**Prevention:**
- Use `git switch branch-name`, not `git checkout commit-hash`
- Be careful checking out tags (they're not branches)

---

#### 🟡 MEDIUM (Workflow Friction)

These slow you down but aren't critical.

**Problem: I committed a file I didn't mean to – how do I uncommit it?**

```bash
# Commit hasn't been pushed yet:
# Option 1: Undo entire commit (keep changes)
git reset --soft HEAD~1
# Changes are back in staging area

# Option 2: Undo commit and staging (keep file changes)
git reset --mixed HEAD~1

# Option 3: Delete commit completely (lose changes)
git reset --hard HEAD~1

# Commit already pushed – use revert instead:
git revert <commit-hash>
```

---

**Problem: Large binary file bloated my repo**

```bash
# Find the culprit:
git rev-list --all --objects | sort -k2 | tail -10

# Remove it from history:
git filter-branch --tree-filter 'rm -f large-file.zip' --all

# OR: Use Git LFS for future binary files
git lfs install
git lfs track "*.psd"
git add .gitattributes
```

---

**Problem: `git clone` is too slow (large repo)**

```bash
# Clone only recent history:
git clone --depth 1 https://github.com/username/huge-repo.git

# Later, fetch full history:
cd huge-repo
git fetch --unshallow
```

---

**Problem: I want to rename master branch to main**

```bash
# Locally:
git branch -M master main

# On remote:
git push -u origin main

# Tell GitHub to make main the default branch:
# GitHub → Settings → Default branch → select main
```

---

**Problem: `git status` shows files I didn't modify**

```bash
# Cause 1: Line ending differences (CRLF vs LF)
git config core.autocrlf true  # Windows
git config core.autocrlf input  # Mac/Linux

# Cause 2: File permissions changed
git config core.filemode false  # if not needed

# Cause 3: Check what's actually different
git diff filename.txt
```

---

**Problem: Accidentally stashed changes and forgot where**

```bash
# Find all stashes:
git stash list

# Recover the latest:
git stash pop

# Or a specific one:
git stash apply stash@{2}

# See diff before applying:
git stash show stash@{0} -p
```

---

**Problem: I need to undo published commits WITHOUT rewriting history**

```bash
# Use git revert (creates a new commit that undoes changes)
git revert <commit-hash>
git push origin main

# This is safe because it doesn't change history
```

---

#### 🟢 LOW (Learning Curve)

These are confusing but not breaking.

**Problem: I cloned but got `fatal: remote origin already exists`**

```bash
# You ran git init in a cloned folder
git remote -v  # list remotes

# Solution: remove the duplicate
git remote remove origin
git remote add origin https://github.com/username/repo.git
```

---

**Problem: Tag vs Branch – which is which?**

```bash
# Branch: moves when you commit (like a pointer)
#   Use for: active development
git branch feature-feature
git commit -m "add feature"
# Branch tip moves to new commit

# Tag: fixed point in history (like a label)
#   Use for: releases
git tag v1.0.0
# Tag stays at v1.0.0 forever

# List them:
git branch -a   # all branches
git tag -l      # all tags
```

---

**Problem: `Everything up-to-date` but my changes aren't on GitHub**

```bash
# You're on a new local branch that remote doesn't know about
git branch -a  # -a shows all branches

# Solution: push with -u flag to create remote branch
git push -u origin feature-branch
```

---

**Problem: I can't remember what I changed – need a history**

```bash
# See all commits on your branch:
git log --oneline

# See what changed in last 3 commits:
git log -p -3

# See changes since main:
git log main..feature-branch --oneline

# See who changed each line:
git blame filename.txt
```

---

**Problem: Submodules are confusing**

```bash
# Submodules are repos inside repos (advanced, avoid if possible)

# If you inherited a project with submodules:
git clone --recurse-submodules https://github.com/username/repo.git

# Or after cloning:
git submodule update --init --recursive
```

---

**Problem: Cherry-pick – I need one commit from another branch**

```bash
# Current branch: main
# You want commit from feature-branch:

git log feature-branch --oneline  # find the commit hash
git cherry-pick <commit-hash>

# Now that commit is replayed on main
```

---

---

**This documentation is in Markdown format to be "at your fingertips."** You can save it as a `.md` file or open it in VS Code to search through it.

---
