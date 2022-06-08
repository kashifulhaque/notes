# Redirections

Date: January 9, 2022
Lecture #: 2
Lecture URL: https://youtu.be/BBh69kH_G_Y
Notion URL: https://21f1003586.notion.site/Redirections-734673f36f21448f99de25ccb092c8d4
Type: 📒 Lecture
Week #: 3

### `command 2> file1`

- Redirect the output of the `command` to `stdout`, which is the display in this case
- Redirect the error of the `command` to `file1`

![Untitled](Redirections%202e485d9043af4316b13b2056a472c002/Untitled.png)

---

### `command > file1 2> file2`

- Redirect the output of the `command` to the `stdout`, i.e. `file1`
- Redirect the error of the `command` to `stderr`, i.e. `file2`

![Untitled](Redirections%202e485d9043af4316b13b2056a472c002/Untitled%201.png)

---

### `command < file1`

- Any `command` which takes input from the keyboard, now takes input from `file1`

![Untitled](Redirections%202e485d9043af4316b13b2056a472c002/Untitled%202.png)

---

### `command > file1 2>&1`

- The output of `command` is written to `file1`
- The error is redirected to stream 1, which is `stdout`

![Untitled](Redirections%202e485d9043af4316b13b2056a472c002/Untitled%203.png)

---

### `command1 | command2` → pipe operator `|`

- The output of `command1` is sent to `command2` as input
- By default, the `stderr` will output to the display

![Untitled](Redirections%202e485d9043af4316b13b2056a472c002/Untitled%204.png)

**Count the number of files in the directory `/usr/bin`**

![VirtualBox_Ubuntu_10_01_2022_22_26_26.png](Redirections%202e485d9043af4316b13b2056a472c002/VirtualBox_Ubuntu_10_01_2022_22_26_26.png)

**List the files of `/usr/bin` directory, but use the `less` command to scroll at ease**

`ls /usr/bin | less`

---

### `command1 | command2 > file1`

- The `stdout` of `command1` is mapped to `stdin` of `command2`
- The `stdout` of `command2` is written to `file1`
- The `stderr` is output to the display

![Untitled](Redirections%202e485d9043af4316b13b2056a472c002/Untitled%205.png)

---

### `/dev/null`

- A sink for output to be discarded
- Use → silent and clean scripts

So, a typical usage looks like ...

### `command > file1 2> /dev/null`

- The output of `command` is written to `file1`
- The `stderr` is written to `/dev/null`, *~~which gets warped to another dimension~~*

![Untitled](Redirections%202e485d9043af4316b13b2056a472c002/Untitled%206.png)

---

### `command1 | tee file1`

- The `tee` command splits the output into 2 streams, one stream is written to the `file1` another, one to the display
    - This command can write to multiple files as well

![Untitled](Redirections%202e485d9043af4316b13b2056a472c002/Untitled%207.png)

---

### `diff` command

- This command compares files line-by-line

***Usage***

`diff file1 file2`