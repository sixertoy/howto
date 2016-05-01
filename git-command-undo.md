# Undo, Cancel, Abort GIT Commands

- [Untracked or not staged changes](#untracked)
- [Staged changes](#staged)
- [Committed changes](#committed)

<br>
<a name="untracked"></name>
### Work with changes not staged for commit or untracked status

#### Commands

> Delete all user modifications made
> Revert all changes in files/folders to HEAD<br>
> Must be applied on files  before a `git add`<br>
> Will not delete untracked files

**Single/Multiple file(s)**

```bash
git checkout -- <file_to_undo>
git checkout -- <file_to_undo> <file2_to_undo> <...>
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
<a name="staged"></name>
### Work with staged changes to be committed

> Reset files/folders status to *to be committed*
> Will not delete all user modifications made
> Will be applied on changes **after** a `git add`<br>
> Will be applied on changes **before** a `git commit`

#### Commands


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
git config --global alias.unstage 'reset HEAD'
```

<br>
<a name="committed"></name>
### Work with commits

*Undo last commit*

```bash
git reset HEAD~1
```

*Undo {n} last commit*

> {n} represent numbers of commits to be removed from index

```bash
git reset HEAD~{n}
```

###### Alias

```bash
git config --global alias.rewind 'reset HEAD~$1'
git config --global alias.rewind-last 'reset HEAD~1'
```
