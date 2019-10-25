# Git

[Rewrite all commits from the beginning:](https://stackoverflow.com/a/41769800/5763764)

```
git rebase -i --root
```

[Fix wrong author in multiple commits:](https://stackoverflow.com/a/1320317/5763764)

```
git rebase -i <commit-before-first-mistake>
git commit --amend --author "Name <email>" --no-edit && \
git rebase --continue
```