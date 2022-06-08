# Command Line Editors - pt. 2

Date: February 2, 2022
Lecture #: 2
Lecture URL: https://youtu.be/HLhza4vZTsI
Notion URL: https://21f1003586.notion.site/Command-Line-Editors-pt-2-258a6a2baeaa4ec59dee72011a8382b6
Type: 📒 Lecture
Week #: 5

### `readlink`

Prints the resolved symbolic links or canonical file names, *but what does that mean?*

If we have file which is a symbolic link to file which in turn is another symbolic link to a file and so on ...

The `readlink` command will display the actual file the initial symbolic link is referring to

**Example usage**

`readlink -f /usr/bin/pico`

***Output***

`/usr/bin/nano`

### `.bashrc`

It is a config file that is read by the bash shell everytime it opens

### `nano`

`nano` is a text editor, example syntax is `nano filename`

It also does syntax highlighting

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled.png)

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%201.png)

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%202.png)

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%203.png)

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%204.png)

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%205.png)

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%206.png)

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%207.png)

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%208.png)

*Source: [https://www.nano-editor.org/dist/latest/cheatsheet.html](https://www.nano-editor.org/dist/latest/cheatsheet.html)*

### Modes in `vi` editor

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%209.png)

`i` will insert the characters from the current position of the cursor

`o` will insert a new line

`a` will append the text

### `vi` help

- **These work only in the Command mode**
    - Press `Esc` to enter this mode
- To exit out of `vi`
    - `:w` → write out
    - `:x` → write out and quit
    - `:wq` → write out and quit
    - `:q` → quit (if write out is over)
    - `:q!` → ignore changes and quit
    - *If nothing else works, cry and smash your keyboard, and then rage quit*

![Untitled](Command%20Line%20Editors%20-%20pt%202%20474c6ba3cddd440b9f4bf5720df235cf/Untitled%2010.png)

### `vi` command mode

- Screen manipulation
    - `Ctrl + F` → Scroll forward one screen
    - `Ctrl + B` → Scroll backward one screen
    - `Ctrl + D` → Scroll down half screen
    - `Ctrl + U` → Scroll up half screen
    - `Ctrl + L` → Redraw screen
    - `Ctrl + R` → Redraw screen removing deleted stuff
- Moving around
    - `0` → Start of the current line
    - `$` → End of the current line
    - `w` → Beginning of the next word
    - `b` → Beginning of the preceding word
    - `:0` → First line in the file
    - `1G` → First line in the file
    - `:n` → n-th line in the file
    - `nG` → n-th line in the file
    - `:$` → Last line in the file
    - `G` → Last line in the file
- Changing text
    - `r` → Replace a single character under the cursor
    - `R` → Replace characters from the cursor till `Esc`
    - `cw` → Change word under the cursor, from the current character till `Esc`
    - `cNw` → Change **N** words, from the current character till `Esc`
    - `C` (CAPITAL C) → Change characters in the current line till `Esc`
    - `cc` (small c) → Change the line till `Esc`
    - `Ncc` → Change the next **N** lines, starting from the current till `Esc`
- Deleting text
    - `x` → Delete a single character under the cursor
    - `Nx` → Delete **N** characters from the cursor
    - `dw` → Delete one word, from the character under the cursor
    - `dNw` → Delete **N** words, from the character under the cursor
    - `D` → Delete the rest of the line, from the character under the cursor
    - `dd` → Delete the current line
    - `Ndd` → Delete the next N lines, starting from the current one
- Copy and Paste text
    - `yy` (small y) → Copy the current line to the buffer
    - `Nyy` → Copy the next N lines, including the current, into the buffer
    - `p` → Paste buffer into the file after the current line
    - `u` → Undo the previous action
- Searching text
    - `/string` → Search forward for the given `string`
    - `?string` → Search backward for the given `string`
    - `n` → Move the cursor to the next occurance of the `string`
    - `N` → Move the cursor to the previous occurrance of the `string`

`:se nu` → Set line numbers

`:se nonu` → Unset the line numbers