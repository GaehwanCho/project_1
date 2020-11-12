---
categories: tool
tags:
  - git
toc: true
sidebar_main: true
---

# 1. git basic

# 2. git command

## status

```bash
$ git status
```

## pull

- git fetch & git pull  
  `git fetch` is different from `git pull`.  
  `git fetch` receive the latest code of remote repo origin/master.  
  `git pull` performs both function of `git fetch` and `git merge`.
  If you would like to check difference from local to remote, type `git diff HEAD origin/master`.  
  If you want to check commit log, type `git log --decorate --all --oneline`.

```bash
# receive latest code & merge
$ git pull

# receive latest code
$ git fetch
# merge local & remote
$ git merge origin/master
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
