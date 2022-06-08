# Linux Process Management

Date: December 22, 2021
Lecture #: 3
Lecture URL: https://youtu.be/2aThmDRvSWU
Notion URL: https://21f1003586.notion.site/Linux-Process-Management-d73af14458004045b281f5995be7cf32
Type: 📒 Lecture
Week #: 2

### `sleep` command

- It is a delay for a specified amount of time
    - The time is specified in seconds

***Example***

```bash
# The following command will make the prompt sleep for 5 seconds
sleep 5
```

### Coprocess

- The shell command → `coproc`
- A Coprocess is executed asynchronously in a subshell
    - In simple words, this command is used to run a process without actually losing control of the prompt
    - As we don’t lose prompt access, we can execute other commands

***Usage***

```bash
coproc sleep 20
```

When the above mentioned process is completed, the prompt will output a message saying `Done`

We can run the `ps` command to view the running status of the aforementioned command

### `kill`

- This command is used to kill an already running process
- `*Ctrl + C` is also quite handy*

***Usage***

```bash
kill -9 <PID>
```

***How do I know the PID?***

`ps` command, try `ps --forest` instead

### `&` sign to put a process in the background

- We can also put the `&` (ampersand) sign at the end of a command to put that process in the background

***Usage***

```bash
sleep 30 &
```

***Alright, how do I bring it to the foreground?***

```bash
fg
```

### `jobs`

List the commands that are running in the background

***Example***

![VirtualBox_Ubuntu_01_01_2022_14_51_47.png](Linux%20Process%20Management%207b8847096a9046968319be1962aaf3b6/VirtualBox_Ubuntu_01_01_2022_14_51_47.png)

### `top` command

It’s like your Windows Task Manager, but in the Linux terminal

*To exit out of `top`, press `Q` or `Ctrl + C`*

Pressing `Ctrl + Z` while `top` is open suspends the process, then you can do your work and come back to it by using the `fg` command

`jobs` command will show the top process

***Well, `Ctrl + Z` will suspend any running process***

### $-

```bash
echo $-
```

The output of this shell variable would tell us about the bash shell we are currently using

To know what the output means, type `man bash` and match the flags

### Launch a bash shell which is not interactive

```bash
bash -c "echo \$-"
```

```bash
bash -c "echo \$-; ps --forest;"
```

***To know the PID of the new bash shell we launcher***

```bash
bash -c "echo \$$; echo \$-; ps --forest;"
```

### `history`

The following command displays out all the commands that have been run on the current shell, chronologically

```bash
history
```

The following command will run the `n`-th command that has been run, make sure to put `n` from the list of commands output from the above command

`n` is integer

```bash
!n
```

The following command will run the previous command that was executed on the bash shell

```bash
!!
```

### Brace Expansion

So the output of `echo $-` had a `B` flag, it refers to Brace Expansion

*is this a JJK reference?* ブレース展開

**So, What is a Brace Expansion?**

- Brace expansion is a mechanism by which arbitrary strings may be generated. [Source](https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html)

***Example***

```bash
echo a{b,c,d}e
```

![VirtualBox_Ubuntu_01_01_2022_17_04_52.png](Linux%20Process%20Management%207b8847096a9046968319be1962aaf3b6/VirtualBox_Ubuntu_01_01_2022_17_04_52.png)

```bash
echo {a..z}
```

![VirtualBox_Ubuntu_01_01_2022_17_06_25.png](Linux%20Process%20Management%207b8847096a9046968319be1962aaf3b6/VirtualBox_Ubuntu_01_01_2022_17_06_25.png)

```bash
echo {A..C}{g..k}
```

![VirtualBox_Ubuntu_01_01_2022_17_08_29.png](Linux%20Process%20Management%207b8847096a9046968319be1962aaf3b6/VirtualBox_Ubuntu_01_01_2022_17_08_29.png)

```bash
# The * is a wildcard character, it expands to all the files in the current dir
echo *
```

*Similarly ...*

```bash
# The following command will return all the files folders that start with D
echo D*
```

### Exit codes

- `0` → All good, no error
- `1` → General errors, misc. errors
- `2` → Misuse of shell built-in
- `126` → Command invoked cannot execute
- `127` → Command not found
- `128` → Invalid argument to exit
    - `exit` takes int from `0 - 255`
- `128+n` → Fatal error signal "n"
    - When a process running in another place (like in another shell) was killed from somewhere else (killed from not the same shell)
    - `kill -9 $PPID` → `$?` returns $137 \ (127 + 9)$
- `130` → Script terminated by `Ctrl + C`
- `255*` → Exit status out of range

If the exit code is out of range, bash takes the modulo of the exit code w.r.t. 256

***Example***

```bash
# Create a new bash subshell and exit with the status code 300
bash -c "exit 300"

# Check the exit code
echo $?

# The output will be ...
44
```