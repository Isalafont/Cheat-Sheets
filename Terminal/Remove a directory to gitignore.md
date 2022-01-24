**Create the .gitignore file** #gitignore

To create a .gitignore file, you can just `touch` the file which creates a blank file with the specified name. We want to create the file named .gitignore so we can use the command:

`touch .gitignore`

**Ignore the files**

Now you have to add the line which tells git to ignore the DS Store files to your .gitignore. You can use the nano editor to do this.

`nano .gitignore`

Nano is nice because it includes instructions on how to get out of it. (Ctrl-O to save, Ctrl-X to exit)

Copy and paste some of the ideas from this [Github gist](https://gist.github.com/octocat/9257657) which lists some common files to ignore. The most important ones, to answer this question, would be:

```
# OS generated files #
######################
.DS_Store
.DS_Store?
```

The # are comments, and will help you organize your file as it grows.

This [Github article](https://help.github.com/articles/ignoring-files/) also has some general ideas and guidelines.

**Remove the files already added to git**

Finally, you need to actually remove those DS Store files from your directory.

Use this great command from the top voted answer. This will go through all the folders in your directory, and remove those files from git.

`find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch`

**Push .gitignore up to Github**

Last step, you need to actually commit your .gitignore file.

`git status`

`git add .gitignore`

`git commit -m '.DS_Store banished!'`