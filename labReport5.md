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

