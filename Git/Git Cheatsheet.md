### Git Clone a Repo into a new directory

```shell
$ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
```

### Git Init a Repo

Create an empty Git repository or reinitialize an existing one
```shell
$ git init
$ git add <file>
$ git commit -m "A meaningfull first commit message"
```

💡 ==Good tips==
```md  
hint: of your new repositories, which will suppress this warning, call:

hint: git config --global init.defaultBranch <name>

hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and

hint: 'development'. The just-created branch can be renamed via this command:

hint: git branch -m <name>
```


#### Push to an existing Repository from the command line

```shell
$ git remote add origin git@github.com:Isalafont/CheatSheet.git
$ git branch -M main
$ git push -u origin main
```

---
## Working with branches

#### List the branch

```shell
$ git branch
```

#### Create a branch 

```shell
$ git branch <name of feature branch>
# or 
$ git check out -b <name of feature branch>
# or
$ gco -b <name of feature branch>
```

#### Rename a branch 
In the branch you want to rename
```bash
$ git branch -M <new name branch>
````

#### Change Branch
```shell
$ git check out <name of feature branch>
# or
$ gco <name of feature branch
# or 
$ git switch <name of branch>
```

#### Delete a branch 

```shell
$ git branch -D <name of the branch>
```

Delete all the branch pushed and merged 

```shell
$ git sweep
```

---
## Saving your work

###### Checking Status 

```shell
$ git status
# or 
$ gst
```

Add new files you've just created.

```shell
$ git add <file>
$ git commit -m "meaningfull commit message"
# or
$ gcmsg "meaningfull commit message"
```

Adding all the files
```shell
$ git add .
# or
$ gaa
```

##### Choose only the files you want to commit and stages / stash the other ones 

*It will review all the files you have modified and you could choose to commit then or to stash them.*

```shell
$ git add -p
```

#### Stash your files 
```shell
$ git stash
```

Save a stash file with a name
```shell
$ git stash save <name>
```

List all the stash file
```shell
$ git stash list
```
Show the stash
```shell
$ git stash show [-u|--include-untracked|--only-untracked] [<diff-options>] [<stash>]
```

Drop the stash 
```shell
$ git stash drop [-q|--quiet] [<stash>]
```

Pop the stash
```shell
	$ git stash (pop | apply) [--index] [-q|--quiet] [<stash>]
```

Other commands 
```shell
$ git stash_ branch <branchname> [<stash>]
$ git stash_ [push [-p|--patch] [-S|--staged] [-k|--[no-]keep-index] [-q|--quiet]
	     [-u|--include-untracked] [-a|--all] [-m|--message <message>]
	     [--pathspec-from-file=<file> [--pathspec-file-nul]]
	     [--] [<pathspec>…​]]
$ git stash_ clear
$ git stash_ create [<message>]
$ git stash_ store [-m|--message <message>] [-q|--quiet] <commit>
```

---
### Pull working branch 

From you main or develop branch 
First pull the last version of your main branch 

```shell
$ git pull origin main
# or 
$ git fetch origin main 
$ git merge
```

---

### Push working branch Process 

#### Push Feature branch 
```shell
$ git push <remote> <name of feature branch>
```

*example : *
```shell
$ git push origin feat/recsys-design
```

###### If current branch is behind remote branch
```shell
$ git pull <remote> <name of feature branch>
```

---

### Set up tracking information for a branch

```bash
$ git branch --set-upstream-to=origin/<branch> <name of feature branch>
```

example :

_git branch -- set-upstream-to=origin/develop feat/recsys\_design_

### Once branch working on tree clean

```bash
$ git push <remote> <name of feature branch>
```

example :

_git push origin feat/recsys\_design_

---

### Fetch Branch from a Working Partner

```shell
$ gco -b <workin partner branch> origin<working partner branch>
```

*example: *
```shell
$ gco -b kjr/fix-recsys origin/kjr/fix-recsys
```
or 
```shell
$ git fetch origin
$ gco <name of the branch>
```

### Git merge develop branch into feature branch

```bash
$ gco <develop branch>
$ git pull origin <develop branch>
$ gco <feature branch>
$ git merge <develop branch>
$ git push origin <feature branch>
```

### Git Rebase master into feature branch

Pull last version of master on master branch 
```shell
$ gco master
$ git pull origin master
$ gco <feature branch>
$ git rebase master
$ git push --force-with-lease
```

#### Quand le Git Rebase merde
```shell
git checkout develop
git pull origin develop
git checkout -b API-2104/homepage-2
git cherry-pick SHA1 SHA2 ... SHAN
git branch -m API-2104/homepage API-2104/homepage-old
git branch -m API-2104/homepage-2 API-2104/homepage
git push --force-with-lease origin API-2104/homepage
```

## Cleaning a Branch
- go to the master branch
- delete branch we want to clean
- recreate the branch with the exact same name (from repository github)
- take the SHA number existing in the repository 
  ex : SHA *3ea5f639a1879507b08b2ee480020e3517676de0* and cherry-pick the commits
- git push --force origin the branch 

```shell
$ gco master
$ git branch -D <name of the branch>
$ gco -b <name of the branch>
$ git cherry-pick 7a298ce30b7f8def555ba6d69c88ec6044ab4561
$ git push --force origin <name of the branch>
```

---

### Checking the remotes

```shell
$ git remote
heroku
origin
```

```bash
$ git remote -v

origin git@github.com:Isalafont/Cheat-Sheets.git (fetch)
origin git@github.com:Isalafont/Cheat-Sheets.git (push)

```

#### Set a new remote
```bash
$ git remote add <my_awesome_remote_repo> git@github.com:Isalafont/Cheat-Sheets.git
```

#### Changing Remote name
```bash
$ git remote rename <old_name> <new_name>
```

#### Remove Remote name
```bash
$ git remote remove <name>
```

---

#### Show git history
```shell
$ git logs
```

#### Find and show all git history
Manage reflog information
```shell
$ git reflog
```

`git reflog show` accepts any of the options accepted by `git log`.

If you have delete some commits with the `git reset --hard HEAD 1`  command and want to find the deleted commit, use this command:  
```shell
$ git reflog
$ git sherry-pick {commit SHA}
```

--- 
### Retrieve last branch 

```shell
$ gco -   
```


### Delete a git repository 

```shell
$ rm -rf .git
```


### Git Prout

Si tu veux aussi faire git add ., git commit, git push, en 1 prout ajoute ça dans ta config git👇  
  
prout = "!f() { git add -A && git commit -m \"$@\" && git push origin master; }; f"  

--- 

### Helpful commands

```bash
$ git --help
```


### Changing a remote repository URL
[changing a remote repository](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories#changing-a-remote-repositorys-url)

