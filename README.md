# Git Homework Assessment — Step-by-Step Commands

This README explains all steps and Git commands used to complete the homework assessment: initializing a repo, making commits, cleaning history, recovering lost work, creating branches, defining aliases, tagging, and pushing to a remote repository.

---

## 1) Initialize repo, create file, and push first commit via SSH

```bash
# initialize repository and rename master branch
git init
git branch -M main

# generate SSH key for GitHub
ssh-keygen -t ed25519 -C "agron.ahmeti@xponenlt.ai" -f ~/.ssh/id_ed25519_xpo

# add SSH key to ssh-agent (update ~/.ssh/config as needed)
# add public key to GitHub account

# configure user identity for repo
git config user.name "Agron Ahmeti"
git config user.email "agron.ahmeti@xponenlt.ai"

# connect to remote repository via SSH
git remote add origin git@github-xpo:agron-xpo/git-xpo-assessment.git

# create project.txt and open it
touch project.txt
start project.txt

# Added first line and then first commit
git add project.txt
git commit -m "first commit"

# push branch remote with upstream
git push -u origin main
```

---

## 2) Add unclear commits

```bash
# second line: "Here is the 2nd line"
git commit -am "update"
# second line: "Here is the second line"
git commit -am "stuff"

# third line: "Here is third line"
git commit -am "final"
```

---

## 3) Clean up history with interactive rebase

```bash
# interactive rebase last 3 commits
git rebase -i HEAD~3

# squash "stuff" into "update" and rename commit message to "add second line"
# rename "final" commit message to "add third line"
```

---

## 4) Simulate mistake and remove commit

```bash
# fourth line: "Here is fourth line"
git commit -am "add fourth line"

# remove the commit
git reset --hard HEAD~1
```

---

## 5) Recover lost commit

```bash
# check HEAD movements
git reflog HEAD

# recover the lost commit (example using reflog entry)
git reset --hard HEAD@{1}
```

---

## 6) Create a branch from the recovered commit

```bash
# replace <commit-hash> with actual hash from reflog
git branch recover-commit 1e960dd
```

---

## 7) Define a git alias for visual commit history

```bash
git config alias.lg "log --oneline --graph --decorate --all"
```

Now `git lg` shows the full commit graph.

---

## 8) Tag the cleaned version

```bash
# add tag
git tag -a v1.0 -m "Version 1.0 — cleaned history"

# check tags
git tag

git lg
```

---

## 9) Push both branches to remote repo

```bash
# push main branch
git push -u origin main

# push recovered branch
git push -u origin recover-commit
```

---

## 10) Add a README for documentation

```bash
# create README file
touch README.md
# update(explain) README file
git add README.md
git commit -m "add README documenting homework steps"

git push origin main
```

---

