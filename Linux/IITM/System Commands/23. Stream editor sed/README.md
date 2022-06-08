# Stream editor sed

Date: February 20, 2022
Lecture #: 1
Lecture URL: https://youtu.be/uCJjZ3cbaAw
Notion URL: https://21f1003586.notion.site/Stream-editor-sed-4d1c90712d98497a9bd56a4dd192e134
Type: 📒 Lecture
Week #: 7

### `sed`

It is a language for processing text streams

### Introduction

- It is a programming language
- `sed` is an abbreviation of **s**tream **ed**itor
- It is a part of POSIX
- `sed` precedes `awk`

### Execution Model

- Input stream is a set of lines
- Each line is a sequence of characters
- Two data buffers are maintained → active ***pattern*** space and auxiliary ***hold*** space
- For each line of input, an execution cycle is performed loading the line into the pattern space
- During each cycle, all the statements in the script are executed in the sequence for matching address pattern for actions specified with the options provided

### Usage

- Single line at the command line
    
    `sed -e ‘s/hello/world/g’ input.txt`
    
- Script interpreted by sed
    
    `sed -f ./myscript.sed input.txt`
    
    Where `myscript.sed` could be ...
    
    ```bash
    #!/usr/bin/sed -f
    2,8s/hello/world/g
    ```
    

### `sed` statements

![photo.png](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/photo.png)

### Grouping commands

`{ cmd; cmd; }`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled.png)

- `5` → select the 5th line
- `$` → select the last line
- `%` → select all the lines
- `1~3` → starting from the 1st line, select every 3rd line
- `/regex/` → select the line by matching the regular expression
- `/regex1/, /regex2/` → from the line of the 1st occurrence of `regex1` to the line of the 1st occurrence of `regex2`
- `/regex/, +4` → action has to be taken on the next 4 lines, starting from the first match of `regex`
- `/regex/, ~2` → the line where the 1st regular expression is matched, the next line which is a multiple of 2 will be matched
- `5, 15` → execute from the 5th line to 15th line
- `5, /regex/` → from the 5th line till the first occurrence of `regex`

### actions

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%201.png)

### programming

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%202.png)

### `bash` + `sed`

- Including sed inside shell script
- heredoc feature
- Use with other shell scripts on the command line using pipe

---

### Examples

`sample.txt`

```
L1 Linux is a free, opensource, secure and reliable os
L2 text editing: vim or emacs in place of notepad
L3 text processing: latex, libreoffice write in place of microsoft word
L4 spreadsheet: libreoffice calc in place of microsoft excel
L5 slides: libreoffice impress in place of microsoft powerpoint
L6 image processing: gimp, inkscape, imagej in place of adobe photoshop
L7 browsing: mozilla firefox in place of microsoft edge
L8 email: mozilla thunderbird in place of microsoft outlook
L9 symbolic math: sympy, sagemath in place of maple, mathematica
L10 array math: octave, numpy scilab in place of matlab
L11 literature: jabref, calibre in place of mendeley
L12 video editing: kdenlive in place of camtasia
L13 screen recording: obs in place of camtasia
L14 fetch files: wget, curl
L15 security: ufw, netstat, nmap
```

Default action is to print

`sed -e “” sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%203.png)

The above command takes an optional `-n` flag to negate whatever command we give to `sed`

Suppress automatic printing of pattern space

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%204.png)

---

Print every line with it’s line number

`sed -e “=” sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%205.png)

Print the 5th line, and don’t print anything else by default

`sed -n -e “5p” sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%206.png)

If we use `sed -e “5p” sample.txt`, line #5 will be printed twice

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%207.png)

We can also replace the double quotes with single quotes

We also use single quotes when we don’t want the shell to interpret certain special characters

---

Print every line except line #5

`sed -n -e ‘5!p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%208.png)

To print the last line

`sed -n -e ‘$p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%209.png)

To print all lines except the last line

`sed -n -e ‘$!p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2010.png)

Print line #5 to line #8

`sed -n -e ‘5,8p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2011.png)

Now, combine two commands

`sed -n -e ‘=; 5,8p’ sample.txt`

Print the line numbers, and print the lines from 5 to 8

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2012.png)

If we don’t want those blank line numbers to show up, we write the following command

`sed -n -e ‘5,8{=;p}’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2013.png)

