# SoftwareDevelopment

## Git


Set alias for pretty print git log
```
git config --global alias.adog "log --all --decorate --oneline --graph" 
```

Pretty print git log
```
git adog
```

Squash several sequencial commits into one to keep clean history
1. "undo" the commits till commit_id (the last commit you want to keep) -> all the changes after will gointo staging area as if just did git add
```
git reset --soft [commit_id] 
```
2. commit as one
```
git commit -m [commit_name]
```

Switch branch (try not to use checkout)
```
git switch [branch_name]
```

rebase a feature branch to top of the mainline
```
git switch feature_branch
git rebase master
```

Combines the spefified branch's history into the current branch (try to use only in fast forward mode)
```
git merge [from_branch_name] 
```

Pull and rebase local master in one line (Used When you work on local mainline but the remote master has new commits)
```
git pull --rebase origin master
```

Delete local branch
```
git branch -d <local-branch>
```
  
Delete a local branch set to track a remote branch
(-r, --remotes tells git to delete the remote-tracking branch). This will not delete the branch on the remote!
```
git branch -d -r origin/<remote branch name>
```
