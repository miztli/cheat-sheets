### Restore file from another branch

`git restore --source=NABOLT-470--decrease-payload-response src/utils/helpers.js`

### Review changes from a given dev
`git log --author="Paliienko" --patch --stat --since="2 months ago" --all`

### Replace remote
```
git remote -v
git remote set-url origin git@bitbucket.org:ulta-beauty/iphone.git
```

### Undo reset

`git reset --hard ORIG_HEAD`

### Ignore local files
Add files to `.git/info/exclude` same as added to .gitignore

### Stash only non-staged files
1. Stage all files you need to remain in the working dir
2. Stash the rest `git stash --keep-index`
3. Name the stash if needed: `git stash -m "stash name"`