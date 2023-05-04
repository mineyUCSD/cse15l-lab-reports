# Lab Report 3

## `find`

**I choose `find`!** 😹

## Command Line Options 

*  `-type`
*  `-cmin`
*  `-exec`
*  `-delete`

## `-type`

`-type` basically allows you to specify what type of file you are searching for

**Example 1: Searching for Directories**

Input

```
$ find ./technical -type d

```

Output

```
./technical
./technical/911report
./technical/biomed
./technical/government
./technical/government/About_LSC
./technical/government/Alcohol_Problems
./technical/government/Env_Prot_Agen
./technical/government/Gen_Account_Office
./technical/government/Media
./technical/government/Post_Rate_Comm
./technical/plos

```

Using `-type d` will find all directories. Identifying all of the directories in `./technical` could be tedious if you are `cd`-ing and `ls`-ing to identify the directories,
so it is handy to use  `-type -d`. Also, just using the command `$ find ./technical` you would not be able to find the directories because of the number of text files
in `./technical`

**Example 2: Searching for files**

Input

```
$ find ./technical/911report/ -type f 

```

Output

```
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
./technical/911report/preface.txt
```
Using `-type f` will find only the files, leaving out directories. Because `./technical/911report/` has no directories, `-type f` appears to have no effect.
I will add some directories to see if the functionality words

Input

```
 $ cd ./technical/911report/ 
 $ mkdir directory1
 $ mkdir directory2
 $ ls
 
 ```
 
 Output
 
 ```
 chapter-1.txt   chapter-12.txt    chapter-13.3.txt  chapter-2.txt  chapter-6.txt  chapter-9.txt  preface.txt
chapter-10.txt  chapter-13.1.txt  chapter-13.4.txt  chapter-3.txt  chapter-7.txt  directory1
chapter-11.txt  chapter-13.2.txt  chapter-13.5.txt  chapter-5.txt  chapter-8.txt  directory2

 ```
 So, I added two directories. Let's try  `-type f` to see if the previous output is unchanged(as added directories should be ignored by `-type f`)
 
 Input
 
 ```

 $ LabReport3:444$ find ./technical/911report/ -type f
 
 ```
 
 Output
 ```
 ./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
./technical/911report/preface.txt
 ```
 Woopdy do! 🤙 The output is the same, the directories were ignored!
 
 ## `-cmin`
 
 `-cmin` allows you to see which files have been changed within some specificed number of minutes. There are other forms, like `ctime` but I like `-cmin` because
 of how it sounds and because I just cloned the `./technical` so all of my changes are rather recent
 
 **Ex 1 : Which files were changed less than 15 minutes ago?**
 
 Input
 
 ```
 $ find ./technical/911report/ -cmin -15

 ```
 
 Output 
 
 ```
 
 ./technical/911report/
./technical/911report/directory1
./technical/911report/directory2
 
 ```
 
So, less than 15 minutes ago, the directory `911report` was changed in the making of the directories `directory1` and `directory2`. That was such a swift way of identifying the changes I made to `./technical/911report/`!
For the syntax of the command, doing `-cmin -15` means that it is less than 15 minutes. If it were instead `-cmin +15` the output would be different....

**Ex 2 Which files were changed more than 15 minutes ago???**

Input

```
find ./technical/911report/ -cmin +15
```

Output

```
./technical/911report/chapter-1.txt
./technical/911report/chapter-10.txt
./technical/911report/chapter-11.txt
./technical/911report/chapter-12.txt
./technical/911report/chapter-13.1.txt
./technical/911report/chapter-13.2.txt
./technical/911report/chapter-13.3.txt
./technical/911report/chapter-13.4.txt
./technical/911report/chapter-13.5.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/911report/chapter-5.txt
./technical/911report/chapter-6.txt
./technical/911report/chapter-7.txt
./technical/911report/chapter-8.txt
./technical/911report/chapter-9.txt
./technical/911report/preface.txt

```

