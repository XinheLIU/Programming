# Git Cheatsheet

## Version Control

- keep track of changes
- keep original versions \(every committed versions\)
- synchronize code
- revert back to old version
- branching: create different versions of different repo
- merge
- pull requests

## Commands

![Git Data Transport Commands](https://www.stephenmarron.com/wp-content/uploads/2017/02/git-880x440.png)

- git clone &lt;url&gt; : make a copy of a repository on your computer 
  - a "fork" creates your copy
- git add &lt;filename&gt; : add file to staging area, tells git to include the files
  - git add \- adds all changed files
  - git add . adds all new files
  - git add -u updates tracking for files that changed name or been deleted
  - git add -A: combines . and u
- git commit -m &lt;"message"&gt;: save changes to repository as a new version
  - git commit -am "msg": combines add and commit
- git status: show current status of a repository
- git push: sends committed changes to **remote repository**
  - remote add origin &lt;git URL&gt;
  - git push -u origin &lt;branch&gt; \(eg. master\)
    - -u
- git pull: retrieves changes from remote directory
  - show difference and merge conflicts
- git log: shows a history of commits and messages
  - git log --online
- git revert &lt;commit ref&gt;
  - git reset --hard &lt;commit&gt; : revert back to previous commit
    - git reset --hard origin/master: revert back to original version
- git branch: shows different branch of code
  - git branch &lt;branch\_name&gt;: create new branch
  - git branch -D &lt;branch\_name: delete the branch
- git checkout &lt;branch\_name&gt;: check out to a different branch
  - git checkout -b &lt;branch name&gt;: create a new branch
- git merge &lt;branch\_name&gt;: merges the &lt;branch\_name&gt; to current branch
- git stash
  - saves uncommited changes on a stack
  - git stash list, git stash apply, git stash pop
- git config --global user.name/user.email &lt;input&gt;
  - git config --list
- exist : exist git
