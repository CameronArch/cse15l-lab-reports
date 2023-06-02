# Lab Report 5 - Debugging Scenario

## Student Debugging Post

**1) Environment:** 
Operating system = Windows 11, Editor = Visual Studio Code, Terminal = Git Bash in VS Code

**2) Symptom:** 
![Image](StudentBug.png) 
``` 
Camer@Cameron-Laptop MINGW64 ~/OneDrive/Documents/GitHub/list-examples-grader (main)
$ bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected
Cloning into 'student-submission'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
Finished cloning
There was 1 failure: FAILURES!!! Tests run: 1, Failures: 1
```
Expected: All tests should pass on the `https://github.com/ucsd-cse15l-f22/list-methods-corrected` student submission because it is the correct implementation of `ListExamples`. The tests should fail the `https://github.com/ucsd-cse15l-f22/list-methods-lab3` student submission because it is an incorrect implementation of `ListExamples`.

Actual: Both `https://github.com/ucsd-cse15l-f22/list-methods-corrected` and `https://github.com/ucsd-cse15l-f22/list-methods-lab3` student submissions fail the tests for `ListExamples`.

**3) Failure-Inducing Input and Context:** 
Failure-inducing input: `https://github.com/ucsd-cse15l-f22/list-methods-corrected`

The commands used: `bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected` and `bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-lab3`

Working Directory: `list-examples-grader`

Last commands ran: None, this is a new terminal

`TestListExamples.java` is unchanged compared to given file.

 `grade.sh` Script: 
 ```
 CPATH='.;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission
echo 'Finished cloning'


# Draw a picture/take notes on the directory structure that's set up after
# getting to this point

# Then, add here code to compile and run, and do any post-processing of the
# tests

file=`find student-submission/ListExamples.java`

if [[ (! -f $file) ]]
then 
echo "Not correct file submitted"
exit 1 
fi


cp -r $file grading-area
cp -r lib grading-area


cd grading-area

javac -cp $CPATH *.java 2> CompileError.txt

if [[ ($? -ne 0) ]]
then
cat CompileError.txt
exit 1
fi


java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > results.txt

grep -i "OK" results.txt > success.txt
grep -i "Failure" results.txt > failure.txt


echo `cat failure.txt`


echo `cat success.txt`
```

## TA Response

First, run `bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected`. Then, show what is contained in result.txt with `cat grading-area/result.txt`. Fianlly, send a screenshot of the terminal output or a copy of the output.

## Student Reply

![Image](StudentBug2.png)
```
Camer@Cameron-Laptop MINGW64 ~/OneDrive/Documents/GitHub/list-examples-grader (main)
$ bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected
Cloning into 'student-submission'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.

Camer@Cameron-Laptop MINGW64 ~/OneDrive/Documents/GitHub/list-examples-grader (main)
$ cat grading-area/results.txt
JUnit version 4.13.2
.E
Time: 0.008
There was 1 failure:
1) initializationError(org.junit.runner.JUnitCommandLineParseResult)
java.lang.IllegalArgumentException: Could not find class [TestListExamples]
        at org.junit.runner.JUnitCommandLineParseResult.parseParameters(JUnitCommandLineParseResult.java:100)
        at org.junit.runner.JUnitCommandLineParseResult.parseArgs(JUnitCommandLineParseResult.java:50)
        at org.junit.runner.JUnitCommandLineParseResult.parse(JUnitCommandLineParseResult.java:44)
        at org.junit.runner.JUnitCore.runMain(JUnitCore.java:72)
        at org.junit.runner.JUnitCore.main(JUnitCore.java:36)
Caused by: java.lang.ClassNotFoundException: TestListExamples
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:641)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:188)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:520)
        at java.base/java.lang.Class.forName0(Native Method)
        at java.base/java.lang.Class.forName(Class.java:467)
        at org.junit.internal.Classes.getClass(Classes.java:42)
        at org.junit.internal.Classes.getClass(Classes.java:27)
        at org.junit.runner.JUnitCommandLineParseResult.parseParameters(JUnitCommandLineParseResult.java:98)
        ... 4 more

FAILURES!!!
Tests run: 1,  Failures: 1
```

## TA Response - Solution

It appears that the file `TestListExamples.java` is within the `grading-area` directory. This means there are not any tests being ran on the student submission of `ListExamples.java`. The bug is that `TestListExamples.java` does not exist in the `grading-area` directory where the student submission is contained, so there is not a file for testing the submission.

Solution: In your `grade.sh` script, you need to copy `TestListExamples.java` into `grading-area` as well which should fix the bug.

## Student Reply - Bug Fixed

Thank you! It is woring as expected now.

![Image](StudentFIx.png)




