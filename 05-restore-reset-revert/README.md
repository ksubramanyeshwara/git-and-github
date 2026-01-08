# Restore vs Reset vs Revert

## Restore

Restore the files previous state without altering commit history.

- `git restore <filename>`: Discard unstaged changes in the working directory.
- `git restore --staged <file>`: Unstages a file but keeps your changes in the working directory.

## Reset

- It moves the HEAD pointer and the current branch to a specific state.
- It has three modes
  1. `--soft`
  2. `--mixed`
  3. `--hard`

### `git reset --soft`

- Moves HEAD only
- Keeps staging area
- Keeps working directory

**Use when**

- You want to edit commit message.
- You want to combine commits.

`git reset --soft HEAD~1`: It moves HEAD back by 1 commit.

### `git reset --mixed` (default)

- Moves HEAD
- Clears staging area
- Keeps working directory

**Use when**

- You added wrong files using git add
- You want to re-stage properly

`git reset --mixed HEAD~1`: It moves HEAD back by 1 commit and files are unstaged.

### `git reset --hard`

- Moves HEAD
- Clears staging area
- Deletes working directory changes

**Use when**

- You want to discard everything
- You messed up locally and want a clean state

`git reset --hard HEAD~1`: t moves HEAD back by 1 commit and files are unstaged and files are deleted forever(unless reflog)

> Rewrites local history. Never use this on commits that have already been pushed to a shared repository.

## Revert

- It is the safest way to undo changes in shared environment.
- Creates a brand new commit that does the exact opposite of a previous commit.

**When to use**

- Commit already pushed
- Team/shared branches
- Production fixes

`git revert <commit-hash>`

> It does not delete old commits; it only adds a new "undoing" commit on top, keeping the project history intact.

## Golden rules

- Unstage / discard files: git restore
- Fix local commits (not pushed): git reset
- Undo pushed commits: git revert

## Amend

- Change the last commit message
- Add missed files to the last commit
- Remove files from the last commit
- Fix small mistakes without creating a new commit

`git commit --amend`

### When you amend:

- Git creates a new commit
- Old commit is replaced
- Commit hash changes

```
Before: A → B
After:  A → B'
```
> ❌ Do NOT amend a pushed commit (unless you know what you’re doing). If you want to then you need to force push it

### When SHOULD you use git amend?

- Fix typo in commit message
- Add missed files
- Clean commit before pushing