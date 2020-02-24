# Git Basics 24/02/2020

- `init` : make current folder a git repository
- `status` : see the status of current repository
- `add` : put files into the index
- `commit` : add changes to master
- commit has a -m property to allow addition of message, 
if excluded then git commit opens the editor

- `diff` : changes between 2 commits
- `log` : list history 

log --oneline
log --oneline --graph -- decorate

checkout <hash> file : restore a file
checkout <hash> : restore the entire folder 


index/staging area has files ot be committed
HEAD where you are in the history 

remote : anywahere you didn't `init`
  - remote add origin <url> : adds url as remoate named origin
  - remote -v to verify - fetch and pull 
- `push` : send code to remote
- pull: get code from remoate
