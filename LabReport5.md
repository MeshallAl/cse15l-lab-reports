CSE 15L Lab Report 5
---

## Part 1: Debugging Scenario

### Student EDStem Post:
**What environment are you using (computer, operating system, web browser, terminal/editor, and so on)?**

I am using a Windows laptop, however for this assignement I am remotely connected to ieng6 via ssh.

**Detail the symptom you're seeing. Be specific; include both what you're seeing and what you expected to see instead. Screenshots are great, copy-pasted terminal output is also great. Avoid saying “it doesn't work”.**

I am working on my grade.sh script to grade a "list-examples" program. My script should be cloning the given URL into the directory student-submission then checking for the files existence then outputting a grade based on the results of the Junit tests. My script works dine the first time when I run it. However, anytime after that, it displays a bunch of errors as well as an incorrect grade. I am confused as what goes wrong and why does the script still produce a grade when something clearly went wrong. Find below some screenshots of the script and its output.

*Script:*

![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/5b7eb009-1c29-410a-99bc-70851e8fa1fc)

*1st Run (compile-error file):*

![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/2d88a82c-859e-4e97-bdc1-35c222dd1f62)

*2nd Run (corrected file)*

![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/4f36652c-c777-4249-a96c-4be07f287580)

**Detail the failure-inducing input and context. That might mean any or all of the command you're running, a test case, command-line arguments, working directory, even the last few commands you ran. Do your best to provide as much context as you can.**

My current working directory is "list-example-grader" and it contains "TestListExamples.java" , "lib", and "grade.sh". I have only used the "vim" command prior to running the tests. The first test I ran was "bash grader.sh https://github.com/ucsd-cse15l-f22/list-methods-compile-error" . This test worked fine and returned all the expected results. The faliure-inducing input in this case would be "bash grader.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected" since I tested this right after. This returned some terminal error and then the wrong restults which mathced with that of the previous test. I actually ran the tests again and the problem continued.

### TA Response:

I recommend paying attention to the "student-submission" directory and the contents of "ListExamples.java" each time you run the script. Does the script successfully clone the file? Try using "cat" 

### Student Response:



