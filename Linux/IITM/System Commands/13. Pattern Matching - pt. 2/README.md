# Pattern Matching - pt. 2

Date: January 17, 2022
Lecture #: 4
Lecture URL: https://youtu.be/XQUJPRc-7zA
Notion URL: https://21f1003586.notion.site/Pattern-Matching-pt-2-18da9c08be534558ad86e28d07cba0bd
Type: 📒 Lecture
Week #: 4

Match package names that are 4 characters long

`dpkg-query -W -f='${Section} ${binary:Package}\n' | egrep ' .{4}$'`

Match package names that are 3 characters long and start with the letter `g`

`dpkg-query -W -f='${Section} ${binary:Package}\n' | egrep ' g.{3}$'`

Match package names that are between 1 to 5 characters long and start with the letter `g`

`dpkg-query -W -f='${Section} ${binary:Package}\n' | egrep ' g.{1,5}$'`

Match package names that are from the `math` category

`dpkg-query -W -f='${Section} ${binary:Package}\n' | egrep '^math'`

*make sure to use the* `^` *(hat) character in the front of the regex pattern to match the* `math` *category, otherwise it will match package category and the names*

Match package names that from [KDE](https://kde.org/)

`dpkg-query -W -f='${Section} ${binary:Package}\n' | egrep ' kd.*$'`

To skip empty lines from a file

`cat filename.txt | egrep -v ‘^$’`

---

- Pick any 12 digit or more number from a text file
    - `egrep ‘[[:digit:]]{12}’ filename.txt`
- Pick any 6 digit or more number from a text file
    - `egrep ‘[[:digit:]]{6}’ filename.txt`

*But, there is one problem, if there is any number that is more than 12 digits or more than 6 digits respectively, it will pick that up too*

- Pick an exactly 6 digit number from a text file
    - Add a word boundary `\b`
    - `egrep ‘\b[[:digit:]]{6}\b’ filename.txt`
- Pick a roll number (of the type MM22B001) from a text file
    - `egrep ‘\b[[:alpha:]]{2}[[:digit:]]{2}[[:alpha:]][[:digit:]]{3}\b’ filename.txt`
- Pick a URL from a text file (like [github.com](http://github.com) or [https://www.iitm.ac.in](https://www.iitm.ac.in))
    - `egrep ‘\b[[:alnum:]]+\.[[:alnum:]]+\b’ filename.txt`

### `cut`

A command used to cut lines from files

*does horizontal trimming*

***A sample file*** `fields.txt`

```
1234;hello world,line-1
234567;welcome cmdline,line-2
3456;parse text,line-3
```

- Cut first 4 characters from the beginning of the lines
    - `cut -c 1-4 fields.txt`
- Cut the next 4 characters from the previous
    - `cut -c 5-8 fields.txt`
- We can skip the beginning or the ending of the substring parameter, *it works like python*
    - Cut 4 chars from the beginning
        - `cut -c -4 fields.txt`
    - Cut from 8th char to the end
        - `cut -c 8- fields.txt`
- Use space as the delimiter and print the first field
    - `cat fields.txt | cut -d “ ” -f 1`
- Similarly, print the second field
    - `cat fields.txt | cut -d “ ” -f 2`
- If we want both fields
    - `cat fields.txt | cut -d “ ” -f 1-2`
- Delimit at a semi-colon `;` and get the first field
    - `cat fields.txt | cut -d “;” -f 1`
- Similarly, get the 2nd field
    - `cat fields.txt | cut -d “;” -f 2`
- We can pipe multiple commands
    - To get the part of the line between `;` and `,`
        - `cat fields.txt | cut -d “;” -f 2 | cut -d “,” -f 1`
    - To do the same thing using `grep` (*similar thing, not exactly the same*)
        - `cat fields.txt | egrep ‘;.*,’`
- To get the part `welcome cmdline` from the file `fields.txt`
    - `cat fields.txt | cut -d “;” -f 2 | cut -d “,” -f 1 | head -n 2 | tail -n 1`