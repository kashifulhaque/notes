# Pattern Matching - pt. 1

Date: January 17, 2022
Lecture #: 3
Lecture URL: https://youtu.be/1y85iTaqq8Y
Notion URL: https://21f1003586.notion.site/Pattern-Matching-pt-1-8cb1aa5c0e6c42b2a9b517b040006284
Type: 📒 Lecture
Week #: 4

### Pattern matching

**`regex` & `grep`**

### Regex

- regex is a pattern template to filter text
- BRE: POSIX Basic Regular Expression engine
- ERE: POSIX Extended Regular Expression engine

### Why learn regex?

- Languages: Java, Perl, Python, Ruby, ...
    - To process input from the user
    - To perform string operations
- Tools: `grep`, `sed`, `awk`, ...
- Applications: MySQL, PostgreSQL, ...

### Usage

- `grep ‘pattern’ filename`
- `command | grep ‘pattern’`
- Default engine: BRE
- Switch to use ERE:
    - `egrep ‘pattern’ filename`
    - `grep -E ‘pattern’ filename`

### Special characters (BRE & ERE)

![Untitled](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/Untitled.png)

### Special characters (BRE)

![Untitled](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/Untitled%201.png)

### Special characters (ERE)

![Untitled](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/Untitled%202.png)

### Character classes

![Untitled](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/Untitled%203.png)

*To make it slightly easy to match pattern*

### Backreferences

- `\1` through `\9`
- `\n` matches whatever was matched by the `n`th earlier paranthesized sub-expression
- A line with two occurences of *“hello”* will be matched using: `\(hello\).*\1`

### BRE operator precedence

![Untitled](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/Untitled%204.png)

### ERE operator precedence

![Untitled](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/Untitled%205.png)

### Uses of `grep`

![VirtualBox_Manjaro_18_01_2022_14_45_38.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_14_45_38.png)

### Usage of `.` in the `grep` command

`.` is like a wildcard for a single character

![VirtualBox_Manjaro_18_01_2022_15_09_05.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_15_09_05.png)

`$` is used to denote an anchor

Like a pattern at the end of the line

![VirtualBox_Manjaro_18_01_2022_15_10_59.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_15_10_59.png)

Well what if your name contains a `.`

Then escape it using the `\` character

![VirtualBox_Manjaro_18_01_2022_15_12_57.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_15_12_57.png)

If we want the `.` to be necessarily after a character

![VirtualBox_Manjaro_18_01_2022_15_14_18.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_15_14_18.png)

Match string using anchors at the beginning

ask `grep` to ignore the case by passing in the `-i` flag

![VirtualBox_Manjaro_18_01_2022_15_25_03.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_15_25_03.png)

Match a pattern at the end of the line, a word boundary one might say

`\b` looks for a word boundary, so that pattern could also occur at the end of a word in the middle of a line

`$` looks for line boundary only, so the pattern occurs at the end of the line

![VirtualBox_Manjaro_18_01_2022_15_27_31.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_15_27_31.png)

Usage of square brackets `[]`

Here, the first character in the pattern is followed by either of the 2 characters given in `[]`

In the `grep 'S.*[mn]'` command, it matches from the start of the line

We add `\b` to mark a word boundary just to match it within a word

*Had to switch to* `bash` *to show the formatting*

![VirtualBox_Manjaro_18_01_2022_15_37_18.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_15_37_18.png)

![VirtualBox_Manjaro_18_01_2022_16_05_28.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_16_05_28.png)

The last command in the following screenshot does negation

![VirtualBox_Manjaro_18_01_2022_16_07_40.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_16_07_40.png)

Number of times a character should occur

In the curly braces, we provide the # of times the preceding character should be matched

We can pass one number or a multiple numbers separated by comma for their matching

![VirtualBox_Manjaro_18_01_2022_16_10_29.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_16_10_29.png)

![VirtualBox_Manjaro_18_01_2022_17_18_49.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_17_18_49.png)

![VirtualBox_Manjaro_18_01_2022_18_26_36.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_18_26_36.png)

![VirtualBox_Manjaro_18_01_2022_18_28_40.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_18_28_40.png)

![VirtualBox_Manjaro_18_01_2022_18_30_50.png](Pattern%20Matching%20-%20pt%201%207a1eb6cb734542c7a464c3dd7498ef55/VirtualBox_Manjaro_18_01_2022_18_30_50.png)