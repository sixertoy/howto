# GIT Commands

## Recording Changes to the Repository

<br>
### Add files to index with `git add`

> Can be applied to untracked/not staged files/folders<br>
> Add files to `.gitignore` file to avoid GIT to track changes on those files

#### #Commands

**Single/multiple file(s)**

```bash
git add <file_to_be_commited>
git add <file_to_be_commited> <file2_to_be_commited> <...>
```

**All files**

```bash
git add -A .
```

###### Alias

```bash
git config --global alias.add-all 'add -A .'
```

<br>
### Commit changes with `git commit`

#### Commands

> Will only applied on staged files after a `git add`

```bash
git commit -m "a human readable and explicit commit message"
```

###### Alias

```bash
git config --global alias.ci 'commit'
```

#### Add files to current `git commit` before `git push`

> Add forgotten files and use `--amend` flag

```bash
git commit -m "files is missing to this commit"
git add <forgotten_file1> <forgotten_file2> <...>
git commit --amend
```

###### Alias

```bash
git config --global alias.amend '!git add {} && git commit --amend'
```

#### Undo last commit

> Mark all changes as new<br>
> Removing previous changes from the index

*Undo last commit*

```bash
git reset HEAD~1
```

*Undo {n} last commit*

> {n} represent number of commits to be removed from index

```bash
git reset HEAD~{n}
```

**Example below will reset current state index to b2d449f, all previous changes from 72143fd and b537da4 will be marked as new**

```bash
git log -3
2016-02-01 <user> 72143fd
        update 3
2016-02-01 <user> b537da4
        udpate 2
2016-02-01 <user> b2d449f
        update 1
git reset HEAD~2
```

###### Alias

```bash
git config --global alias.rewind 'reset HEAD~$1'
git config --global alias.rewind-last 'reset HEAD~1'
```

#### Undo to a particular commit hash with flags

> --hard **>** --mixed **>** --soft

*--soft*

> Mask last changes as new<br>
> Keep previous changes from the index

```bash
git reset --soft <commit_hash>
```

*--mixed*

> Mask all changes as new<br>
> Removing previous changes from the index

```bash
git reset --mixed <commit_hash>
```


*--hard*

> Removes all changes
> Flag `--hard` will act like a `git reset HEAD` plus a `git checkout --`

```bash
git reset --hard <commit_hash>
```

###### Alias

```bash
git config --global alias.cancel 'reset --mixed $1'
git config --global alias.discard 'reset --hard $1'
```

<br>
### Push local index changes to remote repository

```bash
git push
```

#### Undo push to remote repository

> **Index history will be lost**
> Be sure that another user has not yet pulled or merged previous changes<br>
> You can also use `--soft` or `--mixed` flags instead of `--hard`

```bash
git reset --hard <commit_hash>
git push --force
```
