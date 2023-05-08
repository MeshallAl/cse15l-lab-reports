Lab Report 3
--- 
Throughout the lectures and labs we have used multiple commands in bash to assist us in navigating directories and managing our files. In this lab report I will be looking at more command line options that can be used with the `find` command to further assist us. The `find` command alone can be useful but both too specific and broad. 
  
### The `-iname`  Option:
This command is very similar to the `-name` command which has been disscused in lab and lecture. However, unlike the `-name` command the `-iname` is not case-sensitive. This means that you can search for a particular file when you are not sure of the cases of each letter. 

**Example 1;**

```
stringSearch-data:322$ find ./technical/* -iname "*eES*"
./technical/government/Media/Higher_Registration_Fees.txt
./technical/government/Media/water_fees.txt
```
In this example, I use the `find` command to look through all files of `./technical` and check for `-iname` file names containing "eES" in the name. At first glance, it would seem rather odd to have this letter combonation. However, the `-iname` is case-insensitive meaning it just looks for those letters disregarding their case. This provides a broader search which is helpful. 

**Example 2;** 
```
stringSearch-data:322$ find ./technical/government/Env_Prot_Agen/* -iname "*.TXT"
./technical/government/Env_Prot_Agen/1-3_meth_901.txt
./technical/government/Env_Prot_Agen/atx1-6.txt
./technical/government/Env_Prot_Agen/bill.txt
./technical/government/Env_Prot_Agen/ctf1-6.txt
./technical/government/Env_Prot_Agen/ctf7-10.txt
./technical/government/Env_Prot_Agen/ctm4-10.txt
./technical/government/Env_Prot_Agen/final.txt
./technical/government/Env_Prot_Agen/jeffordslieberm.txt
./technical/government/Env_Prot_Agen/multi102902.txt
./technical/government/Env_Prot_Agen/nov1.txt
./technical/government/Env_Prot_Agen/ro_clear_skies_book.txt
./technical/government/Env_Prot_Agen/section-by-section_summary.txt
./technical/government/Env_Prot_Agen/tech_adden.txt
./technical/government/Env_Prot_Agen/tech_sectiong.txt
```
Very similar to the previous example, this command returns all the files with the given string. In this case I used an example that would usually never work to further demonstrate the case-insensitive nature of the command. The string ".TXT" does not exsit, yet the command gave us all the other case alternatives of it. If we were to run this with  `-name`, the command would return nothing all the time. 

