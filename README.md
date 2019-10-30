### git status
- git status -s

### git config
```
git config --list
git confit --global rerere.enabled true --> whenever you fix a merge conflict it will be cached and used for next time
```

### git diff
```
git diff --> This shows modified files but not staged
git diff --staged --> This shows staged files going in next commit
git diff --cached --> Same as --staged
git diff --check --> identifies whitespace errors
git diff master...branch --> Get the first ancestor and then compare the branches to one another == git merge-base branch master
```
### git commit
```
git commit -a —-> This skips the git add command
git commit --amend
```
### git add
```
git add --patch —>
```

### git rm
```
git rm —> used to untrack a file
git rm -cached [filename] —> remove file from staging and not local
```

### git rm
```
git --cherry-pick SHA --> This will only pick that commit and merge it in your branch with a new SHA-1
```

### git log
```
git log -p -2
git log --stat
git log —pretty=oneline
git log --pretty=format:"%h - %an -%ar: %s" -5 --graph
git log -—since=2.weeks
git log —Sfunction_name
git log —-author
git log —-grep —-match-all
got log --no-merges branch1..origin/master
git log branch --not master --> get all the changes on the branch that are not in master
```

### git tag
```
git tag -l 'enterprise-2.10.* '
git show “tag”
git tag -a enterprise-2.10.1 -m “message”
git tag -s v1.5 -m 'message' --> sign your tags
```

### git remote
```
git remote get-url origin 
git remote add local_proj /opt/git/project.git
```

### git request-pull
```
git request-pull origin/master remoteurl --> Get all the changes from remoteurl and pull to master
```

### git branch
```
git branch -v
git branch —-merged
git branch —-no-merged
git branch -vv —-> Tracks the tracking branches
```

### git push
```
git push origin local branch:remotebranch
git push origin --delete branch —-> This deletes the remote branch
```

### git checkout
```
git checkout -b serverfix origin/serverfix —> This bases the serverfix branch out of the remote branch
git checkout -b sf origin/serverfix —> This creates a local branch named sf from remote branch origin/serverfix
```

### git fetch
```
git fetch --all ; git branch -vv
```

### git rebase
```
git rebase -—onto master server client
Then you have to:
git checkout master
git merge client —> This fast forwards master to client branch
```

### git merge
```
git merge --no-commit --squash branchname --> gets all the work on the merge branch and squashes into on non-merge commit, --no-commit --> dont automatically record a commit
```

### git format-patch
```
git format-patch --> generate the mbox-formatted files
git format-patch -M --> Look for renames
```

### git send-email
```
git send-email *.patch --> Sends the patch as email (Set email in ~/.gitconfig)
```

### git apply
```
git apply patchname.patch --> use this if the patch format is created with diff
git apply patchname.patch --check --> check if the patch will be applied cleanly
```

### git am
```
git am patchname.patch --> use this when the format-patch command has been used to create the patch
```
### git describe
```
git describe  master
```

### git shortog
```
git shortlog --no-merged master --not v1.0.1
```

### git archive
```
git archive master --prefix='project/' | gzip > `git describe master .tar.gz`
```

### Sign tag and view
```
gpg --list-keys
gpg -a export {pub from prev output} | git hash-object -w --stdin
git tag -a maintainer-gpg-pub {SHA-1 from prev}
git show maintainer-gpg-pub | gpg --import
```

### Create git server

1. `git clone --bare my_project my_project.git`
2. Copy project to git server `scp -r my_project.git user@git.example.com:/srv/git`
3. Give project shared access `git init --bare --shared`
4. Test and clone to client: `git clone user@git.example.com:/srv/git/my_project.git`

### Extra git commands
GIT_TRACE=1  GIT_TRACE_PACKET=1
