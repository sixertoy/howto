# GIT Commands

## References

- [Git Basics - Undoing Things](https://git-scm.com/book/be/v2/Git-Basics-Undoing-Things)
- [Fixing Mistakes](https://www.kernel.org/pub/software/scm/git/docs/user-manual.html#fixing-mistakes)

<br>
## Recording Changes to the Repository

### Undo changes to not indexed files

> Revert changes to files/folders to HEAD current branch status

#### Commands

> Will **only applied to not staged** files, before a `git add`<br>
> Will not be applied after a `git add`<br>
> Will not be applied after a `git commit`<br>
> Will not be applied after a `git push`<br>
> Will not delete untracked files

**Single/Multiple file(s)**

```bash
git checkout -- <file_to_revert>
git checkout -- <file_to_revert> <file2_to_revert> <...>
```

**All files**

```bash
git checkout -- .
```

###### Alias

```bash
git config --global alias.undo 'checkout --'
```

<br>
### Add changes to index with `git add`

> Can be applied to untracked/not staged files/folders
> Add files to `.gitignore` file to avoid GIT to track changes on these files

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

##### Undo

> Will reset files status to untracked/not staged

**Single/multiple file(s)**

```bash
git reset HEAD <file_to_unstage>
git add <file_to_unstage> <file2_to_unstage> <...>
```

**All files**

```bash
git reset HEAD --
```

###### Alias

```bash
git config --global alias.unstage 'reset HEAD --'
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

> Add forgottent files and use `--amend` flag

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

> Mark all changes as new
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

> Mask last changes as new
> Keep previous changes from the index

```bash
git reset --soft <commit_hash>
```

*--mixed*

> Mask all changes as new
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
> Be sure that another user has not yet pulled or merged previous changes
> You can also use `--soft` or `--mixed` flags instead of `--hard`

```bash
git reset --hard <commit_hash>
git push --force
```

<br>
## Working with GIT Branches

*Create a new branch*

```bash
git checkout -b <branchName>
```

*Switch to another branch*

```bash
git checkout <branchName>
```

*Delete a local branch*

```bash
# First switch to a safe branch
git checkout develop
# Then delete the desired branch
git branch -d <branchName>
```

*Delete a remote branch*

```bash
# First switch to a safe branch
git checkout develop
# Then delete the desired branch
git push origin --delete <branchName>
```

*Add a short description to a branch*

```bash
git config branch.<branch_name>.description "<a_short_description>"
```

*show a branch description*

```bash
git config branch.<branch_name>.description
```

## Working with GIT History

### Current index files status

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

### Commits logs

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
```

### Diff for files

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

<br>
## Miscellaneous

### Update gitignore cache

```bash
git rm -r --cached .
```

### Log history as tree view

```bash
git log --oneline --decorate --graph
```