Source: ([https://www.computerhope.com/unix/ufind.htm](https://www.computerhope.com/unix/ufind.htm))
 
### The `-path` Option:
This command option can be added to the `find` command to find all the files within the given path. Instead of searching for a for a specific file by name, you can use this command option to search for files with a specific path. This is helpful for deep directories or common names of directories within other directories.

**Example 1:**
```
stringsearch-data:349$ find -path "*/Env_Prot_Agen/*"
./technical/government/Env_Prot_Agen/1-3_meth_901.txt
./technical/government/Env_Prot_Agen/atx1-6.txt
./technical/government/Env_Prot_Agen/bill.txt
./technical/government/Env_Prot_Agen/ctf1-6.txt
./technical/government/Env_Prot_Agen/ctf7-10.txt
./technical/government/Env_Prot_Agen/ctm4-10.txt
./technical/government/Env_Prot_Agen/final.txt
./technical/government/Env_Prot_Agen/jeffordslieberm.txt
./technical/government/Env_Prot_Agen/multi102902.txt
./technical/government/Env_Prot_Agen/nov1.txt
./technical/government/Env_Prot_Agen/ro_clear_skies_book.txt
./technical/government/Env_Prot_Agen/section-by-section_summary.txt
./technical/government/Env_Prot_Agen/tech_adden.txt
./technical/government/Env_Prot_Agen/tech_sectiong.txt
```
In this example, I used the `-path` command option to limit the find command to finding files which contain this path "/Env_Prot_Agen/" . As a result, the command returned all the above files. This helps as I can find all the files which contain this path at some point. 

**Example 2:**
```
stringsearch-data:377$ find -path "*/technical/*/About_LSC/*"
./technical/government/About_LSC/CONFIG_STANDARDS.txt
./technical/government/About_LSC/Comments_on_semiannual.txt
./technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt
./technical/government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt
./technical/government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt
./technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt
./technical/government/About_LSC/ONTARIO_LEGAL_AID_SERIES.txt
./technical/government/About_LSC/Progress_report.txt
./technical/government/About_LSC/Protocol_Regarding_Access.txt
./technical/government/About_LSC/Special_report_to_congress.txt
./technical/government/About_LSC/State_Planning_Report.txt
./technical/government/About_LSC/State_Planning_Special_Report.txt
./technical/government/About_LSC/Strategic_report.txt
./technical/government/About_LSC/commission_report.txt
./technical/government/About_LSC/conference_highlights.txt
./technical/government/About_LSC/diversity_priorities.txt
./technical/government/About_LSC/reporting_system.txt
```
Similar to the previous example, I used the `-path` option to specify a certain path condition for `find`. In the example, I mentioned two directories with `*` inbetween. By doing this I could search for files in which I want to be incorportated in this unrestriced path. The files could be in two different folders, but as long as they share these path requirements they will be returned.

Source: ([https://www.computerhope.com/unix/ufind.htm](https://www.computerhope.com/unix/ufind.htm))

### The  `-type` Option:
This command option can limit the find command to find files with a specific type. In our current directory, there are not many different special file types. However, this command option can still be used and is very useful. 

**Example 1:**
```
stringsearch-data:381$ find "technical/" -type d
technical/
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos
```
In this example, I used the `-type` option with the `d` character to return all the directories located within `technical`. As a result, in the command line all the directories and their subdirectories are printed out with their paths. From this quick search I am able to see and locate any dirctory needed while having its path for quick access. 

**Example 2:**
```
stringsearch-data:405$ find "technical/government/Alcohol_Problems/" -type f
technical/government/Alcohol_Problems/DraftRecom-PDF.txt
technical/government/Alcohol_Problems/Session2-PDF.txt
technical/government/Alcohol_Problems/Session3-PDF.txt
technical/government/Alcohol_Problems/Session4-PDF.txt
```
In this example, I used the command option `-type` with the character `f` to return all the regular files within `technical/government/Alcohol_Problems/`. As a result, all the files in that directory were printed. If this directory had other files of different types they would not have been shown allowing you to efficient find specific files.

Source: ([https://www.computerhope.com/unix/ufind.htm](https://www.computerhope.com/unix/ufind.htm))

### The `-size` Option
This command option allows you to restrict the find command to have a certain criteria regarding the size of the files you want. Using this command you can specify if you would like files larger or smaller than a certain size allowing for more personalization in using the find command. Additionally it can be used to differeniate between empty or complete files with similar names and paths. It can also be used for storage analysis and management.

**Example 1:**
 ```
stringsearch-data:414$ find "technical/" -size +150k
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-3.txt
technical/government/About_LSC/commission_report.txt
technical/government/Env_Prot_Agen/bill.txt
technical/government/Env_Prot_Agen/multi102902.txt
technical/government/Env_Prot_Agen/tech_adden.txt
technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
technical/government/Gen_Account_Office/d01591sp.txt
technical/government/Gen_Account_Office/pe1019.txt
 ```
 In this example, I used the  `-size` option with `+150k` to restrict the output to only files with more than 150 Kilobytes. This option is very useful in finding files of a certain size. Since this size is quite large for a text file in this directory, not many results were outputed allowing us only to see what we specified.
 
 **Example 2:**
 ```
stringsearch-data:426$ find "technical/" -size -2k
technical/plos/pmed.0020191.txt
technical/plos/pmed.0020226.txt
 ```
 Unlike the previous example, I used the same option but with `-2k`. This made the `find` command find all the files in `technical` with less than 2 Kilobytes. Similarly, since this is quite a small size, the command only outputed a few files since all the other files were too large. This allows us to only see the files with the given size requirement.  
 
Source: ([https://www.computerhope.com/unix/ufind.htm](https://www.computerhope.com/unix/ufind.htm))

