---
categories: tool
tags:
  - git
toc: true
---

# 1. git basic

# 2. git command

## status

```bash
$ git status
```

## push

```bash
$ git add .
$ git commit -m "commit test"
$ git push -u origin master // push to master branch
```

## create / delete branch

```bash
# branch status
$ git branch
# create branch
$ git branch <branch name>
# switch branch
$ git checkout <branch name>
# create & switch branch
$ git checkout -b <branch name>
# delete branch
- local
$ git branch -d <branch name>
- remote repo
$ git push origin --delete <branch name>
```

# 3. git tips

## save git id/pw

```bash
$ git config credential.helper store --global
```

## if gitignore is not work?

```bash
$ git rm -r --cached .
```
