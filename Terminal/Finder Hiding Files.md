#shell 
#### To show hidding files in the Finder run the following command in terminal 

```shell
$ defaults write com.apple.Finder AppleShowAllFiles true 
$ [Enter]
$ killall Finder
```

To hidde this .files put `false` instead of true

#### To show .gitignore File from Terminal
==Retrieve File path==
```shell
$ pwd
```

==Unhidde File==
```shell
$ ls -al <path/to/dir>
```

Output
```shell
total 24
drwxr-xr-x 9 IsabelleL staff 288 Jan 24 12:52 .
drwxr-xr-x 37 IsabelleL staff 1184 Dec 15 16:38 ..
drwxr-xr-x 15 IsabelleL staff 480 Jan 24 17:43 .git
-rw-r--r-- 1 IsabelleL staff 13 Apr 10 2021 .gitignore
drwxr-xr-x 16 IsabelleL staff 512 Oct 20 14:47 .obsidian
drwxr-xr-x 3 IsabelleL staff 96 Apr 11 2021 Git
-rw-r--r--@ 1 IsabelleL staff 1072 Apr 10 2021 LICENSE
-rw-r--r-- 1 IsabelleL staff 239 Apr 11 2021 README.md
drwxr-xr-x 7 IsabelleL staff 224 Jan 24 17:33 Terminal
```

==Open .gitignore file in terminal==
```shell
$ nano .gitignore
```

Or in text editor
```shell
$ open .gitignore
```