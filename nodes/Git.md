---
context:
  - "[[Version Control]]"
  - "[[Programming Software]]"
  - "[[System Software]]"
---

# Git

[[Free and Open Source]] distributed [[Version Control]] system.

---

**Appication**: As a [[Software Application]], Git itself is a [[CLI Application]], but there are also many [[GUI Application]]s that wrap around it.

## Common Commands

- `git init`: Initialize a new [[Repository]].
- `git clone`: Clone an existing repository.

- `git status`: Show changed/untracked files.
- `git add <file>`: Stage specific file.
- `git add .`: Stage all changes.
- `git commit -m "message"`: Commit staged changes.
- `git push`: Push to remote (origin).
- `git pull`: Fetch + merge from remote.

- `git log`: Show commit history.
- `git log --oneline`: Show compact commit history.
- `git diff`: Show unstaged changes.
- `git diff --staged`: Show staged changes.

- `git stash`: Save changes temporarily.
- `git stash list`: List stashes.
- `git stash pop`: Apply last stash and remove it.
- `git stash apply`: Apply last stash (keep it).
- `git stash drop`: Delete last stash.
