## Tiny Git Tutorial

### Download git

| Operating System | Link |
|---	|---	|
| Windows | [Download](http://git-scm.com/download/win) |
| Linux	| [`apt-get install git`](http://git-scm.com/download/linux) |
| OSX	| [Download](http://git-scm.com/download/mac)	|

### Initialize a local git repository
Execute once
```bash
git init
#git clone https://github.com/mamrehn/machine-learning-tutorials.git
git config --global user.name "my Name"
git config --global user.email "me@website.com"
git config --global credential.helper "cache --timeout=3600"
git remote add origin https://github.com/mamrehn/machine-learning-tutorials.git
git fetch origin
```

### Add changes in the filesystem to github
Call when updating
```bash
git add -A                  # stages All
# git add .                 # stages new and modified, without deleted
# git add -u                # stages modified and deleted, without new
git pull                    # equals: git fetch; git merge FETCH_HEAD
git status                  # check if merge was successful
git commit -m "my commit message"
git push origin master      # upload to github repostitory
git log                     # check current version history
```

### Undo actions
Use to unstage or edit commits
```bash
git reset HEAD              # unstage all files in the index (after git add <...>)

git config --global alias.unstage 'reset --'
git unstage my/file.txt     # after this config adjustment, unstaging per path is possible

git commit -m 'my message'
git add forgotten_file
git commit --amend          # add forgotten_file to the previous commit

git checkout -- myFile.txt  # unmodify myFile.txt by replacing it from HEAD
```

### Branches
Use branches for bigger projects and more elegant history.
```bash
git checkout -b myFeature   # create new current branch named myFeature
# git branch -d myFeature   # delete branch myFeature
# git checkout master       # go back to the master
git push origin myFeature   # convert private branch to public repository
git pull                    # first get the newest rep. version...
git merge myFeature         # ...then merge with your branch
```
If merging yields some error messages, try to solve them manually
```bash
git diff <source_branch> <target_branch>
```

### Compress history (optional)
To only submit a subset of commits performed locally during one day of frequently committed small pieces of work, squash commits together into a bigger one before pushing them to the remote repository.
```bash
git rebase -i HEAD~3

[EDITOR]
pick 1fc6c95 My last commit message.
pick 6b2481b A patch.
pick dd1475d The oldest of the three commits.
```
Interactively edits the last three commits. 
In response, the text editor appears.
Change all but the newest `pick` to `squash` to meld one commit into the previous.

**Note**: Don't prune a good version history! Use this for a series of very small changes only - like typo correction.

### Additional sources to learn git(hub)

* [Github::Resources](https://help.github.com/articles/what-are-other-good-resources-for-learning-git-and-github/)
* Commit message guidelines from [openstack.org](https://wiki.openstack.org/wiki/GitCommitMessages) and [stackoverflow.com](http://stackoverflow.com/questions/43598/suggestions-for-a-good-commit-message-format-guideline)
