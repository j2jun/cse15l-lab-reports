# Week 5 Lab Report – Researching Command

## **“find”** command locates or searches the files or directories.

Assume all code is in *./technical* working directory.

---

1. find *-name* option

**Example 1.1**
```
$ find . -name Annual_Fee.txt
```

Output:
```
./government/Media/Annual_Fee.txt
```

The command above searches for the name *“Annual_Fee.txt”* in the working directory.

Also, this command can search for multiple files. This is very useful in finding files with similar names. Let’s say you have categorized files by certain pattern, then you can use this command and write **“*”** to find all the files with similar pattern. (See the code below)

**Example 1.2**
```
$ find ./biomed -name 1471-2148-2-*.txt
```
Output:
```
./biomed/1471-2148-2-12.txt
./biomed/1471-2148-2-14.txt
./biomed/1471-2148-2-15.txt
./biomed/1471-2148-2-17.txt
./biomed/1471-2148-2-2.txt
./biomed/1471-2148-2-5.txt
./biomed/1471-2148-2-7.txt
./biomed/1471-2148-2-8.txt
```

Sometimes, instead of a file, you want to find a folder. You can use *find -name* to locate where the folder that is saved. (See the code below)

**Example 1.3**
```
$ find . -name Media
```
Output:
```
./government/Media
```

---
2.	find *-type* option

•	find -type **f** -name

If you want to look for files that have empty content, you can use this command below. This is useful when you want to delete any unnecessary files. (See the code below)

**Example 2.1**
```
$ find . -type f -empty
```
Output: 
```
./government/Media/Anthem_Payout.txt
./government/Media/Assuring_Underprivileged.txt
./government/Media/Avoids_Budget_Cut.txt
./government/Media/Barnes_Volunteers.txt
./government/Media/Barnes_new_job.txt
./government/Media/Barnes_pro_bono.txt
./government/Media/Barr_sharpening_ax.txt
./government/Media/BergenCountyRecord.txt
./government/Media/Bias_on_the_Job.txt
./government/Media/Boone_legal_service.txt
…… (There are more files)
```

Like find -name option, you can also find files using this command. (See the code below)

**Example 2.2**
```
$ find . -type -name chapter*.txt
```
Output:
```
./911report/chapter-1.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
./911report/chapter-12.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-2.txt
./911report/chapter-3.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-8.txt
./911report/chapter-9.txt
```

•	find -type **d**

Now, let’s say you want to look for all directories inside the working directory, use the code below.

**Example 2.3**
```
$ find . -type d
```
Output:
```
.
./911report
./biomed
./government
./government/About_LSC
./government/Alcohol_Problems
./government/Env_Prot_Agen
./government/Gen_Account_Office
./government/Media
```

Finding all directories help you to know what is in the folder.

---

3.	Find *-size* option

You can find files based on size. There are following suffices to specify the file size:

*	**b:** 512-byte blocks (default)
*	**c:** bytes
*	**w:** two-byte words
*	**k:** Kilobytes
*	**M:** Megabytes
*	**G:** Gigabytes

Let’s say you want to find exactly *5 Kilobytes* inside a */government* directory. (See code below)

**Example 3.1**
```
$ find ./government -type f -size 5k
```
Output:
```
./government/Gen_Account_Office/d01121g.txt
./government/Media/Annual_Fee.txt
```

Also, you can search files that are greater or less than specified size.

Here, you can search files greater than *1MB* inside */technical* directory. Make sure to write **“+”** symbol before the size value. (See code below)

**Example 3.2**
```
$ find . -type f -size +1M
```
Output:
```
```

You will get no result because there are no files with greater than *1 Megabytes*. If you want to find files with less than a certain value, then use **“-”** symbol before the size value.

You can also search files within a size range. Let’s say in */biomed* directory, you want to find all files between *1 byte* and *1 Megabytes*. (See below code)

**Example 3.3**
```
$ find ./biomed -type f -size +1c -size 1M
```
Output:
```
./biomed/1468-6708-3-1.txt
./biomed/1468-6708-3-10.txt
./biomed/1468-6708-3-3.txt
./biomed/1468-6708-3-4.txt
…
./biomed/rr196.txt
./biomed/rr37.txt
./biomed/rr73.txt
./biomed/rr74.txt
```

Using a file size to find files can be useful when you want to delete a file that takes up too much space.

---

There are many more useful options to find files or directories. The best recommendation is searching *"command-line find options"* in Google.
