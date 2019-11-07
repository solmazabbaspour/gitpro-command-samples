## Progit command samples
Here is a cheatsheet of the commands mentioned in the [progit book](https://git-scm.com/book/en/v2).
### git status
- git status -s

### git config
```
git config --list
git config --global rerere.enabled true --> whenever you fix a merge conflict it will be cached and used for next time
git config --global core.autocorrect 1  --> autocorrects git commands and runs them after 0.1 seconds
git config --local fetch +refs/pull/*/head:refs/remotes/origin/pr/* --> Adds prs to your branch list
```

### git diff
```
git diff                      --> Modified files but not staged
git diff --staged             --> Staged files going in next commit
git diff --cached             --> Same as --staged
git diff --check              --> Identifies whitespace errors
git diff  --ours--/theirs     --> Shows merge conflicts
git diff master..branch       --> All commits that are in branch but not in master
git diff master...branch      --> Get the first ancestor and then compare the branches to one another == git merge-base branch master
```
### git commit
```
git commit -am                —-> Skips the git add command
git commit --amend --no-edit  --> Redo commit and dont change commit message
git commit -s                 --> Sign your commit
```
### git add
```
git add --patch     -—> Add hunks
git add -i          --> Interactive mode
```

### git clean
```
git clean -f -d --> Clean untracked files also in subdirectories
git clean -n -d --> Dry run the clean command
```

### git grep
```
git grep -n search-term
git grep --count
```

### git stash
```
git stash
git stash --keep-index            --> do not stash, staged files
git stash -u                      --> also stash the untracked files
git stash --patch                 --> you will be asked which hunks you want to stash
git stash show -p | git apply -R  --> unapplying a stash
git stash branch nameofbranch     --> First creates a branch and then runs the stash
git stash list
git stash apply
git stash apply stash@{1}
git stash apply --index           --> Will apply the staged changes as well
git stash drop
```
### git rm
```
git rm                      -—> used to untrack a file
git rm --cached [filename]  -—> remove file from staging and not local
```

### git cherry-pick
```
git --cherry-pick SHA       --> This will only pick that commit and merge it in your branch with a new SHA-1
```

### git log
```
git log -p -2
git log --stat
git log —-pretty=oneline
git log --pretty=format:"%h - %an -%ar: %s" -5 --graph
git log -—since=2.weeks
git log -L
git log —-author
git log —-grep —-match-all
got log --no-merges branch1..origin/master
git log —-abbrev-commit --pretty=oneline
git log branch --not master   --> Get all the changes on the branch that are not in master
git log —Sfunction_name       --> When this function was introduced
git log -g master             --> see history like reflog
git log  master..branch       --> All commits that are in branch but not in master
got log --merge               --> files involved in a merge conflict
git log --left-right master...branch --> All unreferenced commits on either branch

```
### git tag
```
git tag -l 'enterprise-2.10.* '
git show “tag”
git tag -a enterprise-2.10.1 -m “message”
git tag -s v1.5 -m 'message'                --> sign your tags
```
### git show
```
 git show master@{yesterday}
 git show HEAD@{5}
```

### git remote
```
git remote get-url origin 
git remote add local_proj /opt/git/project.git
```


### git branch
```
git branch -v
git branch —-merged
git branch —-no-merged
git branch -vv          —-> Tracks the tracking branches
```

### git push
```
git push origin local branch:remotebranch
git push origin --delete branch           —-> This deletes the remote branch
```

### git checkout
```
git checkout -b serverfix origin/serverfix    -—> This bases the serverfix branch out of the remote branch
```

### git fetch
```
git fetch --all ; git branch -vv
git fetch origin refs/pull/123/head   --> Fetches the pull request
```


### git merge
```
git merge --no-commit --squash branchname   --> Gets all the work on the merge
                                                branch and squashes into on non-merge commit,
                                                --no-commit --> Dont automatically record a commit
git merge -Xignore-all-whitespace
```

### git reset
```
git reset --soft HEAD~  --> resets the HEAD and points to prev commit
git reset --mixed HEAD~ --> This is the default it also changes the staging area (Like no git add was done)
git reset --hard HEAD~  --> This also change the working directory so be very careful
```

### git blame
```
git blame -L 12,22 filename
git blame -L -C 12,22 filename --> See where the snippets originally came from
```

### git bisect
```
git bisect Start
git bisect bad
git bisect good v1.0
git bisect run test-error.sh
```

### git submodule
```
git submodule add url
git submodule init
git submodule update
git submodule foreach 'git checkout -b featureA'
```

### git rev-list
```
git rev-list SHA1..SHA2       --> Get all the SHAs in between to SHAs
```

### git cat-file
```
git cat-file commit SHA       --> Get commit message
```


### git request-pull
```
git request-pull origin/master remoteurl  --> Get all the changes from remoteurl and pull to master
```

### git format-patch
```
git format-patch      --> Generate the mbox-formatted files
git format-patch -M   --> Look for renames
```

### git send-email
```
git send-email *.patch --> Sends the patch as email (Set email in ~/.gitconfig)
```

### git apply
```
git apply patchname.patch         --> use this if the patch format is created with diff
git apply patchname.patch --check --> check if the patch will be applied cleanly
```

### git am
```
git am patchname.patch            --> use this when the format-patch command has been used to create the patch
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

### git ls-remote
```
git ls-remote           --> Get list of remote branches
```
### git count-object
```
git count-objects -vH   --> count the size and objects on a repo
```

### Sign tag and view
```
gpg --list-keys
gpg -a export {pub from prev output} | git hash-object -w --stdin
git tag -a maintainer-gpg-pub {SHA-1 from prev}
git show maintainer-gpg-pub | gpg --import
```

### Git filter-branch
```
git filter-branch --all                   --> Runs this on all branches
git filter-branch --subdirectory-filter trunk HEAD
git filter-branch --tree-filter 'rm -rf [/path/to/spurious/asset/folder]'
```
### Create git server

1. git clone --bare my_project my_project.git`
2. Copy project to git server `scp -r my_project.git user@git.example.com:/srv/git`
3. Give project shared access `git init --bare --shared`
4. Test and clone to client: `git clone user@git.example.com:/srv/git/my_project.git`


### Extra git arguments
GIT_TRACE=1  GIT_TRACE_PACKET=1
