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
git add -A   # stages All
# git add .  # stages new and modified, without deleted
# git add -u # stages modified and deleted, without new
git pull
git status
git commit -m "my message"
git push origin master
git log
```

Use [branches](http://rogerdudler.github.io/git-guide/index.de.html) for bigger projects and more elegant history.