Including the `+` before `15` changed find from looking for less than to looking for more than 15 minutes. It found all of the files, expect for the directories that I added less
than 15 minutes ago. That is because I cloned `./technical` probably an hour ago at this point. I see use in this if you are trying to find files that you were recently
working on that are in a directory, maybe if the directory is a bit cluttered and you cannot find the files you were changing just by scrolling through the list, or possibly you forgot!

## `-exec`

`-exec` is pretty cool as it allows you to execute commands on the files you find with find

**Ex 1 `cat`-ing the files you find!**

Input 

```
$ find ./technical/911report/ -name "preface.txt" -exec cat {} \;
```

Output

```


            PREFACE
            We present the narrative of this report and the recommendations that flow from it to
                the President of the United States, the United States Congress, and the American
                people for their consideration. Ten Commissioners-five Republicans and five
                Democrats chosen by elected leaders from our nation's capital at a time of great
                partisan division-have come together to present this report without dissent.
            We have come together with a unity of purpose because our nation demands it.
                September 11, 2001, was a day of unprecedented shock and suffering in the history of
                the United States. The nation was unprepared. How did this happen, and how can we
                avoid such tragedy again?
            To answer these questions, the Congress and the President created the National
                Commission on Terrorist Attacks Upon the United States (Public Law 107-306, November
                27, 2002).
            Our mandate was sweeping. The law directed us to investigate "facts and circumstances
                relating to the terrorist attacks of September 11, 2001," including those relating
                to intelligence agencies, law enforcement agencies, diplomacy, immigration issues
                and border control, the flow of assets to terrorist organizations, commercial
                aviation, the role of congressional oversight and resource allocation, and other
                areas determined relevant by the Commission. In pursuing our mandate, we have
                reviewed more than 2.5 million pages of documents and interviewed more than 1,200
                individuals in ten countries. This included nearly every senior official from the
                current and previous administrations who had responsibility for topics covered in
                our mandate. We have sought to be independent, impartial, thorough, and nonpartisan.
                From the outset, we have been committed to share as much of our investigation as we
                can with the American people. To that end, we held 19 days of hearings and took
                public testimony from 160 witnesses.
            Our aim has not been to assign individual blame. Our aim has been to provide the
                fullest possible account of the events surrounding 9/11 and to identify lessons
                learned.
            We learned about an enemy who is sophisticated, patient, disciplined, and lethal. The
                enemy rallies broad support in the Arab and Muslim world by demanding redress of
                political grievances, but its hostility toward us and our values is limitless. Its
                purpose is to rid the world of religious and political pluralism, the plebiscite,
                and equal rights for women. It makes no distinction between military and civilian
                targets. Collateral damage is not in its lexicon.
            We learned that the institutions charged with protecting our borders, civil aviation,
                and national security did not understand how grave this threat could be, and did not
                adjust their policies, plans, and practices to deter or defeat it. We learned of
                fault lines within our government-between foreign and domestic intelligence, and
                between and within agencies. We learned of the pervasive problems of managing and
                sharing information across a large and unwieldy government that had been built in a
                different era to confront different dangers.
            At the outset of our work, we said we were looking backward in order to look forward.
                We hope that the terrible losses chronicled in this report can create something
                positive-an America that is safer, stronger, and wiser. That September day, we came
                together as a nation. The test before us is to sustain that unity of purpose and
                meet the challenges now confronting us. We need to design a balanced strategy for
                the long haul, to attack terrorists and prevent their ranks from swelling while at
                the same time protecting our country against future attacks. We have been forced to
                think about the way our government is organized. The massive departments and
                agencies that prevailed in the great struggles of the twentieth century must work
                together in new ways, so that all the instruments of national power can be combined.
                Congress needs dramatic change as well to strengthen oversight and focus
                accountability.
            As we complete our final report, we want to begin by thanking our fellow
                Commissioners, whose dedication to this task has been profound. We have reasoned
                together over every page, and the report has benefited from this remarkable
                dialogue. We want to express our considerable respect for the intellect and judgment
                of our colleagues, as well as our great affection for them.
            We want to thank the Commission staff. The dedicated professional staff, headed by
                Philip Zelikow, has contributed innumerable hours to the completion of this report,
                setting aside other important endeavors to take on this all-consuming assignment.
                They have conducted the exacting investigative work upon which the Commission has
                built. They have given good advice, and faithfully carried out our guidance. They
                have been superb. We thank the Congress and the President. Executive branch agencies
                have searched records and produced a multitude of documents for us. We thank
                officials, past and present, who were generous with their time and provided us with
                insight. The PENTTBOM team at the FBI, the Director's Review Group at the CIA, and
                Inspectors General at the Department of Justice and the CIA provided great
                assistance. We owe a huge debt to their investigative labors, painstaking attention
                to detail, and readiness to share what they have learned. We have built on the work
                of several previous Commissions, and we thank the Congressional Joint Inquiry, whose
                fine work helped us get started. We thank the City of New York for assistance with
                documents and witnesses, and the Government Printing Office and W.W. Norton
                & Company for helping to get this report to the broad public.
            We conclude this list of thanks by coming full circle: We thank the families of 9/11,
                whose persistence and dedication helped create the Commission. They have been with
                us each step of the way, as partners and witnesses. They know better than any of us
                the importance of the work we have undertaken.
            We want to note what we have done, and not done. We have endeavored to provide the
                most complete account we can of the events of September 11, what happened and why.
                This final report is only a summary of what we have done, citing only a fraction of
                the sources we have consulted. But in an event of this scale, touching so many
                issues and organizations, we are conscious of our limits. We have not interviewed
                every knowledgeable person or found every relevant piece of paper. New information
                inevitably will come to light. We present this report as a foundation for a better
                understanding of a landmark in the history of our nation.
            We have listened to scores of overwhelming personal tragedies and astounding acts of
                heroism and bravery. We have examined the staggering impact of the events of 9/11 on
                the American people and their amazing resilience and courage as they fought back. We
                have admired their determination to do their best to prevent another tragedy while
                preparing to respond if it becomes necessary. We emerge from this investigation with
                enormous sympathy for the victims and their loved ones, and with enhanced respect
                for the American people. We recognize the formidable challenges that lie ahead.
            We also approach the task of recommendations with humility. We have made a limited
                number of them. We decided consciously to focus on recommendations we believe to be
                most important, whose implementation can make the greatest difference. We came into
                this process with strong opinions about what would work. All of us have had to
                pause, reflect, and sometimes change our minds as we studied these problems and
                considered the views of others. We hope our report will encourage our fellow
                citizens to study, reflect-and act.
            Thomas H. Kean, chair
            Lee H. Hamilton, vice chair

```

