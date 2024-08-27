---
title: Git
type: docs
prev: docs/Fun
next: docs/JavaScript
---
### Update your branch with `main`
#### Option 1
```
git checkout my_branch
git fetch origin main
git merge origin/main
```
Resolve conflicts, if any, then stage, commit, and push changes
#### Option 2
```
git checkout my_branch
git fetch origin
git rebase origin/main
#Possible merge conflicts here ...
# git rebase --continue
git push origin my_branch --force
```

### Bring a file in from another branch to your current one
`git checkout source_branch -- path/to/file`

git cherry-pick <commit_hash>

Resolve conflicts, if any, then stage, commit, and push changes

### Stash it
1. Stash changes if you are having issues: `git stash`
2. Check which stash you want to apply using: `git stash list`
3. Remove from stash and apply: `git stash pop stash@{n}`
4. Keep in stash and apply: `git stash apply stash@{n}`

### Unwanted, untracked files
Preview: `git clean -n`
Clean: `git clean -f -d`

### Git not letting you checkout?
`git checkout -f[--force] my_branch`

`git switch -f[--force] my_branch`
