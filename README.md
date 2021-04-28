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
1. "undo" the commits till commit_id (the last commit you want to keep) -> all the changes after will go into staging area as if just did git add
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

Push a local branch to remote (create new remote branch with the specified name)
```
git push origin local_branch_name:remote_branch_name
```


## CD (Continuos Deployment)

Software features are delivered frequently through **automated** deployments - no manual review and deployment, reduced overhead.

**How to build a CD pipeline?**

1. Tests: Stop bugs from entering production stages
* Unit tests
* Integration tests
* Web UI tests
* Headless browser testing (headless: no GUI)
* End-to-end test: set up requests/data generator(s)
* Backward compatibility tests - e.g. via PostProd stage
* Gamma testing
  * Chaos testing (failure injection framework e.g. Apache Ozone)
  * Dependency connection test

2. Limit blast radius
* Fail fast v.s. fail slow
* Real time Monitors/Alarms (consider using % threshold)
* Auto-cut
* Deployment blockers: e.g. Time window blocker - avoid deploy in low traffic time to fail fast
* Port scan
* Deployment configuration

3. Mindset: CD needs continuous improvement and maintenance! Effort spent on avoid creating bugs -> create better ways to catch bugs
* Write GOOD and MORE tests - higher coverage
* Fine tune alarms
* Deploy more often
* Assume rollbacks will happen

**Commom pitfalls**
* Alarm missing data - configure your alarms such that missing data is treated as alarm state
* Queue based incomming traffic - load balancer usually has health check on hosts but for those services that takes only requests from queues, have mechanisms detect host health


## AWS
**IAM Roles vs. Users**
These are two fundamental types of "principals" (a.k.a. identities) that customers can use. The primary difference is that the credentials for Users are supposed to be long lived - do not expired automatically, and must be manually rotated (either by a human or another system) every 90 days for example. However, the credentials for Roles expire at a specific point in time.
