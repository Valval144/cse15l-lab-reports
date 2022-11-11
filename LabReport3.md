# Week 5: Lab 3 #
## Find Command ##
---
## -name ##

- the name command finds files with a specified name

Ex. 1: `find .-name "preface.txt"`

```
owner@Owners-MacBook-Pro-2 technical % find . -name "preface.txt"
./911report/preface.txt
```
- -name searches within /technical and looks for files named "preface.txt" and returns it. In this case, it was found within ./technical/911report/(and then found inside)
- This is useful in cases where you want to find a file when there are many of them or when there are files with similar names. You can also use this command to quickly see if the file exists or belongs in the directory in the first place. 

Ex. 2: `find . -name "G*"`

```
owner@Owners-MacBook-Pro-2 technical % find . -name "G*"            
./government/Gen_Account_Office
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./government/Post_Rate_Comm/Gleiman_EMASpeech.txt
./government/Post_Rate_Comm/Gleiman_gca2000.txt
./government/Media/Good_guys_reward.txt
./government/Media/Ginny_Kilgore.txt
./government/Media/GreensburgDailyNews.txt
./government/Media/Greedy_Generous.txt
```
- This is very similar to using a regular name command but because of the "G*" it looks for files or directories within /technical that at least start with "G". For example I got things like "Gen", "Gleiman", and "Good"
- This is useful when you want to find files/directories that start with a certain letter, how many times they repeat, or when you are trying to find a file/directory with an unfamiliar name.

Ex.3: `find ./government/Post_Rate_Comm -iname "cOHeNetAl*"`
(*emphasis on -iname*)

```
owner@Owners-MacBook-Pro-2 technical % find ./government/Post_Rate_Comm -iname "cOHeNetAl*"
./government/Post_Rate_Comm/Cohenetal_CreamSkimming.txt
./government/Post_Rate_Comm/Cohenetal_DeliveryCost.txt
./government/Post_Rate_Comm/Cohenetal_Cost_Function.txt
./government/Post_Rate_Comm/Cohenetal_comparison.txt
./government/Post_Rate_Comm/Cohenetal_Scale.txt
./government/Post_Rate_Comm/Cohenetal_RuralDelivery.txt
```
- The -iname command is also similar to -name only that the "i" stands for insensitive so it "loosely" finds files/directories with the same name ignoring capitalizatoin. For example, I searched in "cOHeNetAl*" so this command ignored the random capitalization and found any files that started with "cohenetal" within ./government/Post_Rate_Comm.
- This is useful when trying to find files/directories and not have to worry about capitalization as much. Also, when trying to find if there is a capitalization error in any files/directories that shouldn't have them.
---
## -type ##
- the type command finds things based on the specified parameter such as file or directory. 

Ex.1: `find ./government/Alcohol_Problems -type f`

```
owner@Owners-MacBook-Pro-2 technical % find ./government/Alcohol_Problems -type f
./government/Alcohol_Problems/Session2-PDF.txt
./government/Alcohol_Problems/Session3-PDF.txt
./government/Alcohol_Problems/DraftRecom-PDF.txt
./government/Alcohol_Problems/Session4-PDF.txt
```
- In this command I used type -f, the -f meaning files, so I wanted to look for all the files in ./government/Alcohol_Problems
- This would be useful when checking if you have all required files within a directory or in general when trying to search for a file within a directory. This could also be used when trying to see if you have all required files to submit for a PA or assignment. 

Ex.2: `find . -type d`

```
owner@Owners-MacBook-Pro-2 technical % find . -type d
.
./government
./government/About_LSC
./government/Env_Prot_Agen
./government/Alcohol_Problems
./government/Gen_Account_Office
./government/Post_Rate_Comm
./government/Media
./plos
./biomed
./911report
```
- Here we are using -type followed by "d" to find all directories within /technical which is also why all the directories within "government" are also showing. 
- This is useful when trying to find all directories within the current directory. I could find this useful when doing a PA/turning it in and making sure I am not missing anything.

Ex.3: `find . -type d -name "A*"`

```
owner@Owners-MacBook-Pro-2 technical % find . -type d -name "A*" 
./government/About_LSC
./government/Alcohol_Problems
```
- This command is a little more specific I used -type d to find a directory but now I used -name to find a specific directory within /technical that starts with "A".

- This is useful when trying to pinpoint a specific directory by its name instead of being shown all the directories within /technical(another directory)
---
## -amin ##
- command finds what was last accessed n minutes ago

Ex.1: `find . -amin -1`  & `find . -amin -10`
```
owner@Owners-MacBook-Pro-2 technical % find . -amin -1 
.
./911report
./911report/chapter-13.5.txt
owner@Owners-MacBook-Pro-2 technical % find . -amin -10
.
./911report
./911report/chapter-13.5.txt
./911report/Extra-chapter.txt
```
- In this example I used both -amin -1 and -amin -10 to have the terminal show what files I accessed within /technical 1 and 10 minutes ago showing 2 different answers. 1 minute ago I accessed chapter-13.3.txt and 10 minutes ago I accessed chapter-13.3.txt and a file I created, Extra-chapter.txt
- This is useful when you want to see your history within a certain file. For example, sometimes when doing a larger PA I forget what file I was coding in so I can use this command to see what I was recently working on. I could also change -amin to -atime and refer to time past 24+ hours.

Ex.2: `find ./911report -type f -name "*13*" -amin -10`
```
owner@Owners-MacBook-Pro-2 technical % find ./911report -type f -name "*13*" -amin -10
./911report/chapter-13.5.txt
```
- This is a far more specific command where I look for files (-type f) within the ./911report, find the name of the file I want to look at which was any file that has the number 13 in it (-name "*13*"), and that it was accessed 10 minutes ago(-amin -10). Following all of this, it showed me chapter-13.5.txt. Notice how it did not mention "Extra-chapter.txt" from my last command because of the -name "*13*" so it was not brought up even if it was accessed within the same time period. 
- I find this useful when trying to be very specific on what files you want to show that you accessed certain minutes ago instead of getting a very general list. 

Ex.3: `find ./government -type d -atime -10`

```
owner@Owners-MacBook-Pro-2 technical % find ./government -type d -atime -10
./government
./government/Media
```
- Before starting, I added a file within the Media directory. This command goes within ./government and checks to see what directory (-type d) within that government directory was accessed within the past 10 minutes.
- This could be useful when wanting to see specifially in what directory you were workin in n-minutes ago. For example, if you forgot what file you were just in but remember within what directory, you can type in this command and how many minutes ago or substitue it with -atime if it was accessed 24+ hours ago.
