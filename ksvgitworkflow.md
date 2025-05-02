
## Initializing Git
```git init --initial-branch=main```

## Github repo create with local repo name
```
gh repo create "${PWD##*/}" --public --source=. --remote=origin     #Bash (OR)
gh repo create (basename (pwd)) --public --source=. --remote=origin #Fish
```
## Repo rename sync 
# (local -> remote)
```
gh repo rename "${PWD##*/}"     #Bash (OR)
gh repo rename (basename (pwd)) #Fish```
# (remote -> local)
```
mv "$(pwd)" "../$(gh repo view --json name -q .name)" && cd "../$(gh repo view --json name -q .name)" && pwd #Bash (OR)
mv (pwd) ../(gh repo view --json name -q .name) && cd ../(gh repo view --json name -q .name) && pwd          #Fish
```
## Stage, Commit, Push
```
git add $(git rev-parse --show-toplevel)/* && git commit && git-town sync #Bash
git add (git rev-parse --show-toplevel)/* && git commit && git-town sync  #Fish
```
## Create a new feature branch off the main branch
git-town hack <feature-branch-name>
## Create a proposal to merge a feature branch
```git-town propose <feature-branch-name>``` 
#This get's you directly to create pr page after stashing away the work of another feature u were working on using safe practices

## Display the local branches visually and allows switching between them
```git-town switch```

For more features check: ```git-town --help```