# Simple Commands in Linux - 2

Date: December 22, 2021
Lecture #: 1
Lecture URL: https://youtu.be/lpe6AKk5GIk
Notion URL: https://21f1003586.notion.site/Simple-Commands-in-Linux-2-0cd2a51884c14be1a43ad24cd99c6692
Type: 📒 Lecture
Week #: 2

### `ls`

- Short and Long form of options
- Interpretation of directory as an argument
- Recursive listing
- Order of options on command line
    
    `**ls -l` will display the files & folders in the current directly, in a list**
    
    ![VirtualBox_Ubuntu_22_12_2021_18_59_13.png](Simple%20Commands%20in%20Linux%20-%202%20b73350887e6c4417a406db0d184c0a11/VirtualBox_Ubuntu_22_12_2021_18_59_13.png)
    
    *If we add the name of a folder after `ls -l`, it will display the files & folders of that folder*
    

### Commands to work with text files

- `less <file-name>` → To read text files, page-by-page
    - Press `q` to exit
- `cat <file-name>` → To read the entire text file, and dump them on the terminal window
    - Depending on the situation, `less` can be a better way to display the contents of a file on the terminal window rather than `cat`
- `more <file-name>` → Works similarly to `less`
    - View contents of the file page-by-page
- `head <file-name>` → Displays the first 10 lines of a file
    - Takes an optional flag, `-n` followed by an integer to display that number of lines
- `tail <file-name>` → Works the opposite of `head` command
- `wc <file-name>` → Displays the number of lines (or newlines), words and bytes in a file
    - Takes optional flags like `-l` to display only the # of lines

- `which <command>` → A command to locate the commands, *heh*

![fc3.png](Simple%20Commands%20in%20Linux%20-%202%20b73350887e6c4417a406db0d184c0a11/fc3.png)

- `whatis <command>` → Gives a brief description of a command
- `apropos <keyword>` → Takes in the keyword and returns a list of commands that contain the keyword in their name or in their description
    
    ![VirtualBox_Ubuntu_22_12_2021_19_26_27.png](Simple%20Commands%20in%20Linux%20-%202%20b73350887e6c4417a406db0d184c0a11/VirtualBox_Ubuntu_22_12_2021_19_26_27.png)
    
- `help` → Displays the reserved keywords
    - Can pass a command name as optional parameter and it’ll display it’s help
    - Works with `shell keyword`
- `info` → Open a file (which is similar to a webpage) that lists all the commands, and we can move the cursor to any command and press ***Enter*** to get the manual of that command
    - Use the `<` button to go back, how do you press the `<` button? `Shift + ,`
- `type` → Know the type of a command
    
    ![VirtualBox_Ubuntu_22_12_2021_19_34_22.png](Simple%20Commands%20in%20Linux%20-%202%20b73350887e6c4417a406db0d184c0a11/VirtualBox_Ubuntu_22_12_2021_19_34_22.png)
    

**What are aliases?**

Aliases are a nickname given to a command, which may want for our convenience

**How to set an alias?**

```bash
alias <name>='<your-command>'

# Example
alias ll='ls -al'
```

**How to remove an alias?**

```bash
unalias <name>

# Example
unalias ll
```

**OK, How do I know all of my aliases?**

```bash
# Type 'alias' in the bash shell
alias
```

### Multiple arguments

- Second argument
- Interpretation of last argument
- Recursion is assumed for `mv` but not for `cp`

### Links

- Hard links
- Symbolic links
    - It is a bit analogous to desktop shortcuts in Windows

**How to make a symbolic link?**

- The command `ln` is used, with the `-s` flag

```bash
ln -s <source> <destination>
```

***Example***

![VirtualBox_Ubuntu_01_01_2022_12_29_53.png](Simple%20Commands%20in%20Linux%20-%202%20b73350887e6c4417a406db0d184c0a11/VirtualBox_Ubuntu_01_01_2022_12_29_53.png)

**How to create a Hard link?**

Just don’t pass the `-s` flag to the `ln` command

```bash
ln <source> <destination>
```

***Example***

![VirtualBox_Ubuntu_01_01_2022_12_33_24.png](Simple%20Commands%20in%20Linux%20-%202%20b73350887e6c4417a406db0d184c0a11/VirtualBox_Ubuntu_01_01_2022_12_33_24.png)

*Notice the `inode` number for the hardlink is the same as the file*

### Size of files

- `ls -s` lists the files with file sizes
- `stat <file-name>` lists various other details as well as the file size
- `du <file-name>` shows the size of the file
    - Takes an optional `-h` flag to format the output in human readable form

### In-memory filesystem

- `/proc`
- `/sys`

These directories are not stored on your HDD/SSD

They are located in your system memory

These contain the info about the system, so *no `rm -rf`-ing around as `root`*

### A few commands

- `free` → To display the system memory stats, like used memory, free memory
    - Takes an optional `-h` flag to format the output in human readable form
- `df -h` → To know about the partitions, in human readable form