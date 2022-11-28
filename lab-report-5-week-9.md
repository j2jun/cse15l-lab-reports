# Lab Report 5 – Grade Server

## Code Block: ```grade.sh```

```
# Create your grading script here
#set -e

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
