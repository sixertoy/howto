#### Add All files to a ```git commit```

```bash
git add -A .
```

#### Add a single/multiple file(s) to a ```git commit```

```bash
git add <file_to_be_commited>
git add <file_to_be_commited> <file2_to_be_commited> <...>
```

#### Remove all files from a ```git add```

```bash
git reset HEAD --
```

#### Remove a single/multiple file(s) from ```git add```

*Single File*

```bash
git reset HEAD <file_to_remove_from_add>
```

*Multiple Files*

```bash
git reset HEAD <file_to_remove_from_add> <file2_to_remove_from_add> <...>
```

### Cancel last ```git commit```

```bash
git reset HEAD~1
```

### Cancel **{n}** last ```git commit```

```bash
git reset HEAD~{n}
```


git reset HEAD~{n}

# GIT Commands

# Git Commands

## Branches

#### Create

```bash
git checkout -b <branchName>
```

#### Switch

```bash
git checkout <branchName>
```

#### Delete a local branch

```bash
# First switch to a safe branch
git checkout develop
# Then delete the desired branch
git branch -d <branchName>
```

#### Delete a remote branch

```bash
# First switch to a safe branch
git checkout develop
# Then delete the desired branch
git push origin --delete <branchName>
```

## Commits <small>```add```, ```commit``` & ```push```</small>

#### Add files to a commit <small>```add```</small>

###### Single

```bash
git add <fullPathFilename>
```

###### Multiple

> 3 files in this example

```bash
git add <fullPathFilename1> <fullPathFilename3> <fullPathFilename3>
```

###### Alls

```bash
git add -A .
```

#### Commit files to your local repository <small>```commit```</small>

```bash
git commit -m "#JIRA-TASK-NUM commit because we need to fix somethings"
```

#### Push to a remote Git Server <small>```push```</small>

```bash
git push
```

## History <small>```status``` ```log``` & ```Diff```</small>

### Current HEAD version files status

```bash
# long
git status
# short
git status --short
```

> in short version :<br>
> ```D``` is for deleted<br>
> ```M``` is for modified<br>
> ```??``` is for files that must be added to versionning (untracked files)

### Log commits history

```bash
# shows all logs
git log
# shows only the last 25 commits logs
git log -25
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

## Cancel changes <small>```reset``` & ```revert```</small>

### Unstage tracked files

> **After** an ```add``` and **before** a ```commit```

```bash
git reset HEAD --
```

### Local changes (not yet pushed)

```bash
# cancel 1 local previous commit
git reset HEAD~1
# cancel n local previous commit
git reset HEAD~n
```

### Remote changes (pushed)

> **It will delete your changes to files**<br>
> **It will delete both history, local and remote**

```bash
# first cancel locally (delete history)
git reset --hard HEAD^
# then push forced
git push --force
```


-  Update gitignore

```bash
git rm -r --cached .
```

- Create branch from current

```bash
git checkout -b branch_name
git push -u origin branch_name
```

- Revert and delete history

```
git reset --hard HEAD~
git push -f
```

- Init empty branch

> Since git > v1.7.2

```bash
git checkout --orphan NEWBRANCH
git rm -rf .
git add .
git commit -m "Init branch"
git push -f
```