Wow! I was able to `cat` the file I searched for with `find`! It works for every file that is found, but I had to do only one because the output of all of those txt files would
be enourmous, and it is large as it is with just this pleasant preface. The syntax for `-exec` is strange, and I don't have a clue what ` {} \; ` at the end of the
command means, but without it `-exec` errors. Ima try another!

**Ex2 `grep`-ping junk that was found with `find`**

Input

```
find ./technical -name "*.txt" -exec grep "sadness" {} \;

```

Output
```
time tasks in patients that report sadness or depression [
        into sadness showed no improvement in RT when given
        weeping, sadness, irritability, anxiety, and confusion,
          of life, crying spells, sadness, and dislike by others
          of intense situational sadness and anxiety accompanied by
        happiness, sadness, or anger, gave the audience insight into the variety of subtle
        melted into melancholy, sadness into ennui. “It's not about moving,” he observed, “it's
```

*Beautiful* 😢 I didn't think that `grep` and `find` could write poetry! Well... The command basically looks through all of the text files in `./technical` and then
`greps` each line and prints it out if it contains `sadness`. The `-exec` command allows for this synergy/marriage situation, and the capabilities of this command seem
considerably substantial.

## `-delete`

`-delete` is dangerous destruction. I must be wary as I use this command. It will delete whatever `find` finds, assuming it has permission. And I think assuming it is an empty directory?
I normally use `rm -r


 
 
 
