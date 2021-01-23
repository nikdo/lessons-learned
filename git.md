# Git

[Checkout remote branch](https://stackoverflow.com/a/1783426/5763764) with autocomplete:

```
git checkout -t origin/autocompleted-branch-name
```

[Rewrite all commits from the beginning:](https://stackoverflow.com/a/41769800/5763764)

```
git rebase -i --root
```

[Log in reverse order:](https://stackoverflow.com/a/2798833/5763764)
```
git log --reverse --oneline
```

List log messages in reverse until specific commit:
```
git log master.. --reverse --format="* %s"
```

[List all authors:](https://stackoverflow.com/a/9597462/5763764)

```
git shortlog -sne        # current branch
git shortlog -sne --all  # all branches
```

[Fix wrong author in multiple commits:](https://stackoverflow.com/a/1320317/5763764)

```
git rebase -i <commit-with-first-mistake>^
# mark commits to reword
git show HEAD  # to verify current commit author
git commit --amend --no-edit --author "Name <email>" && \
git rebase --continue
```