Lab Report 3
--- 
Throughout the lectures and labs we have used multiple commands in bash to assist us in navigating directories and managing our files. In this lab report I will be looking at more command line options that can be used with the `find` command to further assist us. The `find` command alone can be useful but both too specific and broad. 
  
### The `-iname`  Option:
This command is very similar to the `-name` command which has been disscused in lab and lecture. However, unlike the `-name` command the `-iname` is not case-sensitive. This means that you can search for a particular file when you are not sure of the cases of each letter. 

**Example 1;**

```
$ find ./technical/* -iname "*eES*"
./technical/government/Media/Higher_Registration_Fees.txt
./technical/government/Media/water_fees.txt
```
In this example, I use the `find` command to look through all files of `./technical` and check for `-iname` file names containing "eES" in the name. At first glance, it would seem rather odd to have this letter combonation. However, the `-iname` is case-insensitive meaning it just looks for those letters disregarding their case. This provides a broader search which is helpful. 

**Example 2;** 
