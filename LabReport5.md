CSE 15L Lab Report 5
---

## Part 1: Debugging Scenario

### Student EDStem Post:
**What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?**

I am using a Windows laptop, however for this assignement I am remotely connected to `ieng6` via `ssh`.

**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.**

I am working on my grade.sh script to grade a `list-examples` program. My script should be cloning the given URL into the directory `student-submission` then checking for the files existence then outputting a grade based on the results of the Junit tests. My script works dine the first time when I run it. However, anytime after that, it displays a bunch of errors as well as an incorrect grade. I am confused as what goes wrong and why does the script still produce a grade when something clearly went wrong. Find below some screenshots of the script and its output.

*Script:*

![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/5b7eb009-1c29-410a-99bc-70851e8fa1fc)

*1st Run (compile-error file):*

![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/2d88a82c-859e-4e97-bdc1-35c222dd1f62)

*2nd Run (corrected file)*

![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/4f36652c-c777-4249-a96c-4be07f287580)

**Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**

My current working directory is `list-example-grader` and it contains `TestListExamples.java` , `lib`, and `grade.sh`. I have only used the `vim` command prior to running the tests. The first test I ran was `bash grader.sh https://github.com/ucsd-cse15l-f22/list-methods-compile-error` . This test worked fine and returned all the expected results. The faliure-inducing input in this case would be `bash grader.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected` since I tested this right after. This returned some terminal error and then the wrong restults which mathced with that of the previous test. I actually ran the tests again and the problem continued.

### TA Response:

I recommend paying attention to the `student-submission` directory and the contents of `ListExamples.java` each time you run the script. Does the script successfully clone the file? Try using `cat`. 

### Student Response:

I ran the command `cat` on the `ListExamples.java` after running the successful file and got the following result;
```
[cs15lsp23pc@ieng6-201]:list-examples-grader:503$ cat ListExamples.java
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s)
      }
    }
    return result;
  }
```
This proves that the current `ListExamples.java` was the older with the missing `;`. From this I found out that the bug is the missing `rm -rf student-submission` in my script. Before the `ListExamples` file is not getting compiled and instead the grade script is using the first file. Since `student-submission` was not getting deleted, when I clone the file it attempts to create a new directory but fails since the old one is there already. This is the cause of the terminal error output. Since no new file was made, the script continues with the older file providing the other part of the output. As a result, I added `rm -rf student-submission` to my script ensuring that the file is successfully cloned and used each time.

### All Information;

**File Setup Before**

![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/173153a6-593c-46c3-acc4-b4a7365d5370)

**File Setup After**

![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/1bf1670c-d936-4249-9205-e8d604650a97)

**TestListExamples.java**
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.Arrays;
import java.util.List;

class IsMoon implements StringChecker {
  public boolean checkString(String s) {
    return s.equalsIgnoreCase("moon");
  }
}

public class TestListExamples {
  @Test(timeout = 500)
  public void testMergeRightEnd() {
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "a", "b", "c", "d");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testMergeLeftEnd() {
    List<String> left = Arrays.asList("a", "b", "z");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "a", "b", "d", "z");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testFilterSingle() {
    List<String> input = Arrays.asList("Moon", "MOO", "moo");
    List<String> expect = Arrays.asList("Moon");
    List<String> filtered = ListExamples.filter(input, new IsMoon());
    assertEquals(expect, filtered);
  }

  @Test(timeout = 500)
  public void testFilterMulti() {
    List<String> input = Arrays.asList("Moon", "MOO", "moon", "MOON");
    List<String> expect = Arrays.asList("Moon", "moon", "MOON");
    List<String> filtered = ListExamples.filter(input, new IsMoon());
    assertEquals(expect, filtered);
  }
}
```
**grade.sh (Before)**
```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

git clone $1 student-submission
echo 'Finished cloning'

if [[ -f student-submission/ListExamples.java ]]
then
  echo 'ListExamples.java found'
else
  echo 'ListExamples.java not found'
  echo 'Score: 0/4'
fi

cp student-submission/ListExamples.java ./

javac -cp $CPATH *.java

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > junit-output.txt

FAILURES=`grep -c FAILURES!!! junit-output.txt`

if [[ $FAILURES -eq 0 ]]
then
  echo 'All tests passed'
  echo '4/4'
else

  RESULT_LINE=`grep "Tests run:" junit-output.txt`
  COUNT=${RESULT_LINE:25:1}

  echo "JUnit output was:"
  cat junit-output.txt
  echo ""
  echo "--------------"
  echo "| Score: $COUNT/4 |"
  echo "--------------"
  echo ""
fi
```
**Commands Run**
`bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-compile-error`
`bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected`

To fix the bug the line `rm -rf student-submission` was added. 

**grade.sh (After)**
```
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
git clone $1 student-submission
echo 'Finished cloning'

if [[ -f student-submission/ListExamples.java ]]
then
  echo 'ListExamples.java found'
else
  echo 'ListExamples.java not found'
  echo 'Score: 0/4'
fi

cp student-submission/ListExamples.java ./

javac -cp $CPATH *.java

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > junit-output.txt

FAILURES=`grep -c FAILURES!!! junit-output.txt`

if [[ $FAILURES -eq 0 ]]
then
  echo 'All tests passed'
  echo '4/4'
else

  RESULT_LINE=`grep "Tests run:" junit-output.txt`
  COUNT=${RESULT_LINE:25:1}

  echo "JUnit output was:"
  cat junit-output.txt
  echo ""
  echo "--------------"
  echo "| Score: $COUNT/4 |"
  echo "--------------"
  echo ""
fi
```

## Part 2: Reflection

Thankfully, I have learned a lot from during this course. Before taking this course I had no prior experience to using bash, webservers, scripts, vim or any of the other topics covered. I am now able to use these tools and platforms for my own use and for future academics. Another big and helpful topic that I learned is GitHub. With the information I learned, I have already begun using it for my own projects and for research. GitHub alone is such a powerful resource that can prove helpful at all levels. Pair this knowledge with all the other topics and I will am leaving this course with many new tools and resources.






