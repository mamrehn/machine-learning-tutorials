# Initialize a local git repository
Call once
```bash
git init
#git clone https://github.com/mamrehn/machine-learning-tutorials.git
git config --global user.name "my Name"
git config --global user.email "me@website.com"
git config --global credential.helper "cache --timeout=3600"
git remote add origin https://github.com/mamrehn/machine-learning-tutorials.git
git fetch origin
```

# Add changes in the filesystem to github
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

# Branches
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
