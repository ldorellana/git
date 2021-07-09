# GIT BASICS

### SET NAME AND EMAIL
```
git config --global user.name '{name}'
git config --global user.email '{email}'
git config --global core.editor '{editro}' # 'code --wait' for VScode
```

### CHECK IF WE ARE IN GIT REPO
```
git status 
```

### START A GIT REPO
```
git init
```

### ADD NEW AND MOD FILES [DOCS](https://git-scm.com/docs/git-log)
```
git add file1 file2 file3 # add specific files
git add . # add all the changes
```

### COMMIT CHANGES

```
git commit -m '{message}' 
git commit --amend # correct the previous commit
```

### CHECK COMMITS
```
git log
git log --oneline
```

### IGNORE FILES
Inside the file `.gitignore` 
```
filename.extension # ignore this file
*.file_extension # ignore files with that extension
folderName/ # ignore the folder
```

### HEAD
Head is a pointer to a branch pointer
Current location in the branch. 
If we move to another branch, it has a different head

### BRANCHES
```
git branch # show the branches * = current branch
git branch {branch_name} # create new branch at current HEAD
git switch {branch_name} # change to a different branch
git checkout {branch_name} # also change to another branch
git switch -c {branch_name} # create a new branch and switch to it
git checkout -b {branch_name} # create a new branch adn switch to it
```

#### Delete branches
First switch to a different branch, then merge it, then delete it
```
git merge?
git swtich {other_branch}
git branch -d {branch_to_delete} # -D to force delete
```

#### Rename branch
first switch to the branch to rename
```
git switch {branch_to_rename}
git branch -m {branch_to_rename} {new_branch_name}
```

### MERGE BRANCHES

*Fast forward merge* the branch just needs to catch up to the other (move the head)
*Merge commit* the main branch gets a new commit


- Branches are merge, not specific commits
- Always merge to the current HEAD branch
1. Move to the 'main' branch
2. Merge the branches
```
git switch {main_branch}
git merge {branch_to_merge}
```

#### Merge Conflicts
1. Open the files with conficts
2. Edit to remove the conflicts, keep one of both 
3. Remove the conflict markers
4. Add changes and make the commit


### GIT DIFF
Lists all the changes in the working directory
```
git diff # compares unstaged changes 
git diff HEAD # staged and unstaged chagnes since HEAD
git diff --staged/--cached # list changes between staged area and last commit
git diff {filename} # diff specific files, can add --staged, HEAD, etc
git diff branch1..branch2  # compare different branches
git diff commit1..commit2 # compare changes between commits, can get commit code with log

```

### GIT STASH
 Allows you to change branch 
 - without takin the changes to the new branch
 - without having to commit the changes if we are not done yet

```
git stash # save changes in stash
git stash save # same as git stash
git stash pop # take out the changes
git stash apply # the changes are not deleted from stash like in pop
git stash list # show the different stashed changes
git stash apply stash@{#} # apply a saved stash in the list
git stash drop stash@{#} # drop an specific stash
git stash clear # delete all the stash
```

```
1. git stash
2. git switch other_branch
3. Do stuff
4. git swtich previous_branch
5. git stash pop
```

### CHEKING OUT OLD COMITS 

Head detached, going check to a previous commit
```
git checkout {commit_hash}
```
Get back to a branch
```
git switch {branch_name}
```
Create a new branch
```
git switch -c {new_branch_name}
```
Check previous commits
```
git checkout HEAD-{n}   # check a previous commit n = 1 one before, etc. 
```
Return to the branch beore the head detach
```
git switch - # return to the commit beore 
```

### DISCARDING THE CHANGES BEFORE COMMIT
To discard the changes done before the last commit
```
git checkout HEAD file # return file to its state when head started
git chekcout -- file # same as the previous
```

```
git restore {file} # restore a file to the state after the last commit
```
Return to a previous commit
```
git restore --source HEAD~{n} {file} # return to the specified commit
```
### UNSTAGE FILES
```
git restore --staged {file} # usntage files
```

### RESET COMMITS
The reset will delete the commits, but not the changes  
so then it is possible to re-commit in another branch if needed
without loosing the progress
```
git reset {commit_hash} # deletes the commmits but not the changes
git reset --hard {commit_hash} # delets the changes and commits
```

### REVERT COMMITS
Similar to reset, but does not delete the "history"
*reset* creates a new commit with the reverted changes  
*reset* moves the commit pointer backward  
```
git revert {commit_hash}
```

