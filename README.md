### git status
git status -s

### git config
git config --list

### git diff
git diff --> This shows modified files but not staged
git diff --staged --> This shows staged files going in next commit
git diff --cached --> Same as --staged 

### git commit
git commit -a —-> This skips the git add command
git commit --amend

### git rm
git rm —> used to untrack a file
git rm -cached [filename] —> remove file from staging and not local 

### git log
git log -p -2
git log --stat
git log —pretty=oneline
git log --pretty=format:"%h - %an -%ar: %s" -5 --graph
git log -—since=2.weeks
git log —Sfunction_name
git log —-author
git log —-grep —-match-all

### git tag
git tag -l 'enterprise-2.10.* '
git show “tag”
git tag -a enterprise-2.10.1 -m “message”

### git remote
git remote get-url origin 
  
### git branch
git branch -v
git branch —-merged
git branch —-no-merged
git branch -vv —-> Tracks the tracking branches

### git push
git push origin local branch:remotebranch
git push origin --delete branch —-> This deletes the remote branch

### git checkout
git checkout -b serverfix origin/serverfix —> This bases the serverfix branch out of the remote branch
git checkout -b sf origin/serverfix —> This creates a local branch named sf from remote branch origin/serverfix

### git fetch
git fetch --all ; git branch -vv

### git rebase
git rebase -—onto master server client
Then you have to:
git checkout master
git merge client —> This fast forwards master to client branch
