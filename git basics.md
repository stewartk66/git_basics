# Git Basics
## Configuration
### Global changes
```
stewa@LAPTOP-58OP9CKK MINGW64 ~
$ git config --global user.name "Stewart Keay"

stewa@LAPTOP-58OP9CKK MINGW64 ~
$ git config --global user.email "stewartkeay@aol.com"

stewa@LAPTOP-58OP9CKK MINGW64 ~
$ git config --global core.editor "nano -w"

stewa@LAPTOP-58OP9CKK MINGW64 ~
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
core.editor=nano.exe
credential.helper=manager
user.name=Stewart Keay
user.email=stewartkeay@aol.com
core.editor=nano -w
```
### Local changes
git config user.name "Stewart Keay"
git config user.email "stewartkeay@aol.com"

Use `git config user.name` or `git config user.email` to confirm


## Create Repository
```
stewa@LAPTOP-58OP9CKK MINGW64 ~
$ pwd
/c/Users/stewa

stewa@LAPTOP-58OP9CKK MINGW64 ~
$ cd MyStuff/

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff
$ mkdir git

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff
$ cd git

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git
$ mkdir git_basics

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git
$ cd git_basics/

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics
$ pwd
/c/Users/stewa/MyStuff/git/git_basics

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics
$ ls -a
./  ../

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics
$ git init
Initialized empty Git repository in C:/Users/stewa/MyStuff/git/git_basics/.git/

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ ls -a
./  ../  .git/

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
### nano editor commands 
```
nano <filename> to enter editor
ctrl-o to save
confirm name of file
ctrl-x to exit 
```

## git Add & a basic Commit
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ nano README.md

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git add README.md
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.mdstewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git commit      
[master (root-commit) 0cdbee0] init repo first commit
 1 file changed, 5 insertions(+)
 create mode 100644 README.md

* `git commit` on it's own will open the editor (nano) to allow insert of a comit message as one has not been provided in the command 
```

## .git folder

The `.git` folder holds all the version control information 
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics/.git (GIT_DIR!)
$ ls
COMMIT_EDITMSG  description  hooks/  info/  objects/
config          HEAD         index   logs/  refs/
```

## git status with local change 
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ nano README.md

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```
## git status with staged change 
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git add README.md
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md
```

## Get a history list  of commands used 
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ history
    1  git config --global user.name "Stewart Keay"
    2  git config --global user.email "stewartkeay@aol.com"
    3  git config --global core.editor "nano -w"
    4  git config --list
    5  pwd
    6  dir
    7  cd MyStuff/
    8  mkdir git
    9  cd git
   10  mkdir git_basics
   11  cd git_basics/
   12  pwd
   13  ls
   14  ls -a
   15  git init
   16  ls -a
   17  git status
   18  nano README.md
   19  nano README.md
   20  git status
   21  git add README.md
   22  git status
   23  git commit
   24  ls
   25  nano README.md
   26  git status
   27  git add README.md
   28  git status
   29  git commit -m "add and commit"
   30  nano README.md
   31  git add README.md
   32  git status
   33  git commit -m "some more info"
   34  history
```

## git log
### Full Output
`git log` defaults to HEAD
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git log
commit 02da17f1e9019cdf0dff341c226076e7ad9d8676 (HEAD -> master)
Author: Stewart Keay <stewartkeay@aol.com>
Date:   Mon Feb 24 17:59:34 2020 +0000

    add test about index

commit f77b9c86d86dedd81470656d8c41e7bd693799df
Author: Stewart Keay <stewartkeay@aol.com>
Date:   Mon Feb 24 17:50:04 2020 +0000

    some more info

commit 7784a0e8af4aeb417a4ac746499f4fef158824a0
Author: Stewart Keay <stewartkeay@aol.com>
Date:   Mon Feb 24 17:45:14 2020 +0000

    add and commit

commit 0cdbee0fe0a10962b340342ab2ce378fb8087850
Author: Stewart Keay <stewartkeay@aol.com>
Date:   Mon Feb 24 17:31:46 2020 +0000

    init repo first commit
```
### Basic Output
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git log --oneline
02da17f (HEAD -> master) add test about index
f77b9c8 some more info
7784a0e add and commit
0cdbee0 init repo first commit
```
## git diff 
### File in a commit
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff HEAD~2 README.md
diff --git a/README.md b/README.md
index c02ee6a..9678eeb 100644
--- a/README.md
+++ b/README.md
@@ -4,4 +4,7 @@
 - `status` : see the status of current repository
 - `add` : put files into the index
 - `commit` : add changes to master
+- commit has a -m property to allow addition of message,
+if excluded then git commit opens the editor

