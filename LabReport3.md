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

Source: (https://www.computerhope.com/unix/ufind.htm)
 
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
In this example, I used the `-path` command option to limit the find command to finding files which contain this path.
