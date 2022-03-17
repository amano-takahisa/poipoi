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
