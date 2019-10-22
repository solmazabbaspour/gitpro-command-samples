# gitpro-command-samples
### git status
git status -s

### git config
git config --list

### git diff
git diff - modified files but not staged
git diff --staged - staged files going in next commit
git diff --cached - what has been staged so far

### git commit
git commit -a —> skip the git add
git commit --amend

### git rm
git rm —> to untracked a file
git rm -cached [filename] —> remove It from staging and not local 

### git log
git log -p -2
git log --stat
git log —pretty=oneline
git log --pretty=format:"%h - %an -%ar: %s" -5 --graph
git log —since=2.weeks
git log —Sfunction_name
git log —author
git log —grep —match-all

### git tag
git tag -l 'enterprise-2.10.* '
git show “tag”
git tag -a v1.4 -m “message”

### git remote
git remote get-url origin will tell you what it is… just run  git remote remove origin and then git remote add origin https://<token>@github.com/<org>/<repo>
  
### git branch
git branch -v
git branch —merged
git branch —no-merged
git branch -vv —> tracking branches

### git push
git push origin local branch:remotebranch
git push origin --delete branch —> delete remote branch

### git checkout
git checkout -b server fix origin/serverfix —> base of the remote branch
git checkout -b sf origin/serverfix —> local branch sf created from remote branch origin/serverfix

### git fetch
git fetch --all ; git branch -vv

### git rebase
git rebase -—onto master server client
Then you have to :
git checkout master
git merge client —> fast forward master to client branch
