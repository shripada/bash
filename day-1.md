---
marp: true
theme:
paginate: true
---

<style >
:root{
    
    color: gray;
}
h1 {
  color: #004362;
}
h2 {
    color: #00739c;
}
h3 {
    color: #00b0de;
}



</style>

# **Introduction to bash**

### Automate your daily tasks in terminal

---

Printing your current working directory:

```
pwd

/Users/shripada

```

---

### navigating to home directory

Home directory has a shortcut: `~`

```
cd ~
```

---

### Current directory . parent directory ..

A `.` symbolises the current directory
A `..` symbolises the parent directory

```
cd .  # has no effect, you remain in current directory
cd .. # takes you to parent directory
cd ../../ # will take to you parent's parent i.e grandparent
```

---

## Clearing terminal window

```
clear # also Cntrl + K in windows, command + k in mac
```

---

## Viewing files and folders

The `ls` command is quite useful to do this.

```bash
ls      # lists the names of files and folders
ls -l   # gives more info about files and folders, such as user, group, and others permissions, date of creation etc
ls -la  # the additional a flag indicates that even hidden files and folders should be listed
```

## opening a file or folder

```bash
open .  # works in mac and linux and will open the current folder in Finder/Explorer
start . # works only in windows
```

---

## Creating Files

```bash
touch readme.md #creates a file with name readme.md in current folder
```

`echo` command can be used to log some message to console

```bash
> echo 'hello world of shells!'
hello world of shells!
```

We can also direct the output to a file using `>` to overwrite existing contents

```bash

echo 'echo is a console log of bash' > readme.md  # creates readme.md if it does not exist already
```

---

We can use cat command to read and display content of a file to the console

```bash
cat ./readme.md
```

If we want to append to the end of file, use `>>`

```bash
echo 'we can direct the stream of echo to another file' >> readme.md
```

---

## Creating a folder

```bash
mkdir my-images # creates my-images folder inside current folder
```

If we want to create a hierarchy of folders we need to pass `-p` option

```bash
mkdir -p a/b/c  # create a, b and then c. If we miss -p option then it will complain that intermidiate folders do not exist.
```

---

## Removing a file/folder

```bash
rm readme.md    # delete readme.md permanently
rm empty-folder # rm without any option can only delete empty folder
rm -r  folder # recursively delete folder and its contents
rm -rf folder # recursively delete by suppressing any errors / confirmations
```

---

## Copying files/folders

```bash
cp sourceFile  path/to/destination
# if destination is a folder file will be copied into it with same name `sourceFile`,
#otherwise the file will be copied to `to` folder with name `destination`
cp -R src/*  lib/*  # copies recursively everything from src to lib folder.
```

---

## Moving files/folders

```bash
mv aFile toFile # `aFile` will be renamed into `toFile`
mv aFile sub-folder/aFile  # moves aFile from current dir to sub-folder/aFile
mv aFile sub-folder/newFile # moves aFile from current dir to sub-folder with a different name 'newFile'
# if newFile is a directory, then aFile will be moved inside it.
mv a/*  b  # * is a wildcard char,  which selects all files/folders for moving
```

---

## Finding files and folders

We can use `find` command

```bash
find . -name 'shri*.png' # search png files that start with string shri in current directory
find . -iname 'shri*.png' # same as above but case insensitive
```

---

## Finding just folders with type option

```bash
find . -type d
find . -type d -name 'images'  # find all folders with name images recursively
```

---

We can pass `-delete` option to delete files found during the search.

```bash
find . -name '*.js' -delete # deletes all javascript files in current directory
```

---

# Executing a command on searches

`find` is quite versatile in that, we can even run some commands on the searches.
For example, let us say we have a folder hierarchy in current folder
and we want to move all png files present in this hierarchy into a folder called pngs in
current folder. We can do that using `-exec` flag

```bash
find . -iname '*.png' -exec mv {} ./pngs/ \; # {} represents each match.  \; is the end marker of the command.
```

---
