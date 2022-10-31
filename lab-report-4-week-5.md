# Week 5 Lab Report – Researching Command

## **“find”** Command locates or searches the files or directories.

**Assume all working directory is *.technical/* .**
1. find -name option
You can find files based on size. There are following suffices to specify the file size:
**Example 1.1**
'''
$ find . -name Annual_Fee.txt
'''
Output:
'''
./government/Media/Annual_Fee.txt
'''
The command above searches for the name “Annual_Fee.txt” in the working directory.

Also, this command can search for multiple files. This is very useful in finding files with similar names. Let’s say you have categorized files by certain pattern, then you can use this command and write “*” to find all the files with similar pattern. (See the code below)
