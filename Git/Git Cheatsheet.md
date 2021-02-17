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

### Git merge develop branch into feature branch

```bash
$ gco <develop branch>
$ git pull origin <develop branch>
$ gco <feature branch>
$ git merge <develop branch>
$ git push origin <feature branch>
```

---

### Checking the remotes

```shell
$ git remote
heroku
origin
```

---

### Delete a git repository 

```shell
$ rm -rf .git
```

--- 

### Helpful commands

```bash
$ git --help
```