Print every odd line (or starting from line #1, print every 2nd line)

`sed -n -e ‘1~2p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2014.png)

Similarly, print every 3rd line starting from line #1

`sed -n -e ‘1~3p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2015.png)

Negate the above command

`sed -n -e ‘1~3!p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2016.png)

Print the lines that contain the following regex pattern (here, in this case, it is a phrase)

`sed -n -e ‘/microsoft/p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2017.png)

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2018.png)

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2019.png)

---

Print n number of lines after the matching regex pattern

`sed -n -e ‘/adobe/,+2p’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2020.png)

---

Delete a line (line #5 in this case) and print the remaining lines

`sed -e ‘5d’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2021.png)

Delete a range of lines (and print the remaining lines, *duh*)

`sed -e ‘5,8d’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2022.png)

Delete the first line

`sed -e ‘1d’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2023.png)

Delete the last line

`sed -e ‘$d’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2024.png)

---

Delete the lines with the following regex pattern

`sed -e ‘/microsoft/d’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2025.png)

Search and replace the first regex with the second regex pattern on all lines

`sed -e ‘s/microsoft/MICROSOFT/g’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2026.png)

Search and replace the first regex with the second one on line #1

`sed -e ‘1s/linux/LINUX/g’ sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2027.png)

`sed -e '1,$s/in place of/in lieu of/g' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2028.png)

Print the lines without the first few characters at the beginning of each line

(Here, we are removing it from line #3 to line #6)

`sed -E -e '3,6s/^L[[:digit:]]+ //g' sample.txt`

Takes in an optional flag `-E` to let `sed` know that we're using the extended regex engine

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2029.png)

To apply the above command to all the lines

`sed -E -e 's/^L[[:digit:]]+ //g' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2030.png)

Remove line numbers from line #3 to the line till it encounters a regex pattern

`sed -E -e '3,/symbolic/s/^L[[:digit:]]+ //g' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2031.png)

Remove the line numbers starting from line #1 and do it every 3rd line

`sed -E -e '1~3s/^L[[:digit:]]+ //g' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2032.png)

Similarly, do the opposite of remove line numbers starting from line #1 and doing it every 2nd line

`sed -E -e '1~2!s/^L[[:digit:]]+ //g' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2033.png)

Remove the line numbers starting from a line having a regex pattern to a line having another regex pattern

`sed -E -e '/text/,/video/s/^L[[:digit:]]+ //g' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2034.png)

---

Insert a line at line #1

Syntax within single quotes: `<position>i <text-to-insert>`

`sed -e '1i ---------------- header ----------------' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2035.png)

Similarly, to insert header and append footer in a single line ...

Syntax to append a footer: `$a <text-to-append>`

`sed -e '1i ---------------- header ----------------' -e '$a ---------------- footer ----------------' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2036.png)

So, it seems like that `i` inserts before the mentioned line and `a` appends after the line

Insert a line before line #4 and append a line after line #8 in the same syntax

`sed -e '4i -------- header --------' -e '8a -------- footer --------' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2037.png)

Similarly, we can do this insert and append using regex patterns instead of line numbers

`sed -e '/microsoft/i ---- WATCHOUT ----' -e '/in place of/a ---- ALTERNATIVE ----' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2038.png)

Insert a line of text starting at line #1 and every 5 lines

`sed -e '1~5i ------ BREAK ------' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2039.png)

---

Replace any line with a matching regex pattern with another line

`sed -e '/microsoft/c ------ CENSORED ------' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2040.png)

Replace line #1 and every 3rd line after that with another line

`sed -e '1~3c ------ CENSORED ------' sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2041.png)

### `sed` commands from a file

`hf.sed`

```bash
#!/usr/bin/sed -f
1i ------ HEADER ------
$a ------ FOOTER ------
1,5s/in place of/in lieu of/g
6i --- SIMPLER STUFF FROM HERE ONWARDS ---
6,$s/in place of.*//g
```

To run the above sed file

`sed -f hf.sed sample.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2042.png)

