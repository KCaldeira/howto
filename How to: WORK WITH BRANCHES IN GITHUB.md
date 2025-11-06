# How to Work with Branches in GitHub

This guide describes a simple, reliable branching workflow for small projects with a few collaborators.  
It assumes you already have a local Git repository connected to a remote GitHub repository.

---

## Basic Workflow Overview

1. **Keep `main` stable**  
   The `main` branch should always contain working, tested code.  
   Changes are developed in separate *feature branches* and merged into `main` only when ready.

2. **Each change gets its own branch**  
   Create a new branch for each feature or fix, using descriptive names such as `ken-dev`, `add-readme`, or `bugfix/login-timeout`.

3. **Commit and push regularly**  
   Make small, logical commits, and push your branch to GitHub so others can see your progress or collaborate.

4. **Use Pull Requests (PRs)**  
   When your branch is ready, open a PR on GitHub to merge it into `main`. Review and approve before merging.

---

## Common Commands

### 1. Clone a Repository
```bash
git clone https://github.com/username/repo-name.git
cd repo-name
```

### 2. Check Current Branch
```bash
git branch
```

### 3. Create and Switch to a New Branch
```bash
git checkout -b my-feature
```
This creates a new branch from your current branch (usually `main`) and switches to it.

### 4. See All Branches (Local and Remote)
```bash
git branch -a
```

### 5. Make Changes and Commit
```bash
git add .
git commit -m "Add feature X"
```

### 6. Push Branch to GitHub
```bash
git push -u origin my-feature
```
The `-u` flag links your local branch with the remote one so future `git push`/`git pull` commands work without arguments.

### 7. Update Your Branch with Latest `main`
Before merging, keep your branch up to date:
```bash
git fetch origin
git checkout my-feature
git merge origin/main
# or alternatively, rebase for a cleaner history
git rebase origin/main
```

### 8. Merge Branch into `main`
Once your feature is complete and reviewed:
```bash
git checkout main
git pull origin main          # Make sure main is up to date
git merge my-feature
git push origin main
```

Optionally, delete the branch:
```bash
git branch -d my-feature      # Delete local branch
git push origin --delete my-feature  # Delete remote branch
```

---

## Recommended Simple Workflow (for Small Teams)

1. **Start from main**
   ```bash
   git checkout main
   git pull
   ```

2. **Create your branch**
   ```bash
   git checkout -b ken-dev
   ```

3. **Work and commit**
   ```bash
   git add .
   git commit -m "Describe what you did"
   git push -u origin ken-dev
   ```

4. **Open a Pull Request on GitHub**
   - Go to the repository page.
   - Click **Compare & pull request**.
   - Review, discuss, and merge when approved.

5. **After merging, clean up**
   ```bash
   git checkout main
   git pull
   git branch -d ken-dev
   git push origin --delete ken-dev
   ```

---

## Notes

- Use `git status` frequently — it’s your friend.
- Small, frequent commits make collaboration easier.
- If you get merge conflicts, resolve them locally, test, then continue with `git merge --continue` or `git rebase --continue`.
- Keep branches short-lived — merge or close them promptly to avoid drift.

---

## (Optional) Visual Overview

```
          +------------------+
          |     main         |
          +------------------+
                   |
                   |  create branch
                   v
          +------------------+
          |   ken-dev        |
          +------------------+
                   |
                   |  develop, commit, push
                   v
          +------------------+
          |  pull request    |
          +------------------+
                   |
                   |  review, merge
                   v
          +------------------+
          |     main         |
          +------------------+
```
