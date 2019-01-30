---
layout: post
title: "Git Fundamentals"
date: 2019-01-27
---

## Git Fundamentals

##### Development without version control softwares
* Backup files
* Comments
* ...

##### Two types of version control software
1. Centeralized
2. Distributed

##### Version Control Systems
3 phases
    - git basic commands (demo project)
    - git GUI interface
    - git flow

- Git installation - for windows

- commands:
    - initiate a repository
        - git clone <address>
        - git init <directory>
            - no param to convert the current folder to repo
            - to create git in the specified directory
    
    - .git folder will be created to track the changes

    - Config
        -- git config --global --edit
        -- git config --local --edit
        -- git config --global user.name "username"
        -- git config --global user.password "password"

    - Create a demo project
        - simple html website
        - bootstrap

    - git workflow / trees
        1. working direcotry
        2. Index (staging)
        3. HEAD (commited)

    -- create a remote repo
    -- clone the repo
    -- create a HTML app in VS Code
    * notice: 
        1. one item in vs code changes
        2. master is checked out
    -- git commands:
        - git status
            * notice:
                - on branch master
                    - first branch
                    - has to be clean
                    - branch from this
                - untracked files
        - git add index.html
        - git rm --cached index.html
            - removes tracking and mark as deleted but keep the file
        - git add .
            - all files
        - git reset HEAD -- index.html
            - preferred method
    * empty folders are not tracked
    -- add a css file
    -- add a js file
    -- stage main.css
    -- stage changes for html changes
    -- git push -u <remote_name> <local_branch_name>
        -- git commit -m "initial commit"
    -- use VS Code
        -- stage app.js
        -- commit
        -- push
    * always pull before push
    -- git pull: when have different HEAD
        - make changes in remote
        - make changes in local
        -- git pull
        - Your local changes to the following files would be overwritten by merge
        - commit changes
        - git pull again
        - resolve the conflict
        - save, commit, push
        - view remote repo
    -- git push: when have different HEAD at remote
        - make changes at remote
        - make changes at local
        -- git push origin master
        - Error!!!
            - rebase: git push origin master --force
    
    -- what is pull: fetch + merge
        - change remote
        - change local and commit
        -- git fetch
        -- git merge

    -- replace local changes with HEAD
        -- git checkout -- <file>

    -- reset changes to remote HEAD
        -- git fetch origin
        -- git reset --hard origin/master

    -- reset changes to last HEAD
        -- git reset --hard HEAD~1

    * omitting --hard will leave the files but moves the pointer

    -- Reverting: forward moving undo operation
        -make an opposite change and commits
        - make some change
        - commit change
        -- git revert <commit_id>
        - provide comit message
        - check it with git log

    -- Stashing
        - make modification
        - make modification to same file in origin
        -- git pull
        - error!
        - stash local file:
            -- (git stash)
            -- git stash push -m "stash js" js/app.js
            -- git stash push -- path/to/folder
        -- git pull

    -- Reapply stash
        -- git stash list
        -- git stash pop (last one)
            or =
        -- git stash apply stash@{0}

    -- delete last stash
        -- git stash drop stash@{1}
    -- delete stash ALL
        -- git stash clear

    -- What if you don't want git to track your files or folders?
        - create a file on root and a folder with file
        - git recognized them as untracked
        --.gitignore
        - add files and folders
        - new files will be removed from git list

    -- Branching
        - best practice:
        - master should remain clean.
        - dev branch for developers
        - for each task create a feature_branch

        - naming convention
            -<type>/<name>
            bug    - Code changes linked to a known issue.
            feat   - New feature.
            hotfix - Quick fixes to the codebase.
            junk   - Experiments (will never be merged).

            -example
            - feat/employer-360-view
        
        - create dev branch
            - from github
            - Branch -> dev
            - on local:
            -- git fetch
            -- git ckeckout dev

            - on local: (based on current HEAD)
            -- git branch feat/new-task
            -- git checkout feat/new-task
            or =
            -- git checkout -b feat/new-task
            
            - push branch
            -- git push origin feat/new-task

        - Merge
            - merging into your branch:
                - make changes in dev
                - stage and commit
                - checkout feature branch
                -- git merge dev

            - merge to remote - pull request
                - make changes in branch
                - push to remote:
                -- git push origin feat/new-task

                - check github
                - go to feature branch
                -> new pull request
                - go to pull requests
                - review code
                -> Select type of Merge (merge / squash / rebase)
                -> Confirm request      
                * you have the option to delete the branch
                * delete the local branch independently

            -- git diff master dev
            -- git log
            -- VS Code gitlens extension
            -- gitk
            -- Atlassian 