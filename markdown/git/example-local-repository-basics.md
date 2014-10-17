## Git example workflow
This is an example workflow with git to demonstrate the usage of its basic commands.

First, go to your target directory like `~/my/path/` or `C:\my\path\` and create a new git repository.
```bash
$ git init
Initialized empty Git repository in c:/my/path/.git/
```
Then create some content.
```bash
$ echo "<html><head><title>Test Website</title></head>
          <body>There is no text yet</body>
        </html>" > index.html
```
### Commit files
Add all files (`index.html`) from the current directory (`.`) to git's staging area.
```bash
$ git add .
```
Check whether git recognized the file.
```bash
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   index.html
```
Commit the staging area to the local repository. This creates a new fixed version of your repository. You can always go back to this current state of files.
```bash
$ git commit -m "Initial commit. First website."
[master (root-commit) 8d5d2b6] Initial commit. First website.
warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory.
 1 file changed, 1 insertion(+)
 create mode 100644 index.html
```
Note: The warning message informs users that git will take care of the line feed or new line (\n) character vs. carriage return line feed (\r\n) problem on different operating systems.

After the file(s) are committed, check the version history. There is an entry with the commit message.
```bash
$ git log
commit 8d5d2b63b53c2d9cb3c8a0f02c552fdee52b5106
Author: myUsername <mail@server.com>
Date:   Fri Oct 17 16:09:21 2014 +0200

    Initial commit. First website.

user@computer /C/my/path (master)
```
### Branching
Now, add a new feature in an save environment - a branch. Therefore, the unfinished changes will not alter the main version history of your repository called the `master` branch. BRanches are created by the *-b* (branch) flag of the *checkout* command. Call the new branch *content_for_website*.
```bash
$ git checkout -b content_for_website
Switched to a new branch 'content_for_website'

user@computer /C/my/path (content_for_website)
```
Add some changes to the file(s).
```bash
$ echo "<html><head><title>Test Website</title></head>
          <body>Some text</body>
        </html>" > index.html
```
Now commit them. Editing, creating or deleting files cause the staging area to change.
```bash
$ git status
On branch content_for_website
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
```
In order to commit, add the updated (*-u*) files to the staging area.
```bash
$ git add -u .
warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory.
```
The current content of the stagig area. Notice that the suggestion to *add* disappeared.
```bash
$ git status
warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory.
On branch content_for_website
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   index.html

user@computer /C/my/path (content_for_website)
```
Finally, commit to the current branch `content_for_website`.
```bash
$ git commit -m "Website's final version."
[content_for_website warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory.
c843e99] Website's final version.
warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory.
 1 file changed, 1 insertion(+), 1 deletion(-)

user@computer /C/my/path (content_for_website)
```
#### Add small changes into existing commit
Commits should represent a coherent set of changes. If a new commit is only a small addition to an existing one, try to squash them into one.

Assume that the content in the example needs to be changed again and this change is to small for a proper commit.
```bash
$ echo "<html><head><title>Test Website</title></head><body>Some text. And this
..</body></html>" > index.html

user@computer /C/my/path (content_for_website)
```
Add and commit the change.
```bash
$ git add -u .
...
$ git commit -m "Late addition to website."
...
```
Now, there are three commits in the local git repository.
```bash
$ git log
commit 07b7eb88f933ce2160f03b85dcd54ea5f88c68cf
Author: myUsername <mail@server.com>
Date:   Fri Oct 17 16:18:02 2014 +0200

    Late addition to website.

commit c843e999a61e278b3096e09ac823ec8289d9fd5c
Author: myUsername <mail@server.com>
Date:   Fri Oct 17 16:16:37 2014 +0200

    Website's final version.

commit 8d5d2b63b53c2d9cb3c8a0f02c552fdee52b5106
Author: myUsername <mail@server.com>
Date:   Fri Oct 17 16:09:21 2014 +0200

    Initial commit. First website.

user@computer /C/my/path (content_for_website)
```
Use the last two (`HEAD~2`) of them and change them into one by rebasing interactively (`-i`).
```bash
$ git rebase -i HEAD~2

[detached HEAD ae4612f] Website's final version.
 1 file changed, 1 insertion(+), 1 deletion(-)
Successfully rebased and updated refs/heads/content_for_website.

user@computer /C/my/path (content_for_website)
```
Due to the interactive mode, your default editor will show. Edit the displayed files contents in a way that the first `pick` is preserved and the other ones are replayed by `s` or `squash`.
```bash
pick c843e99 Website's final version.
s 07b7eb8 Late addition to website.
```
A new file will be displayed by the text editor regarding the joined commit message.
In this example, only the original or first commit message was used ("*Website's final version.*").
```bash
$ git log
commit ae4612f0f0c2072faac2d222adacc52c3219bf8a
Author: myUsername <mail@server.com>
Date:   Fri Oct 17 16:16:37 2014 +0200

    Website's final version.

commit 8d5d2b63b53c2d9cb3c8a0f02c552fdee52b5106
Author: myUsername <mail@server.com>
Date:   Fri Oct 17 16:09:21 2014 +0200

    Initial commit. First website.

user@computer /C/my/path (content_for_website)
```
#### Merge branch back to the master
Switch to the master banch by filling the repositories directory with the files from `master`.
```bash
$ git checkout master
Switched to branch 'master'

user@computer /C/my/path (master)
```
Notice that `/C/my/path (content_for_website)` changed back to `/C/my/path (master)`.

For a rather graphical display of the current branches you may use one of these commands. More at [stackoverflow.com](http://stackoverflow.com/questions/1057564/pretty-git-branch-graphs).
```bash
$ git log --graph --oneline --all
$ git log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
```
Merge *content_for_website* into the current branch, which is the *master*.
```bash
$ git merge content_for_website
Updating 8d5d2b6..ae4612f
Fast-forward
 index.html | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

user@computer /C/my/path (master)
```
Show the current version of *index.html* in the master branch!
```bash
$ cat index.html
<html><head><title>Test Website</title></head><body>Some text. And this..</body>
</html>
```

