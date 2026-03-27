### Restore file from another branch

`git restore --source=NABOLT-470--decrease-payload-response src/utils/helpers.js`

### Review changes from a given dev
`git log --author="Paliienko" --patch --stat --since="2 months ago" --all`

### Replace remote

```
git remote -v
git remote set-url origin git@bitbucket.org:ulta-beauty/iphone.git
```

### Ignore local files
Add files to `.git/info/exclude` same as added to .gitignore