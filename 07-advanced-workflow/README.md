# Advanced Workflow

## git checherry-pick

- It lets you copy specific commits from one branch to another.
- Git creates a new commit on your current branch with the same changes as original commit, but with the different commit hash.

```
main:      A---B---C
                \
feature:         D---E---F
```

- You're on main and realize that commit E from the feature branch contains a critical bug fix that you need right now, but you don't want commits D and F yet.

Steps:

- First, find the commit hash of E:
  `git log feature` Let's say E's hash is `abc1234`
- Switch to the main branch:
  `git checkout main`
- Cherry-pick commit E:
  `git cherry-pick abc1234`

```
main: A---B---C---E'
\
feature: D---E---F
```

### If conflict arrises

```
# fix files
git add .
git cherry-pick --continue
```

or

```
git cherry-pick --abort
```

### When to Use It

- Hotfixes: Apply a fix from main to older release branches
- Selective backports: Bring specific features/bugfixes to another branch
- Avoiding full merges when only a few commits are needed

### When NOT to Cherry-Pick

- Moving large feature branches
- Replacing proper merges
- When history context matters

### Dissadvantages

- Cherry-picking creates duplicate commits.