To clean up the input file we used previously in `awk`

`block-ex6.input`

```
This file contains comments and numbers
Lines containing roll number and the fee paid need to be picked up
mm22b901  21000
Sum of the total fee paid needs to be printed at the end
Also a list of students, who paid how much
mm22b902 21000
Input text may contain some commends in between
mm22b906      21800
mm22b903 21500 paid through DD
mm22b905   22000
updated as on Jan 26, 2022 by Phani
```

`sed` script

`clean.sed`

```bash
/[[:alpha:]]{2}[[:digit:]]{2}[[:alpha:]][[:digit:]]+/!d
s/[ ]+/ /g
s/ ([[:digit:]]+).*/ \1/g
```

After we run the `sed` script on `block-ex6.input`

`sed -E -f clean.sed block-ex6.input`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2043.png)

---

To join lines using `sed`

Joining lines requires `sed` to read one more line into the buffer

And this is achieved in a limited number of commands

`sed` **commands can be constructed as loops and can perform complicated actions**

Input file: `sample-split.txt`

```
L1 linux is a \ free, opensource, secure and reliable os
L2 text editing: vim or emacs in place of notepad
L3 text processing: latex, libreoffice writer \
in place of microsoft word
L4 spreadsheet: libreoffice calc in place of microsoft excel
L5 slides: libreoffice impress in place\
of microsoft \
powerpoint
L6 image processing: gimp, inkscape, imagej in place of\
adobe photoshop
L7 browsing: mozilla firefox in place of microsoft edge
L8 email: mozilla thunderbird in place of microsoft outlook
L9 symbolic math: sympy, sagemath in place of maple,\
mathematica
L10 array math: octave, numpy scilab in place of matlab
L11 literature: jabref, calibre in place of mendeley
L12 video editing: kdenlive in place of camtasia
L13 screen recording: obs in place of camtasia
L14 fetch files: wget, curl
L15 security: ufw, netstat, nmap
```

Join the lines that are ending in a backslash

`join.sed`

```bash
#!/usr/bin/sed -f
:x /\\$/N
/\\/s/\\\n//g
/\\$/bx
```

This is a loop (*ayo wut*)

Every line of the above `sed` file will be executed for every single that is read into the buffer from the input file

colon `:` indicates a label, and it is ignored while execution, it is used for branching

**First line →** Whenever there is a `\` followed by the end of the line, it will read the next line in the buffer, it's basically like joining the line following the one whic is being processed

**Second line →** On the lines which have `\` if there's a `\n` character after the `\` it will be replaced with null, basically to remove the `\` character

**Third line →** Those lines which contain `\` at the end of the line, we branch to the first line and repeat the steps again

When do we not branch and go on to the next cycle? It is when the line doesn't contain `\` at the end of the line, which means that a recursive action is performed

This recursive loop can go infinite if not designed properly

---

To run the above `sed` file on `sample-split.txt`

`sed -f join.sed sample-split.txt`

![Untitled](Stream%20editor%20sed%2070c5dd4969804582b45002c53607494d/Untitled%2044.png)

There is an optional `--debug` flag that can be passed with the `sed` command

and it will display a plethora of information

Command: `sed --debug -f join.sed sample-split.txt`

Output:

```bash
SED PROGRAM:
  :x
  /\\\\$/ N
  /\\\\/ s/\\\\\n//g
  /\\\\$/ b x
