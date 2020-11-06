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
$ git push -m origin master
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
