### Fork & Clone
- fork creates a completely independent copy of Git repository.
- clone creates a linked copy that will continue to synchronize with the target repository.

### config username and email
```shell
# Config
git config --global user.name "username"
git config --global user.email "email"

# Change config
git config --global user.name "username"
git config --global user.email "email"

# Show
git config user.name
git config user.email

# Show all configuration
git config --list
```

### initialize
```shell
git init
```

### commit
```shell
git commit -m "commit description"

# Includes all currently changed files in this commit
git commit -a -m "commit description"

# Rewirtes last commit
git commit --amend -m "commit description"
```

### ignore (.gitignore file)
```shell
# ignore all .txt files
*.txt

# exception name.file file
!name.file

# ignore all files in temp directory
temp/

# all folders ending with name
*name/

# ? matches a single non-specific character
name?.file

# [range] matches a single character in specified range
name[a-z].file
# [set] matches a single character in specified set of characters
name[abc].file
# [!set] matches a single character except the ones specified set of characters
name[!abc].file
```

### branch
```shell
# show current branch and all branch
git branch
# list all remote branches
git branch -a

# create new branch call <branch>
git branch <new-branch>

# rename current branch to <branch> name
git branch -m <exist-branch>

# safe delete (not delete when unmerged) 
git branch -d <exist-branch>
# force delete 
git branch -D <exist-branch>
# delete branch in remote
git push origin --delete <exist-remote-branch>
	or
git push origin :<exist-remote-branch>
```

### checkout
```shell
# create new branch and check out that branch
# -b equavallent to git branch <branch>
git checkout -b <new-branch>

# switch branch to <branchname>
git checkout <branchname>

# checkout remote branch
# first fetch all contents of the branch
git fetch --all
# then checkout <remotebranch>
git checkout <remote-branch>
```

### merge
```shell
# before merge check HEAD is pointing to the correct merge-receiving branch.
# checkout the main branch that want to be merged into
git checkout <branchname>

# pull the latest remote commits
git fetch
# after fetch use git pull to ensure the branch has latest updates
git pull

# merge feature to currently checkout branch
git merge <feature-branchname>

# merge feature to currently checkout branch and keep all the history
git merge --no-ff <feature-branchname>

# conflict
# check what file are conflict
git status

# <<<<<<< receiving branch
# >>>>>>> merging branch

```


### log
```shell
# show local history include all the reference
git reflog

# show public history 
git log
git log --pretty=oneline
```

### revert
```shell
# create new commit by not deleting other commit
git revert <commitid>
```

### reset
```shell
# revert back to old commit and remove commit after the commit your reset to
git reset <commitid>
```

### detached HEAD state
```shell
# normal HEAD state will point to the lastest commit of current checkout branch

# solution
"Save change to the detached HEAD state"
- create a new branch
- commit the chneages
- merge the changes

"Discard change to the detached HEAD state"
- checkout the branch
```

### Resources
- [gitmoji](https://gitmoji.dev/)
- [shields.io](https://shields.io/)
