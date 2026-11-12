# Git and GitHub

Git is a distributed version control system that records project changes. GitHub hosts Git repositories online and provides collaboration features such as pull requests and code review.

## 1. Install Git

- **Windows:** https://git-scm.com/downloads
- **Ubuntu / Debian:** `sudo apt update` then `sudo apt install git`
- **macOS:** `brew install git`

Check installation:

```bash
git --version
```

## 2. Configure Git

These settings identify the author of commits; they do **not** authenticate you to GitHub.

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global --list
```

## 3. Create a repository

```bash
mkdir my-project
cd my-project
git init
```

- `mkdir` creates a folder; `cd` moves into it.
- `git init` initializes a local repository and creates the hidden `.git` directory.

Git has three main areas: **working directory** (files being edited), **staging area** (selected changes), and **repository** (committed history).

## 4. Basic workflow

```bash
git status
git add main.py
git commit -m "Add main program"
git push
```

- `git status` shows untracked, modified, and staged files.
- `git add main.py` stages one file.
- `git add .` stages changes in the current directory.
- `git add file1.py file2.py` stages selected files.
- `git add *.py` stages matching Python files.
- `git commit -m "message"` records staged changes.
- If a file changes after `git add`, stage it again.
- `git push` sends commits to a configured remote.

Good commit messages are short and specific: `Add input validation`, `Fix division by zero error`, `Update project documentation`.

## 5. Inspect history and changes

```bash
git log
git log --oneline
git diff
git diff --staged
git diff HEAD
git ls-files
```

- `git log` shows commit hash, author, date, and message.
- `git log --oneline` shows compact one-line history.
- `git diff` shows unstaged changes.
- `git diff --staged` shows staged changes.
- `git diff HEAD` compares tracked working changes with the current commit.
- `git ls-files` lists files known to Git's index.

## 6. Ignore, rename, remove and restore

A `.gitignore` file lists untracked files/directories Git should ignore. Example:

```gitignore
__pycache__/
*.pyc
.env
*.log
data/
```

Commands:

```bash
git mv old.py new.py
git rm old.py
git restore --staged main.py
git restore main.py
```

- `git mv` moves/renames a tracked file and stages the operation.
- `git rm` removes a tracked file and stages removal.
- `git restore --staged main.py` unstages it but keeps working changes.
- `git restore main.py` discards unstaged changes to that tracked file. **This can lose work.** Inspect with `git diff` first.

## 7. Revert a commit

```bash
git log --oneline
git revert COMMIT_ID
```

`git revert` creates a new commit that reverses an earlier commit while preserving history.

## 8. Connect to GitHub

Create an empty repository on GitHub, then connect it:

```bash
git remote add origin https://github.com/USERNAME/PROJECT.git
git remote -v
git branch -M main
git push -u origin main
```

- `git remote add origin URL` adds a remote named `origin`.
- `git remote -v` shows fetch and push URLs.
- `git branch -M main` renames the current branch to `main`.
- `git push -u origin main` pushes `main` and sets its upstream; later use `git push`.

## 9. Clone, fetch and pull

```bash
git clone https://github.com/USERNAME/PROJECT.git
git fetch origin
git pull
git pull origin main
```

- `git clone URL` downloads a remote repository and its history.
- `git fetch origin` downloads updates without merging them.
- `git pull` fetches and integrates updates into the current branch.
- `git pull origin main` pulls specifically from `origin/main`.

## 10. Branches and merging

```bash
git branch
git branch feature-login
git switch feature-login
git switch main
git switch -c feature-login
git merge feature-login
```

- `git branch` lists local branches.
- `git branch feature-login` creates a branch.
- `git switch feature-login` switches to an existing branch.
- `git switch -c feature-login` creates and switches to a branch.
- `git merge feature-login` merges it into the current branch.

Typical merge:

```bash
git switch main
git merge feature-login
```

If there is a conflict, edit the affected file to resolve the marked sections, then stage and commit the resolution:

```bash
git add main.py
git commit -m "Resolve merge conflict"
```

## 11. Merge vs rebase

```bash
git switch main
git merge feature
git switch feature
git rebase main
```

- **Merge** combines branch histories and may create a merge commit.
- **Rebase** replays feature commits on a new base and creates new commit IDs.
- Avoid rebasing commits other people already depend on unless the team agrees.

## 12. Tags and releases

```bash
git tag
git tag -a v1.0.0 -m "Version 1.0.0"
git show v1.0.0
git push origin v1.0.0
```

- `git tag` lists tags.
- `git tag -a ... -m ...` creates an annotated tag.
- `git show v1.0.0` displays tag details and its commit.
- `git push origin v1.0.0` publishes the tag.
- GitHub Releases can use tags to identify published versions.

## 13. Pull requests

A **pull request** is a GitHub feature for proposing, discussing, reviewing, and merging branch changes. It is different from `git pull`, which downloads and integrates remote changes into a local branch.

## 14. Complete calculator example from the lecture

```bash
mkdir calculator
cd calculator
git init

# Create main.py, then:
git status
git add main.py
git status
git commit -m "Add initial calculator"
git log --oneline

# Publish main:
git branch -M main
git remote add origin REPOSITORY_URL
git push -u origin main

# Work on a feature:
git switch -c feature-subtraction
# Edit main.py, then:
git add main.py
git commit -m "Add subtraction feature"
git push -u origin feature-subtraction

# Update local main:
git switch main
git pull origin main
```

## 15. Common issues and good habits

- **Untracked file:** stage it using `git add`.
- **Wrong branch:** check `git branch`.
- **Nothing to commit:** inspect `git status` and staged changes.
- Check `git status` before committing; review staged changes with `git diff --staged`.
- Make small commits with meaningful messages.
- Ignore generated files and local settings using `.gitignore`.
- Never commit passwords, API keys, or tokens. Adding a secret to `.gitignore` does not remove it if it was already committed.
