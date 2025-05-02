## Setup:

# Git

```
#Bash
git config --global init.defaultBranch main && \
git config --global user.name "$(read -p 'Enter Git name: ' && echo "$REPLY")" && \
git config --global user.email "$(read -p 'Enter Git email: ' && echo "$REPLY")" && \
git config --global --list

#Fish
git config --global init.defaultBranch main && \
git config --global user.name (read -P 'Enter Git name: ') && \
git config --global user.email (read -P 'Enter Git email: ') && \
git config --global --list
```

# GitHub
```
gh auth login && \
gh auth status && \
gh repo list
```

## Initializing Git
```
git init --initial-branch=main
```

## Github repo create with local repo name
```
gh repo create $(basename $(pwd)) --public --source=. --remote=origin --description "$(editor $(mktemp))" #Bash (OR)

gh repo create (basename (pwd)) --public --source=. --remote=origin --description "(editor (mktemp))"     #Fish
```

## Repo rename sync 

# (local -> remote)
```
gh repo rename "$(basename "$(pwd)")" #Bash (OR)

gh repo rename (basename (pwd)) #Fish
```

# (remote -> local)
```
#Bash
oldfolder=$(basename "$(pwd)") && \
newfolder=$(gh repo view --json name -q .name) && \
cd .. && \
mv "$oldfolder" "$newfolder" && \
cd "$newfolder" && \
pwd && \
unset oldfolder newfolder

#Fish
set oldfolder (basename (pwd)) && \
set newfolder (gh repo view --json name -q .name) && \
cd .. && \
mv $oldfolder $newfolder && \
cd $newfolder && \
pwd && \
set -e oldfolder newfolder

```
## Stage, Commit, Push
```
git add $(git rev-parse --show-toplevel)/* && git commit && git-town sync #Bash
git add (git rev-parse --show-toplevel)/* && git commit && git-town sync  #Fish
```

## Create a new feature branch off the main branch
git-town hack <feature-branch-name>

## Create a proposal to merge a feature branch
```
git-town propose <feature-branch-name>
``` 
#This get's you directly to create pr page after stashing away the work of another feature u were working on using safe practices

## Display the local branches visually and allows switching between them
```
git-town switch
```

## For more features check: 
```
git-town --help
```
