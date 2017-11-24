### Git Cheatsheet

##### List of all basic and minimum Git commands

<br/>

```
Working Area –-> git add file --> Staging Area –-> git commit --> Commit Area
```

<br/>

```
git init
```

Initiate `.git` directory in current working directory.

<br/>

```
git init cookbook
```

Create `cookbook` directory and initiate `.git` directory inside `cookbook` directory

<br/>

```
git add file
```

Add file to staging area

<br/>

```
git add .
```

Add all files to staging area

<br/>

```
git rm file
```

Remove file from staging area. In next commit, file will be deleted. Require `-f` if file is already modified and still exist
in staging area

<br/>

```
git rm --cached file
```

Remove file from staging area and keeps in working directory as untracked

<br/>

```
rm file
```

Remove file from working area. If already in staging area then need `git add/rm` to include it in
next commit for deletion

<br/>

```
git commit -m "message"
```

Move staging area files to commit area

<br/>

```
git commit -a -m "message"
```

Add files to staging area and then move from staging area to commit area. This command is equal to `git add .` and then `git commit -m "message"`

<br/>

```
git log
```

List all the commits of current branch

<br/>

```
git log -p
```

List all commits with difference in each two commits

<br/>

```
git log -2
```

Show last 2 commits from current branch

<br/>

```
git log –oneline
```

Show oneline detail about each commit incluing commit hash and commit message.

<br/>

```
git show
```

Show details of last commit from current branch

<br/>

```
git show commit_hash
```

Show details about specific commit. commit_hash must be a valid commit hash e.g 92323bc7dcdef

<br/>

```
git diff
```

Show changes not staged yet. difference between staging area and working area

<br/>

```
git diff –stage
```

Show changes which are staged already. Changes between staging area and commit area

<br/>

```
git diff fix_branch
```

Compares the last commit of the branch you’re on and the last commit on the `fix_branch`

<br/>

```
git diff --check
```

Identifies whitespaces errors. Extra whitespaces in a file

<br/>

```
git diff-tree -r commit_hash
```

List of files that has been modified in that commit hash

<br/>

```
git checkout commit_hash
```

This will will move you to the `commit_hash` where you can view your project as it was at that particular
commit. You can create new branch from here by passing `git branch branch_name`. 
To go back to original state use: `git checkout branch_name`

<br/>

```
git reset HEAD
```

Unstage a file without changing in it working directory. Roll back `git add` without touching
changes. Move commit pointer to HEAD but doesn't change files in working directory. HEAD = last commit

<br/>

```
git reset –hard HEAD
```

Move pointer to last commit and change staged files back to last commit state as well.

<br/>

```
git reset –hard HEAD~
```

~ = tilde
~ = number of parents

<br/>

```
git reset –hard HEAD~~ == git reset –hard HEAD~2
```

Reset to 2 parents of the last commit

<br/>

```
git reset HEAD file
```

Reset file to last commit. same tilde(~) can be applied here.

<br/>

```
git checkout -- file
```

Remove changes from a file in working directory which is not staged yet. Roll back file to its last commit
`reset` is used to roll back committed files. 
`rm` or `--cached`` is used to roll back staging area files.
`checkout --` is used to roll back files in working directory.

<br/>

```
git stash
```
Record the current state of the working directory and staging area. The command saves your local modifications away and 
reverts the working directory to match the HEAD commit.

<br/>

```
git stash apply
```

Brings back stashed changes (working directory and staging area) on the top of HEAD

<br/>

```
git stash drop
```

Remove stash back once you are done.

<br/>

```
git remote show origin
```

Show details about `origin`

<br/>

```
git ls-remote
```

List all remote branches

<br/>

```
git remote add REMOTE_NAME REMOTE_URL
```

Add remote url to the current working git repo

<br/>

```
git remote set-url REMOTE_NAME
```

Update remote branch url

<br/>

```
git checkout -b fix origin/test
```

Create, Pull and Rename remote branch `test` to `fix` (local)

<br/>

```
git checkout test
```

Pull and switch to `test` branch If exist locally or remote

<br/>

```
git branch fix
git checkout fix
git branch -u origin/test
```

Create branch `fix`
switch to branch `fix`
set upstream of `fix` branch to `origin/test` to track `remote/test`. 

Above commands are equal to below

<br/>

```
git checkout -b fix origin/test 
```

`-u === --set-upstream-`

<br/>

```
git branch -v
```

List all branches with last commit hash, commit message and * on active branche.

<br/>

```
git branch -vv
```

List all branches with last commit hash, commit message, * on active branch and remote up-stream branch

<br/>

```
git branch -m old_name new_name
```

Rename local branch name

<br/>

```
git branch -m new_name
```

Rename local branch name if you are on current branch

<br/>

```
git push origin –delete test
```

Delete `test` branch from remote repository

<br/>

```
git merge fix_branch
```

This will either just fast forward and move pointer to last commit OR create a merge commit and move pointer to that commit, 
depending whether HEAD of current branch is parent of last commit (of fix_branch) or not.
`git merge –ff fix_branch === git merge fix_branch`

<br/>

```
git merge –no-ff fix_branch
```

Create a new merge commit and move pointer to that whether HEAD of current branch is parent of last commit of fix_branch or not.
The `--no-ff` option ensures that a fast forward merge will not happen, and that a new commit object will always be created 
even if git would normally fast forward.

<br/>

```
git merge –ff-only fix_branch
```

This will check if fast forward is possible then will do it otherwise will abort saying fast forward not possible I.e if HEAD 
of current branch is not parent of last commit of `fix_branch`

<br/>

```
git checkout –ours conflicted_file
```

Keep current branch changes and remove other branch's changes from file having conflicts

<br/>

```
git checkout –theirs conflicted_file
```

Remove current branch changes and keep other branch's changes from file having conflicts

<br/>

```
git cherry- pick commit_hash
```

Clone a commit from other branch, to current branch on the top of HEAD and move pointer to it.

<br/>

```
git revert commit_hash
```

Inverse of `cherry-pick`. Pick that commit, revert changes in that commit, create a new commit and put those changed in new commit

<br/>

```
git rebase -i HEAD~2
```

Squash last 2 commits into single commit

<br/>

```
git tag
```

`tag` is like branch but don't move like branch. Tags do push with push commands. Can't be changed once created.
lightweight tag is simple pointer to a commit.
annotated tag is new commit pointing to a commit with details notes

<br/>

```
git blame file
```

For every line of file, it shows who changed it last time

<br/>

[Git Interview Questions 1](https://www.toptal.com/git/interview-questions)

<br/>

[Git Interview Questions 2](https://mindmajix.com/git-interview-questions)



