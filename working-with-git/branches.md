# Working with GIT Branches

## Prefix & Namings

Name of a branch is a JIRA's ticket
Folders:
- imp
- new
- hotfix

## Commands

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
