CSE 15L Lab Report 4
---

### Logging In:
![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/6c389e20-774b-4559-8c7c-fbda3eaf9575)

**Keys Pressed:**
`ssh cs15lsp23pc@ieng6.ucsd.edu`
`<enter>`

The first task I did was logging into my `ieng6` account via `ssh`. As a result, I typed in `ssh` followed by my account username. Due to the creation of the ssh keys, I was not prompted to input my password. 

### Cloning the Repository:
![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/bd5e36f0-12e7-4f65-9c65-c05f64aaf6da)

**Keys Pressed:**
`git clone`
`<shift + insert>`
`<enter>`

In the second step, I cloned the repository into my account. To do this I used the `git clone` command and then pasted the `ssh link` from my clipboard into the terminal using `shift + insert`. 

### Running Failed Tests:
![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/77cb3abe-0210-4322-8a17-f5a9cf33a16f)

**Keys Pressed:**
`cd l` `<tab>`
`<enter>`
`bash t` `<tab>`

In this step, I first change my directory to `lab7` by writing `cd l` and finishing it off by pressing  `<tab>`. In the directory I compiled the code by running the `test.sh` script using `bash t` followed by `<tab>` to fill in the rest.

### Fixing the Code:
![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/67e04307-d7bc-4d60-b42c-5321b3593bc2)

**Keys Pressed:**
`vim l <tab> . <tab>` `<enter>`
`e` `r` `2`
`:wq` `<enter>`

In this step, I opened up the file using the command `vim` with the file name. Similar to last time, I only inputed a few characters and used `<tab>` to fil in the rest. Once vim opened, the cursor was at the beginning of the word "index1" at the line that needed to be fixed. I used `e` to move the cursor to the last character of "index1". There I used the `r` command followed by "2" to replace the "1" into "2". Once the file has been fixed, I used `:wq` to save and exit the file.

### Running Fixed File:
![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/fc64d41d-8afc-452a-ba3c-367baf4d5494)

**Keys Pressed:**
`<up><up> <enter>`

Simlar to a previous step, I iterate through my recent terminal commands to find the `bash test.sh` command which was used to run the failed tests. In this case, the command was two iterations back.

### Commit and Push:
![image](https://github.com/MeshallAl/cse15l-lab-reports/assets/130005669/4fd2bc13-56df-4a7f-aa2a-f32916ab1ab7)

**Keys Pressed:**
`git add L` `<tab>` `.` `<tab>`
`<enter>`
`git commit L` `<tab>` `-m "fixed"`
`<enter>`
`git push origin main`

In this step I used a sequence of `git` commands to add, commit then push the fixed file. I used  `git add` to add the file to the list of files to be commited. I then used `git commit` with `-m` to commit the files with a message. Finally, I used  `git push origin main` to push the fixed file. Throught this process I also used several `<tab>` shortcuts. 
