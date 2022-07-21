# pre-commit

## Run pre-commit only git managed files with file extention filter

```bash
git ls-files '*.py' | xargs pre-commit run --files
```

## Apply a specific hook to them
```bash
git ls-files '*.py' | xargs pre-commit run autopep8 --files
```

## Run multiple hooks selectively
https://github.com/pre-commit/pre-commit/issues/1296
