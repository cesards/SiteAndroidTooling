# Tricks

## Table of contents

- Applying .gitignore to committed files



## Applying .gitignore to committed files

Be sure that your actual repo is the lastest version

Edit .gitignore as you wish
git rm -r --cached .
git add .

Commit it:
git commit -m ".gitignore is now working"





Not pushed yet, but want new changes to go with previous added commit
git add .
git commit --amend



- `git grep <pattern>` greps through all the files in the repo. (https://git-scm.com/docs/git-grep)
- `git grep <pattern> $(git rev-list --all)` greps through all the files in the repo’s entire history. (https://git-scm.com/docs/git-grep )

