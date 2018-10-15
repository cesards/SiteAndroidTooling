---
id: Git
layout: page
title: Git
sidebar: true
---

# Tricks

## Table of contents

- Magic
- Branches
  - Clean remote branches
- .gitignore
  - Applying .gitignore to committed files
- Sub-modules

---

## Magic

- [**`$ git grep <pattern>`**]((https://git-scm.com/docs/git-grep)) greps through all the files in the repo.
- `$ git grep <pattern> $(git rev-list --all)` greps through all the files in the repo’s entire history. (https://git-scm.com/docs/git-grep )

---

## Branches

### Clean remote branches

After fetching, remove any remote-tracking branches which no longer exist on the remote by using:

```sh
git fetch --prune
```

---

## .gitignore

### Applying .gitignore to committed files

Be sure that your actual repo is the lastest version. and then edit `.gitignore` as you wish. After that, use:

```sh
git rm -r --cached .
git add .
```

and then commit the changes:

```sh
git commit -m ".gitignore is now working"
```

If we want the new changes to go with the previous commit, we just need to do:

```sh
git commit --amend
```

---

## Sub-modules

**Topic related sources:**

- [**Using Git Submodules Effectively**](https://www.philosophicalhacker.com/post/using-git-submodules-effectively/)