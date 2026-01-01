# diff

- `git diff` shows what changed in your code
- It compares two states of the same file and shows line-by-line differences.

## git diff

- It compares Working Directory vs Staging Area
- Shows the changes you made in working directory and staging area.
- `-` means old staged content and removed.
- `+` means new content which is in working directory wrt git diff
- Focus will be on both staged and unstaged changes.

## git diff --staged

- It compares the changes in the Staging Area against the last commit (HEAD), rather than comparing the Working Directory against the Staging Area.
- Focus will be on staged changes.
- `-` (Red): Represents the Last Commit (HEAD). These are the lines that existed in your project before you started your current round of work.
- `+` (Green): Represents the Staging Area. These are the changes you have already run git add on and are currently "locked in" for the next commit.

# stash

- It is an internal stack(space) where you can temporarily save your uncommitted changes.
- It allows you to switch branch, pull updates, and do other work without committing earlier work.
- You can stash multiple times and each stash will create new package and pushed on top of the stack.

## What does `git stash` save?

`git stash` packages staged files + staged-but-modified (tracked) files into a single stash entry.

## Common commands

### Save the changes

`git stash` or `git stash push -m "WIP: navbar styling"`

### Include untracked/new files

`git stash -u`

### Include everything (even ignored files!)

`git stash -a`

### Create a branch FROM a stash

`git stash branch new-feature stash@{1}`

### View stashed changes

`git stash list`

```
stash@{0}: WIP: navbar styling
stash@{1}: WIP: login form
```

### Bring back last stash AND remove from stash

`git stash pop`

### Bring back last stash and KEEP in stash

`git stash apply`

### Delete a stash

`git stash drop stash@{}`

### Delete ALL stashes

`git stash clear`

> - Stashes are local only (not pushed to GitHub)
> - Stash can cause merge conflicts when applied (normal Git behavior)