+index/staging area has files ot be committed
```
### Staged Changes 
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git add README.md
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff --staged
diff --git a/README.md b/README.md
index 9678eeb..23358b0 100644
--- a/README.md
+++ b/README.md
@@ -7,4 +7,7 @@
 - commit has a -m property to allow addition of message,
 if excluded then git commit opens the editor

+- `diff` : changes between 2 commits
+- `log` : list history
+
 index/staging area has files ot be committed
```
### Basic Command
Using `git diff` will show all the differences in the HEAD
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ nano README.md

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory
diff --git a/README.md b/README.md
index 23358b0..755923f 100644
--- a/README.md
+++ b/README.md
@@ -11,3 +11,8 @@ if excluded then git commit opens the editor
 - `log` : list history

 index/staging area has files ot be committed
+
+
+
+
+change not required
```
## git restore
### Restore a file from HEAD
Recent versions of git uses `git restore README.md`  
Older version would require `git checkout HEAD README.md`
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git restore README.md 

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
nothing to commit, working tree clean

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ cat README.md
# Git Basics 24/02/2020

- `init` : make current folder a git repository
- `status` : see the status of current repository
- `add` : put files into the index
- `commit` : add changes to master
- commit has a -m property to allow addition of message,
if excluded then git commit opens the editor

- `diff` : changes between 2 commits
- `log` : list history

index/staging area has files ot be committed
```
### Restore a file from a specific commit
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (
$ git log --oneline
d8d85ab (HEAD -> master) added diff and log
02da17f add test about index
f77b9c8 some more info
7784a0e add and commit
0cdbee0 init repo first commit

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (
$ git checkout f77b9c8 README.md
Updated 1 path from 30a9c15
```
### Restore a file to HEAD version
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git log --oneline
d8d85ab (HEAD -> master) added diff and log
02da17f add test about index
f77b9c8 some more info
7784a0e add and commit
0cdbee0 init repo first commit

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git checkout f77b9c8 README.md
Updated 1 path from 30a9c15

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff README.md

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff --staged
diff --git a/README.md b/README.md
index 23358b0..c1a688d 100644
--- a/README.md
+++ b/README.md
@@ -6,8 +6,3 @@
 - `commit` : add changes to master
 - commit has a -m property to allow addition of message,
 if excluded then git commit opens the editor
-
-- `diff` : changes between 2 commits
-- `log` : list history
-
-index/staging area has files ot be committed

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git log --oneline
d8d85ab (HEAD -> master) added diff and log
02da17f add test about index
f77b9c8 some more info
7784a0e add and commit
0cdbee0 init repo first commit

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ cat README.md
# Git Basics 24/02/2020

- `init` : make current folder a git repository
- `status` : see the status of current repository
- `add` : put files into the index
- `commit` : add changes to master
- commit has a -m property to allow addition of message,
if excluded then git commit opens the editor

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git checkout HEAD README.md
Updated 1 path from 18466e8
``` 

## Switching HEAD to a specific commit
Switch HEAD to a specific commit and use `git log` to check what commits are set up for this commit and also show that all commits are still available; HEAD is just pointing to a commit rather than `master` 
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git checkout f77b9c8
Note: switching to 'f77b9c8'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at f77b9c8 some more info

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics ((f77b9c8...))
$ git log --oneline
f77b9c8 (HEAD) some more info
7784a0e add and commit
0cdbee0 init repo first commit

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics ((f77b9c8...))
$ git log --oneline --all --graph --decorate
* d8d85ab (master) added diff and log
* 02da17f add test about index
* f77b9c8 (HEAD) some more info
* 7784a0e add and commit
* 0cdbee0 init repo first commit

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics ((f77b9c8...))
$ git checkout master
Previous HEAD position was f77b9c8 some more info
Switched to branch 'master'

```
## Update on commands used so far 
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ history
   ...
   ...
   35  ls -a
   36  cd .git
   37  ls
   38  cd ..
   39  ls
   40  git status
   41  anno README.md
   42  nano README.md
   43  git add README.md
   44  git commit -m "add test about index"
   45  git status
   46  git log
   47  git log
   48  git diff HEAD~2 README.md
   49  git log --oneline
   50  git status
   51  nano README.md
   52  git diff
   53  git log
   54  git add README.md
   55  git diff
   56  git diff --staged
   57  git commit -m "added diff and log"
   58  nano README.md
   59  git diff
   60  git restore README.md
   61  git diff
   62  git status
   63  cat README.md
   64  git log --oneline
   65  git checkout f77b9c8 README.md
   66  git status
   67  git diff
   68  git diff README.md
   69  git diff --staged
   70  git log --oneline
   71  cat README.md
   72  git checkout HEAD README.md
   73  git checkout f77b9c8
   74  git log --oneline
   75  git log --oneline --all --graph --decorate
   76  git checkout master
   77  nano Readme.md
   78  git --version
   79  history
```
## .gitignore file
Search internet for gitignore <language> and get the raw version. for example `gitignore python` will identify a gitignore file that has some basic python exclusions; ignore anything that can be recreated from source   

```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git add README.md

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git diff --staged
diff --git a/README.md b/README.md
index 23358b0..66201f6 100644
--- a/README.md
+++ b/README.md
@@ -10,4 +10,12 @@ if excluded then git commit opens the editor
 - `diff` : changes between 2 commits
 - `log` : list history

+log --oneline
+log --oneline --graph -- decorate
+
+checkout <hash> file : restore a file
+checkout <hash> : restore the entire folder
+
+
 index/staging area has files ot be committed
+HEAD where you are in the history

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git commit -m "log params & head note"
[master 6035e37] log params & head note
 1 file changed, 8 insertions(+)

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ nano .gitignore

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore

nothing added to commit but untracked files present (use "git add" to track)

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git add .gitignore
warning: LF will be replaced by CRLF in .gitignore.
The file will have its original line endings in your working directory

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git commit -m "add gitignore file"
[master 852e235] add gitignore file
 1 file changed, 2 insertions(+)
 create mode 100644 .gitignore

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ nano .gitignore

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ nano temp.temp

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        temp.temp

nothing added to commit but untracked files present (use "git add" to track)

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ nano .gitignore
*** Change to add *.temp files to the ignore file  ***

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   .gitignore

no changes added to commit (use "git add" and/or "git commit -a")
```
## .gitkeep
Creating a `.gitkeep` file will ensure that an empty folder is available to be committed.
```
stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ mkdir data

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ mkdir analysis

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ touch data/.gitkeep analysis/.gitkeep

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   .gitignore

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        analysis/
        data/

no changes added to commit (use "git add" and/or "git commit -a")

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git add .
warning: LF will be replaced by CRLF in .gitignore.
The file will have its original line endings in your working directory

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ git commit -m"ignore .temp file and add folders"
[master f39f1c6] ignore .temp file and add folders
 3 files changed, 1 insertion(+), 1 deletion(-)
 create mode 100644 analysis/.gitkeep
 create mode 100644 data/.gitkeep

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
$ ls -alh
total 11K
drwxr-xr-x 1 stewa 197609   0 Feb 24 18:57 ./
drwxr-xr-x 1 stewa 197609   0 Feb 24 17:16 ../
drwxr-xr-x 1 stewa 197609   0 Feb 24 18:58 .git/
-rw-r--r-- 1 stewa 197609   8 Feb 24 18:55 .gitignore
drwxr-xr-x 1 stewa 197609   0 Feb 24 18:57 analysis/
drwxr-xr-x 1 stewa 197609   0 Feb 24 18:57 data/
-rw-r--r-- 1 stewa 197609 594 Feb 24 18:36 README.md
-rw-r--r-- 1 stewa 197609  16 Feb 24 18:54 temp.temp

stewa@LAPTOP-58OP9CKK MINGW64 ~/MyStuff/git/git_basics (master)
```
## History update
```
   80  git status
   81  git add README.md README.md
   82  git diff --staged
   83  git commit -m "log params & head note"
   84  nano .gitignore
   85  git status
   86  git add .gitignore
   87  git commit -m "add gitignore file"
   88  nano .gitignore
   89  nano temp.temp
   90  git status
   91  nano .gitignore
   92  git status
   93  touch data/.gitkeep analysis/.gitkeep
   94  mkdir data
   95  mkdir analysis
   96  touch data/.gitkeep analysis/.gitkeep
   97  git status
   98  git add .
   99  git commit -m"ignore .temp file and add folders"
  100  ls -alh
  101  history
```
## github or bitbucket
`bitbucket` - unlimited private repositories, limited usage overall.  
`github` - unlimited public repositories, main usage overall.

## git remote
### History update
```
  102  ls
  103  git remote add origin https://github.com/stewartk66/git_basics.git
  104  git remote -v
  105  git push origin master
```
## git push and pull
If `git push` hits a conflict then `git pull` will pull all the information into the workspace almost like it pulls in the origin version and combines with local to create a new version with the full history and both sets of changes.  
Once the conflict is _fixed_ then fixing the conflict results in a new version with the history as it is in `origin` so it is then good to commit 
as the history is intact with a new version of the file as the HEAD.