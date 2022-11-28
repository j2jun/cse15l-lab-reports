# Lab Report 5 – Grade Server

## Code Block: ```grade.sh```

```
# Create your grading script here

CPATH= .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar 
GRADE=2
ERROR=0

rm -rf student-submission
git clone $1 student-submission

if [ -e student-submission/ListExamples.java ]
then
    echo "File submitted correctly."
else 
    echo " File submitted incorrectly."
    exit 1
fi

cp student-submission/ListExamples.java ./

javac -cp $CPATH *.java
if [ $? -ne 0 ]
then 
    echo "Compile error!"
    exit 1
fi

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > out.txt

if [ $? -eq 0 ]
then 
    echo -e "All tests passed.\nGrade: $GRADE/2"
    exit 0
fi

if [ $(grep -c "filter" out.txt) -ne 0 ]
then
    let ERROR+=1
    echo "Test filter failed."
fi
if [ $(grep -c "merge" out.txt) -ne 0 ]
then
    let ERROR+=1
    echo "Test merge failed."
fi

let GRADE-=ERROR
echo "Grade: $GRADE/2"
```

## Screenshots of Student Submissions

1. https://github.com/ucsd-cse15l-f22/list-methods-compile-error

![Student_Submission_1](https://user-images.githubusercontent.com/54129361/204195313-e3725c56-4771-43fe-bb77-ffd270f67c44.png)

2. https://github.com/ucsd-cse15l-f22/list-methods-signature

![Student_Submission_2](https://user-images.githubusercontent.com/54129361/204195436-ce3a54d9-150f-46d1-b348-952782ffc396.png)

3. https://github.com/ucsd-cse15l-f22/list-methods-nested

![Student_Submission_3](https://user-images.githubusercontent.com/54129361/204195498-720ed5bf-76b6-4fba-83a0-96a2dedb6112.png)


