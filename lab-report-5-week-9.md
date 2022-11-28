# Lab Report 5 – Grade Server

## Code Block: ```grade.sh```

```
 1  CPATH=.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar 
 2  GRADE=2
 3  ERROR=0
 4 
 5  rm -rf student-submission
 6  git clone $1 student-submission
 7 
 8  if [ -e student-submission/ListExamples.java ]
 9  then
10     echo "File submitted correctly."
11  else 
12     echo " File submitted incorrectly."
13     exit 1
14  fi
15 
16  cp student-submission/ListExamples.java ./
17 
18  javac -cp $CPATH *.java
19  if [ $? -ne 0 ]
20  then 
21     echo "Compile error!"
22     exit 1
23  fi
24
25  java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > out.txt
26
27  if [ $? -eq 0 ]
28  then 
29     echo -e "All tests passed.\nGrade: $GRADE/2"
30     exit 0
31  fi
32
33  if [ $(grep -c "filter" out.txt) -ne 0 ]
34  then
35     let ERROR+=1
36     echo "Test filter failed."
37  fi
38  if [ $(grep -c "merge" out.txt) -ne 0 ]
39  then
40     let ERROR+=1
41     echo "Test merge failed."
42  fi
43
44  let GRADE-=ERROR
45  echo "Grade: $GRADE/2"
```

## Screenshots of Student Submissions

1. https://github.com/ucsd-cse15l-f22/list-methods-compile-error

![Student_Submission_1](https://user-images.githubusercontent.com/54129361/204195313-e3725c56-4771-43fe-bb77-ffd270f67c44.png)

2. https://github.com/ucsd-cse15l-f22/list-methods-signature

![Student_Submission_2](https://user-images.githubusercontent.com/54129361/204195436-ce3a54d9-150f-46d1-b348-952782ffc396.png)

3. https://github.com/ucsd-cse15l-f22/list-methods-nested

![Student_Submission_3](https://user-images.githubusercontent.com/54129361/204195498-720ed5bf-76b6-4fba-83a0-96a2dedb6112.png)

---
## Trace ```grade.sh``` for Example 2 Student Submission

Link: https://github.com/ucsd-cse15l-f22/list-methods-signature

**Lines**
 1  CPATH=.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar 
 2  GRADE=2
 3  ERROR=0
 1-3 Assigns variables
* Standard Output: [empty]
* Standard Error: [empty]
* Return Code: 0

 4  rm -rf student-submission
 Deletes all files and directories in student-submission
* Standard Output: [empty]
* Standard Error: [empty]
* Return Code: 0

 6  git clone $1 student-submission
* Standard Output: [empty]
* Standard Error: ```Cloning into 'student-submission'...```
* Return Code: 0

 8  if [ -e student-submission/ListExamples.java ]
 9  then
10     echo "File submitted correctly."
11  else 
12     echo " File submitted incorrectly."
13     exit 1
14  fi
This condition is true because ListExamples.java exists in student-submission directory.

16  cp student-submission/ListExamples.java ./
* Standard Output: [empty]
* Standard Error: [empty]
* Return Code: 0

18  javac -cp $CPATH *.java
* Standard Output: [empty]
* Standard Error: [empty]
* Return Code: 0

19  if [ $? -ne 0 ]
20  then 
21     echo "Compile error!"
22     exit 1
23  fi
This condition is false because line 18's return code is 0.

25  java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > out.txt
* Standard Output:
```
[JUnit version 4.13.2
...
Tests run: 2, Failures: 0
```
* Standard Error: [empty]
* Return Code: 0

27  if [ $? -eq 0 ]
28  then 
29     echo -e "All tests passed.\nGrade: $GRADE/2"
30     exit 0
31  fi
This condition is true because line 25's return code is 0. Therefore, it prints out:
```
All tests passed.
Grade: 2/2
```

33  if [ $(grep -c "filter" out.txt) -ne 0 ]
34  then
35     let ERROR+=1
36     echo "Test filter failed."
37  fi
This condition is false.

38  if [ $(grep -c "merge" out.txt) -ne 0 ]
39  then
40     let ERROR+=1
41     echo "Test merge failed."
42  fi
This condition is false.

44  let GRADE-=ERROR
* Standard Output: [empty]
* Standard Error: [empty]
* Return Code: 0

45  echo "Grade: $GRADE/2"
* Standard Output: ```Grade: 2/2```
* Standard Error: [empty]
* Return Code: 0