INPUT:   'sample-split.txt' line 1
PATTERN: L1 linux is a \\ free, opensource, secure and reliable os
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
PATTERN: L1 linux is a \\ free, opensource, secure and reliable os
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L1 linux is a \ free, opensource, secure and reliable os
INPUT:   'sample-split.txt' line 2
PATTERN: L2 text editing: vim or emacs in place of notepad
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L2 text editing: vim or emacs in place of notepad
INPUT:   'sample-split.txt' line 3
PATTERN: L3 text processing: latex, libreoffice writer \\
COMMAND: :x
COMMAND: /\\\\$/ N
PATTERN: L3 text processing: latex, libreoffice writer \\\nin place of microsoft word
COMMAND: /\\\\/ s/\\\\\n//g
MATCHED REGEX REGISTERS
  regex[0] = 46-48 '\
'
PATTERN: L3 text processing: latex, libreoffice writer in place of microsoft word    
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L3 text processing: latex, libreoffice writer in place of microsoft word
INPUT:   'sample-split.txt' line 5
PATTERN: L4 spreadsheet: libreoffice calc in place of microsoft excel
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L4 spreadsheet: libreoffice calc in place of microsoft excel
INPUT:   'sample-split.txt' line 6
PATTERN: L5 slides: libreoffice impress in place\\
COMMAND: :x
COMMAND: /\\\\$/ N
PATTERN: L5 slides: libreoffice impress in place\\\nof microsoft \\
COMMAND: /\\\\/ s/\\\\\n//g
MATCHED REGEX REGISTERS
  regex[0] = 39-41 '\
'
PATTERN: L5 slides: libreoffice impress in placeof microsoft \\
COMMAND: /\\\\$/ b x
COMMAND: :x
COMMAND: /\\\\$/ N
PATTERN: L5 slides: libreoffice impress in placeof microsoft \\\npowerpoint
COMMAND: /\\\\/ s/\\\\\n//g
MATCHED REGEX REGISTERS
  regex[0] = 52-54 '\
'
PATTERN: L5 slides: libreoffice impress in placeof microsoft powerpoint
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L5 slides: libreoffice impress in placeof microsoft powerpoint
INPUT:   'sample-split.txt' line 9
PATTERN: L6 image processing: gimp, inkscape, imagej in place of\\
COMMAND: :x
COMMAND: /\\\\$/ N
PATTERN: L6 image processing: gimp, inkscape, imagej in place of\\\nadobe photoshop
COMMAND: /\\\\/ s/\\\\\n//g
MATCHED REGEX REGISTERS
  regex[0] = 55-57 '\
'
PATTERN: L6 image processing: gimp, inkscape, imagej in place ofadobe photoshop
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L6 image processing: gimp, inkscape, imagej in place ofadobe photoshop
INPUT:   'sample-split.txt' line 11
PATTERN: L7 browsing: mozilla firefox in place of microsoft edge
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L7 browsing: mozilla firefox in place of microsoft edge
INPUT:   'sample-split.txt' line 12
PATTERN: L8 email: mozilla thunderbird in place of microsoft outlook
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L8 email: mozilla thunderbird in place of microsoft outlook
INPUT:   'sample-split.txt' line 13
PATTERN: L9 symbolic math: sympy, sagemath in place of maple,\\
COMMAND: :x
COMMAND: /\\\\$/ N
PATTERN: L9 symbolic math: sympy, sagemath in place of maple,\\\nmathematica
COMMAND: /\\\\/ s/\\\\\n//g
MATCHED REGEX REGISTERS
  regex[0] = 52-54 '\
'
PATTERN: L9 symbolic math: sympy, sagemath in place of maple,mathematica
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L9 symbolic math: sympy, sagemath in place of maple,mathematica
INPUT:   'sample-split.txt' line 15
PATTERN: L10 array math: octave, numpy scilab in place of matlab
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L10 array math: octave, numpy scilab in place of matlab
INPUT:   'sample-split.txt' line 16
PATTERN: L11 literature: jabref, calibre in place of mendeley
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L11 literature: jabref, calibre in place of mendeley
INPUT:   'sample-split.txt' line 17
PATTERN: L12 video editing: kdenlive in place of camtasia
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L12 video editing: kdenlive in place of camtasia
INPUT:   'sample-split.txt' line 18
PATTERN: L13 screen recording: obs in place of camtasia
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L13 screen recording: obs in place of camtasia
INPUT:   'sample-split.txt' line 19
PATTERN: L14 fetch files: wget, curl
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L14 fetch files: wget, curl
INPUT:   'sample-split.txt' line 20
PATTERN: L15 security: ufw, netstat, nmap
COMMAND: :x
COMMAND: /\\\\$/ N
COMMAND: /\\\\/ s/\\\\\n//g
COMMAND: /\\\\$/ b x
END-OF-CYCLE:
L15 security: ufw, netstat, nmap
```