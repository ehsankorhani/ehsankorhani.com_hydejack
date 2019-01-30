---
layout: post
title: "Git Fundamentals"
date: 2019-01-27
---

## Git Fundamentals

#### Development without version control softwares
* Backup files
* Comments
* ...

#### Two types of version control software
1. Centeralized
2. Distributed

#### How this is structured
1. Git basic commands (and a demo project)
2. Git GUI interface
3. Git Flow

#### Get Git
Download git for windows and install it.
- https://gitforwindows.org/
- https://git-scm.com/downloads

### Git Commands
##### initiate a repository

```bash
git clone <address>
or
git init <directory>
```

_no __directory__ param to convert the current folder to repo_
_with __directory__ param to create git in the specified directory_
    
.git folder will be created to track the changes

#### Git Config
```bash
git config --global --edit
git config --local --edit
git config --global user.name "username"
git config --global user.password "password"
```

##### Create a demo project
```bash
git init myapp
```
A simple web app

#### git workflow / trees
1. working direcotry
2. Index (staging)
3. HEAD (commited)

##### Create a remote repo
* Clone the repo

**Note**
1. One item in vs code changes
2. master is checked out

```bash
git status
```

**Note:**
master branch
- is first branch
- has to be clean
- branch others from this

##### Untracked files
**Stage** file
```bash
git add index.html
```
Remove tracking and mark as deleted but keep the file
```bash
git rm --cached index.html
```

Or stage all files:
```bash
git add .
```
And then

```bash
git reset HEAD -- index.html
```

*empty folders are not tracked*

##### Push changes to remote
* Add a css file
* Add a js file
* Stage main.css
* Stage changes for html changes

```bash
git push -u <remote_name> <local_branch_name>
git commit -m "initial commit"
```
or use VS Code

* stage app.js
* commit
* push

**Always pull before push**

###### git pull: when we have different HEAD
* make changes in remote
* make changes in local
```bash
git pull
```
*Error:* Your local changes to the following files would be overwritten by merge.

1. commit changes
2. git pull again
3. resolve the conflict
4. save, commit, push
5. view remote repo

##### git push: when we have different HEAD at remote
1. make changes at remote
2. make changes at local
```bash
git push origin master
```
*Error!!!*

##### Rebase
If you have permission
```bash
git push origin master --force
```
    
##### What is pull
*fetch + merge*

1. change remote
2. change local and commit
```bash
git fetch
git merge
```

##### Undo changes
Replace local changes with HEAD
```bash
git checkout -- <file>
```

Reset changes to remote HEAD
```bash
git fetch origin
git reset --hard origin/master
```

Reset changes to last HEAD
```bash
git reset --hard HEAD~1
```
*Omitting --hard will leave the files but moves the pointer*

##### Reverting
Forward moving undo operation
Makes an opposite change and commits
1. Make some change
2. Commit change
```bash
git revert <commit_id>
```

3. Provide commit message
4. Check it with git log

#### Stashing
1. make modification
2. make modification to same file in origin
```bash
git pull
```
*Error!*

* stash local file:
```bash
git stash
git stash push -m "stash js" js/app.js
git stash push -- path/to/folder
```
```bash
git pull
```

###### Reapply stash
```bash
git stash list
git stash pop (last one)
```
Or
```bash
git stash apply stash@{0}
```

Delete a stash
```bash
git stash drop stash@{1}
```
Delete stash ALL
```bash
git stash clear
```

#### What if you don't want git to track your files or folders?
1. create a file on root and a folder with file
2. git recognized them as untracked
3. Create a file with this name:
```
.gitignore
```
4. add files and folders
5. new files will be removed from git list

#### Branching
Best practice:
* **master** should remain clean.
* **develop** branch for developers
* for each task create a **feature branch**

##### naming convention
```html
<type>/<name>
```
* bug    - Code changes linked to a known issue.
* feat   - New feature.
* hotfix - Quick fixes to the codebase.
* junk   - Experiments (will never be merged).

example
* feat/employer-360-view
* bug/chatter-mention-list
    
##### create dev branch
1. from github
2. Branch -> dev
3. on local:
```bash
git fetch
git ckeckout dev
```

4. on local: (based on current HEAD)
```bash
git branch feat/new-task
git checkout feat/new-task
```
or =
```bash
git checkout -b feat/new-task
```
5. push branch
```bash
git push origin feat/new-task
```

#### Merging
merging into your branch:
1. make changes in dev
2. stage and commit
3. checkout feature branch
```bash
git merge dev
```
#### Pull Request & Code Review
merge to remote
1. make changes in branch
2. push to remote:

```bash
git push origin feat/new-task
```

3. check github
4. go to feature branch
-> new pull request
6. go to pull requests
7. review code
8. Select type of Merge (merge / squash / rebase)
9. Confirm request      
*you have the option to delete the branch*
*delete the local branch independently*

#### Extra Options
* git diff master dev
* git log
* VS Code gitlens extension
* gitk
* Atlassian SourceTree