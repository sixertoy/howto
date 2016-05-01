## Working with GIT History

### Files status

> in short version :
> ```D``` is for deleted
> ```M``` is for modified
> ```??``` is for files that must be added to index

**Show status**

```bash
git status
```

**Show status in short version**

```bash
git status --short
```

###### Alias

```bash
git config --global alias.st = 'status'
```

### Logs

**Shows all logs**

```bash
git log
```

**Shows last {n} commits logs**

```bash
git log -{n}
```

###### Alias

> Show last log

```bash
git config --global alias.llog = 'log -1'
```### Diff for files

```bash
# Full diff on all files
git diff
# current HEAD version with previous commit
git diff <fullPathFilename3>
# between commits, commit #b8094c9 vs commit #bab68bf
git diff b8094c9:<fullPathFilename3> bab68bf:<fullPathFilename3>
```

<br>
## Aliases

```bash
changed = show --name-status
tree = log --oneline --decorate --graph
delete-remote-branch = push origin --delete
rewind = !git reset HEAD -- && git checkout -- .
diff-br = !git diff --stat --color $1..$2
diff-develop = !git diff --stat develop:$1..HEAD:$1
```
