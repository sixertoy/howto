# Aliases

## Config

```bash
git config alias.<name> <value>
```

```bash
plr = pull --rebase
mg = merge --no-ff
br = branch
ci-v = commit --no-verify
ci = commit
push-v = push --no-verify
st = status
rb = rebase
rbi = rebase -i
co = checkout
llog = log -1
cr = cherry-pick
amend = commit --amend
tree = log --oneline --decorate --graph
amend-add = commit --amend --no-edit
ca = !git add -A . && git commit
ca-v = !git add -A . && git commit --no-verify
```

### Advanced

```bash
unstage = reset HEAD --
```

## Mixins

**Show current branch name**
alias git-bname="git rev-parse --abbrev-ref HEAD"

**Show all remote branches**
alias git-br-origin="git br -a"

**Show current repo user name**
alias git-user="git config --get user.name"

**Show tracked branches, pullable & pushable branches**
alias git-repo-infos="git remote show origin"

**Show remote URL of a repository**
alias git-url="git config --get remote.origin.url"

**Delete remote branch**
alias git-delete-remote-branch="git branch --delete origin <branch>"

## Functions

**Show current branch description**
function git-desc {
  branch=$(git-bname)
    if [ -z "$1" ]; then
      git-br
    else
      git config branch.$branch.description $1
  fi
}

**Show local branches, with description**
function git-br {
  branches=$(git for-each-ref --format='%(refname)' refs/heads/ | sed 's|refs/heads/||')
  for branch in $branches; do
    desc=$(git config branch.$branch.description)
    if [ $branch == $(git-bname) ]; then
      branch="*  \033[0;32m$branch\033[0m"
     else
      branch="   $branch"
     fi
     echo -e "$branch \033[0;36m$desc\033[0m"
  done
}

function git-log-branch {
  git log develop..
}
