# Command Line Editors - pt. 1

Date: February 2, 2022
Lecture #: 1
Lecture URL: https://youtu.be/NIIZ1cgrO7g
Notion URL: https://21f1003586.notion.site/Command-Line-Editors-pt-1-d1e3cf98aed64ed78a8e621b73e43636
Type: 📒 Lecture
Week #: 5

### Command line editors

Working with text files in the terminal

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled.png)

### Features

- Scrolling, view modes, current position in the file
- Navigation (char, word, line, pattern)
- Insert, Replace, Delete
- Cut-Copy-Paste
- Search-Replace
- Language-aware syntax highlighting
- Key-maps, init scripts, macros
- Plugins

### `ed`

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%201.png)

*Command Format* → `[starting-address[,ending-address]command[command-parameters]]`

**To locate the cursor on any particular line of the file ...**

*We can use the line number itself*

- press **2** → in the 2nd line of the text file
- press **. (dot)** → referring to the current line the cursor is
- press **$** → refers to the last line
- press **%** → refers to all the lines, i.e. any action we are doing applies to all the lines
- press **+** → line after the cursor
- press **- (minus sign)** → line before the cursor
- press **, (comma)** → represent the entire buffer, i.e. the whole file
- press **; (semicolon)** → refers the end of the text file from the current position
- **`/RE/`** → To match a specific Regular Expression in the file

### A way to invoke the `ed` editor

`ed file.txt`

and it shows the number of bytes in the file, instead of the contents of the file ... *ayo wut*

![Daco_874128.png](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Daco_874128.png)

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%202.png)

**Run a bash command, read the bash command’s output and write it to the file**

![VirtualBox_Manjaro_01_02_2022_21_03_18.png](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/VirtualBox_Manjaro_01_02_2022_21_03_18.png)

**Delete the last line of the file and write the changes to the file**

![VirtualBox_Manjaro_01_02_2022_21_06_07.png](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/VirtualBox_Manjaro_01_02_2022_21_06_07.png)

**Append a line to the file (press . then enter to exit)**

![VirtualBox_Manjaro_01_02_2022_21_25_40.png](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/VirtualBox_Manjaro_01_02_2022_21_25_40.png)

**Search and Replace**

![VirtualBox_Manjaro_01_02_2022_21_28_17.png](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/VirtualBox_Manjaro_01_02_2022_21_28_17.png)

**File name**

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%203.png)

**Print the current line**

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%204.png)

**Append to the current line**

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%205.png)

**Join line 5 and 6 (The command is `5,6j`)**

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%206.png)

**Move the current line after the given line #** (*We are moving the current line below line 1 here*)

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%207.png)

**Undo the previous operation**

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%208.png)

**Add a prefix to all the lines and then modify the prefix on some lines**

![VirtualBox_Manjaro_01_02_2022_22_05_55.png](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/VirtualBox_Manjaro_01_02_2022_22_05_55.png)

### `ed/ex` commands

![Untitled](Command%20Line%20Editors%20-%20pt%201%207af2ba62627b4c6ca5fd660e8b113e62/Untitled%209.png)