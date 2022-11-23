# Lab Report 5
### Grade.sh Code Block
```
# Create your grading script here

CP=".;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar"
set -e

rm -rf student-submission
git clone $1 student-submission
cp TestListExamples.java student-submission/
cp -r lib student-submission/

if [[ -e student-submission/ListExamples.java ]]
then
    echo "Correct file submitted"
else
    echo "Wrong file submittied"
    exit
fi

cd student-submission/
echo "In student-submission"

javac -cp $CP *.java 2> compiler_output.txt

# Checking if there are any compiling errors
if [[ $? -eq "0" ]]
then
    echo "Code Compiled"	
else
	echo "ERROR COMPILING! See error message below for more details"
	cat compiler_output.txt
	exit
fi

echo "Starting Tests"
java -cp $CP org.junit.runner.JUnitCore TestListExamples > testResults.txt
echo "Finished Tests"

awk -F\. '{print NF-1}' testResults.txt > temp.txt
NUMTOTAL=$(sed -e '1d;3,$d' temp.txt)
awk -F\E '{print NF-1}' testResults.txt > temp.txt
NUMFAIL=$(sed -e '1d;3,$d' temp.txt)
awk -F '[: ]' 'index($1, "test") {print $1}' temp.txt > testsFailed.txt

NUMPASS=$(($NUMTOTAL - $NUMFAIL))

echo "You have passed $NUMPASS out of $NUMTOTAL test."
echo "You achieved the score of $NUMPASS/$NUMTOTAL."
```
<br/>
### Grading https://github.com/ucsd-cse15l-f22/list-methods-lab3

![grading first](https://user-images.githubusercontent.com/114313685/203482854-568a021a-3f8f-4526-9119-748733ce92ce.PNG) <br/>

### Grading https://github.com/ucsd-cse15l-f22/list-methods-corrected

![grading second](https://user-images.githubusercontent.com/114313685/203482166-74508382-a141-4db2-9f72-f36e12eb5f39.PNG) <br/>

### Grading https://github.com/ucsd-cse15l-f22/list-methods-compile-error

![grading third](https://user-images.githubusercontent.com/114313685/203482607-422b91eb-180b-438a-bda2-864b702c8ce8.PNG) <br/>

### Tracing The Second Grading

The bash script first removes any folder named student-submission and then it git clones <br/>
the inputted url and names it student-submission. It will then copy over the TestListExamples.java <br/>
and the JUnit library folder to the student-submission folder. Then it will check if the <br/>
the ListExamples.java file exists in the student-submission folder. If it does, it will print <br/>
out that the correct file is submitted and if it does not exist, it will say wrong file submitted <br/>
The script will then move the directory over to the student-submission folder and say that <br/>
it is in the student-submission folder. It will then compile all java files in the folder and <br/>
put the stderr into a file called compiler_output.txt. For this submission, there will be no stderr <br/>
in the compiler_output.txt file. If there are no stderr, it will say that the code compiled and if <br/>
there is a stderr, it will say there is a compile error and printout the error. After this, the <br/>
the script will say starting tests and starts running the TestListExamples.java file on the <br/>
student-submission. Once it is done testing, it will say finished tests. Finally, the script <br/>
will count the total amount of tests, the number of tests that failed, and the number of tests that <br/>
passed. It well then print out the number of the test passed out of the total number of tests and <br/>
give the score of the submission.





