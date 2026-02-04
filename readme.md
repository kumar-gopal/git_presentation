---

# 📘 Git & GitHub Complete Setup + Daily Commands Guide (for smooth workflow)
---

## 🔹 1. GitHub Account Setup (One-Time)

### Step 1: Create GitHub Account

* Visit: [https://github.com](https://github.com)
* Sign up and verify email

---

### Step 2: Install Git

```bash
git --version
```

If not installed:

```bash
sudo apt install git -y   # Ubuntu
brew install git          # macOS
```

---

### Step 3: Configure Git Identity

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@gmail.com"
```

Verify:

```bash
git config --list
```

---

### Step 4: Setup SSH (Recommended for Production)

```bash
ssh-keygen -t ed25519 -C "your_email@gmail.com"
cat ~/.ssh/id_ed25519.pub
```

Add the key to:
GitHub → Settings → SSH & GPG Keys

Test:

```bash
ssh -T git@github.com
```

---

## 🔹 2. Basic Repository Commands

### Initialize Repository

```bash
git init
```

**Analogy:**

> Creating a new project folder and telling Git: “Start tracking everything here.”

---

### Clone Existing Repository

```bash
git clone git@github.com:username/repo-name.git
```

**Analogy:**

> Downloading the project from GitHub to your local system.

---

## 🔹 3. Branch Management (Very Important)

### Create a New Branch

```bash
git checkout -b feature/login
```

**When to use:**

* Working on a new feature
* Fixing a bug

**Analogy:**

> Taking a separate notebook to experiment without touching the main book.

---

### Switch Branch

```bash
git checkout main
```

---

### Delete Branch

```bash
git branch -d feature/login
```

**When to use:**

* Feature is merged
* Branch no longer needed

**Analogy:**

> Throwing away a rough draft after final submission.

---

## 🔹 4. Daily Workflow Commands

### Check Status

```bash
git status
```

**Analogy:**

> Checking what files you edited before submitting homework.

---

### Stage Files

```bash
git add .
```

**Analogy:**

> Selecting files you want to submit.

---

### Commit Changes

```bash
git commit -m "feat: add login API"
```

**Analogy:**

> Saving a checkpoint with a message.

---

## 🔹 5. Before Push vs After Push

### BEFORE PUSH (Safe Zone)

#### Undo Last Commit (Keep Code)

```bash
git reset --soft HEAD~1
```

**Use when:**

* Wrong commit message
* Small mistake

**Analogy:**

> Editing a document before sending it.

---

### AFTER PUSH (Production Rules)

#### Safe Undo (Recommended)

```bash
git revert <commit-id>
git push origin main
```

**Use when:**

* Code already shared
* Team project
* Production branch

**Analogy:**

> Sending a correction email instead of deleting the original one.

---

#### Force Push (Dangerous)

```bash
git reset --hard HEAD~1
git push --force-with-lease
```

**Use ONLY when:**

* Your own branch
* No one else pulled

**Analogy:**

> Rewriting shared documents — risky.

---

## 🔹 6. Pull vs Fetch

### git pull

```bash
git pull origin main
```

**What it does:**

* Fetch + merge

**Analogy:**

> Downloading changes and applying them immediately.

---

### git fetch

```bash
git fetch origin
```

**What it does:**

* Downloads changes
* Does NOT merge

**Analogy:**

> Checking updates without installing them.

---

## 🔹 7. Merge vs Rebase

### git merge

```bash
git merge feature/login
```

**When to use:**

* Team collaboration
* Preserve history

**Analogy:**

> Combining two documents with full history.

---

### git rebase

```bash
git rebase main
```

**When to use:**

* Clean commit history
* Feature branches

**Analogy:**

> Rewriting your draft neatly before final submission.

---

## 🔹 8. Stash (Temporary Save)

```bash
git stash
git stash pop
```

**When to use:**

* Urgent branch switch
* Incomplete work

**Analogy:**

> Putting unfinished work in a drawer temporarily.

---

## 🔹 9. Reflog (Life Saver 🚑)

```bash
git reflog
```

**When to use:**

* Lost commits
* Accidental reset

**Analogy:**

> CCTV footage of everything you did in Git.

---

## 🔹 10. Real-World Branch Strategy

| Branch      | Purpose      |
| ----------- | ------------ |
| `main`      | Production   |
| `dev`       | Staging      |
| `feature/*` | New features |
| `hotfix/*`  | Urgent fixes |

---

## 🔹 11. Golden Rules (Production)

* ❌ Never force push on `main`
* ✅ Always pull before push
* ✅ One feature = one branch
* ✅ Small, meaningful commits
* ❌ Never commit `.env` files

---