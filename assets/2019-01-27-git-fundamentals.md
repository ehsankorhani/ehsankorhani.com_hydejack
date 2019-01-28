---
layout: post
title: "git Fundamentals"
date: 2019-01-27
---
- Development without source/version control

- Version Control Systems
- 3 phases:
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
    -- make changes in remote
    -- make changes in local
    -- git pull
        - Your local changes to the following files would be overwritten by merge
        - commit changes
        - git pull again
        - resolve the conflict
        - save, commit, push
        - view remote repo



--- git config