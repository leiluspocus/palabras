---
title: 'Git Workflow Cheatsheet'
date: "2017-06-18T16:55:42+00:00"
description: 'Some commands I use frequently when I use Git. '
template: post
slug: /en/git-workflow-cheatsheet/
category: Cheatsheets
tags:
  - cheat sheet
  - git
  - workflow
---
I follow a pretty regular git workflow on my projects:

* All my features are derived from a master branch
* I merge my feature with master only after a code review (If I work with several people on the project, I ask them. Even If I&rsquo;m alone on the project, I still use Github&rsquo;s Pull Requests to review myself).

## My Git Cheatsheet

### Delete a local / remote branch

```
git branch -D branch_name #locally
git push origin --delete branch_name    #remote
```

### Create a branch from a commit

```git checkout -b branch_name a9c146a09505837ec03b```

### Copy the changes from a certain commit

git cherry-pick can be a life savior if well used (ex: when you merge a feature A, a feature B after and you want to revert feature A).

```git cherry-pick commit_hash```

### Know which files you edited

```git status```

### Add a file

```git add filename```

### Reset your working tree

(careful with this command, you&rsquo;ll loose all your local changes)

```git checkout *```

### Save your local changes without commiting them

Stashs are very convenient specially when you switch a lot between multiples branches (features).

```git stash save my_changes_name```

### View my saved stashs

```git stash list```

### Apply a saved stash

```git stash apply my_changes_name```

## Other Git tips

* Do your best to commit only working stuff. It&rsquo;s easy to handle in case of reverts afterwards.
* Avoid the command git add . Be aware of the changes you&rsquo;re pushing from your working tree.
* <span style="color: #ff0000;"><strong>Never force-quit (CTRL + C) while doing git checkout</strong></span>. I did it once because I was impatient and it was taking couple of seconds. If it takes a long time, it means there are a lot of files being fetches. If you do so, your working tree will be a mess.
