# Git snippets
## Get date and time of commits

```bash
# get commits date and time
git log --date-order --author=<author> --since=2020/1/1 --pretty=format:%cd
```

```bash
# comma separated format
git log --date-order --author=Taka --since=2020/1/1 --pretty=format:%cd --date=format:'%Y/%m/%d, %H:%M, %z '
```

## Replacement
`git grep` then replace words with `sed`.

http://vdeep.net/git-grep-sed-replace

```bash
git grep -l 'Foo' | xargs sed -i '' -e 's/Foo/Bar/g'
```

## Branches
Work in multiple branches simultaneously.
```bash
$ git checkout dev_branch1
# ... work on dev_branch1 ...
# ... e.g. running heavy process

$ git worktree add dev_branch2
# branch2 is checked out under dev_branch2 directory
# ... work on dev_branch2 ...

# after work under dev_branch2 is finished, remove the worktree with
$ git worktree remove dev_branch2
```

## Blaming
Find the author who invented the ugly variable.
https://stackoverflow.com/a/5816177/

```bash
git log -S insanely_long_weird_inappropriate_variable_name --source --all
```
