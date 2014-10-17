## Tiny Git Tutorial

### Download git

| Operating System | Link |
|---	|---	|
| Windows | [Download](http://git-scm.com/download/win) |
| Linux	| [`apt-get install git`](http://git-scm.com/download/linux) |
| OSX	| [Download](http://git-scm.com/download/mac)	|

This is a small collection of commands used in git. For an example workflow using git take a look at this [log file](example-local-repository-basics.md).

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
git add -A :/               # stages All files in the repository
# git add .                 # stages new and modified in directory, without deleted
# git add -u :/             # stages modified and deleted, without new
git pull                    # equals: git fetch; git merge FETCH_HEAD
git status                  # check if merge was successful
git commit -m "my commit message"
git push origin master      # upload to github repostitory, branch name 'master'
git log                     # check current version history via commit messages
git log --oneline myfile    # show version history of file 'myfile'
```

### Undo actions
Use to unstage or edit commits
```bash
git reset HEAD               # undo adding all files in the index (after git add <...>)
git rm --cached              # delete file fom the repo, leaving only a local copy

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
# git checkout someBranch   # go back to an existing branch like 'master'
git push origin myFeature   # convert private branch to public repository
git pull                    # first get the newest rep. version...
git merge myFeature         # ...then merge with your branch
```
If merging yields some error messages, try to solve them manually
```bash
git diff <source_branch> <target_branch>
git diff HEAD^ myfile      # difference of current 'myFile' and the one from last commit (HEAD~1)
```

### Compress history (optional)
To only submit a subset of commits performed locally during one day of frequently committed small pieces of work, squash commits together into a bigger one before pushing them to the remote repository.
```bash
git rebase -i HEAD~3

[EDITOR]
pick 1fc6c95 The oldest of the three commits.
pick 6b2481b A patch.
pick dd1475d My last commit message.
```
Interactively edits the last three commits.
In response, the text editor appears.
Change all but the oldest commits' `pick` to `squash` to meld one commit into the previous.

**Note**: Don't prune a good version history! Use this for a series of very small changes only - like typo correction, or subsequent small changes necessary for this version to finally compile/run which you did not intend to create at all.

### Additional sources to learn git(hub)

* [Github::Resources](https://help.github.com/articles/what-are-other-good-resources-for-learning-git-and-github/)
* Commit message guidelines from [openstack.org](https://wiki.openstack.org/wiki/GitCommitMessages) and [stackoverflow.com](http://stackoverflow.com/questions/43598/suggestions-for-a-good-commit-message-format-guideline)
