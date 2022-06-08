# Command Line Editors - pt. 3

Date: February 2, 2022
Lecture #: 3
Lecture URL: https://youtu.be/w25zlMXshHw
Notion URL: https://21f1003586.notion.site/Command-Line-Editors-pt-3-5452a0b89e32403184ce432b0bfd3b5a
Type: 📒 Lecture
Week #: 5

**To copy a file using secure copy `scp`**

Syntax → `scp <username>@<IP_ADDRESS>:<path/to/file/on/that/machine> <where/to/save>`

Example → `scp gphani@10.17.0.167:Documents/code3d.tar .`

**To untar (extract) a `.tar` file**

Syntax → `tar -xvf filename.tar`

### `emacs`

**C-x means `Ctrl + x`**

**M-x means `Alt + x`**

- Moving around
    - `C-p` → Move up by one line
    - `C-b` → Move left by one character
    - `C-f` → Move right by one character
    - `C-n` → Move down by one line
    - `C-a` → Go to the beginning of the current line
    - `C-e` → Go to the end of the current line
    - `C-v` → Move forward one screen
    - `M-<` → Move to the first line of the file
    - `M-b` → Move left to the previous word
    - `M-f` → Move right to the next word
    - `M->` → Move to the last line of the file
    - `M-a` → Move to the beginning of the current sentence
    - `M-e` → Move to the end of the current sentence
    - `M-v` → Move back one screen

*Source: [https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf](https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf)*

### `emacs` commands

- Exiting `emacs`
    - `C-x C-s` → Save buffer to the file
    - `C-z` → Exit emacs but keep it running
    - `C-x C-c` → Exit emacs and stop it
- Searching a text
    - `C-s` → Search forward
    - `C-r` → Search backward
    - `M-x` → Replace string
- Copy and Paste
    - `M-backspace` → Cut the word before the cursor
    - `M-d` → Cut the word after the cursor
    - `C-k` → Cut from the cursor to the end of the line
    - `M-k` → Cut from the cursor to the end of the sentence
    - `C-y` → Paste the content at the cursor

Syntax for emacs → `emacs -nw filename`

Make sure to pass the `-nw` flag to make it open in terminal mode instead of the GUI