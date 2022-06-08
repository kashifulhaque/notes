# Simple Commands in Linux - 1

Date: December 22, 2021
Lecture #: 3
Lecture URL: https://youtu.be/DIpBEmRDHnw
Notion URL: https://21f1003586.notion.site/Simple-Commands-in-Linux-1-3e5b2c25e6d04a7499afcb89af041b20
Type: 📒 Lecture
Week #: 1

### Some basic commands

- `date` → Date and time
    
    ![VirtualBox_Ubuntu_22_12_2021_12_05_05.png](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/VirtualBox_Ubuntu_22_12_2021_12_05_05.png)
    
    - `date -R` → Gives the date in RFC5322 standard
- `cal` → Calendar of a month
    
    ![VirtualBox_Ubuntu_22_12_2021_12_06_49.png](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/VirtualBox_Ubuntu_22_12_2021_12_06_49.png)
    
- `free` → Memory statistics
    
    ![VirtualBox_Ubuntu_22_12_2021_12_07_43.png](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/VirtualBox_Ubuntu_22_12_2021_12_07_43.png)
    
    - `free -h` → Makes the output human readable
- `groups` → Groups to which the user belongs
    
    ![VirtualBox_Ubuntu_22_12_2021_12_08_36.png](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/VirtualBox_Ubuntu_22_12_2021_12_08_36.png)
    
    *idk what the junk is this*
    
- `file` → What type of a file it is
    
    ![VirtualBox_Ubuntu_22_12_2021_12_10_01.png](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/VirtualBox_Ubuntu_22_12_2021_12_10_01.png)
    
- `cd -` → To visit the previous directory we were in
    
    ![VirtualBox_Ubuntu_22_12_2021_12_11_27.png](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/VirtualBox_Ubuntu_22_12_2021_12_11_27.png)
    

### Typical output of `ls -l`

![Untitled](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/Untitled.png)

### File types

- `-` → Regular file
- `d` → Directory
- `l` → Symbolic link
- `c` → Character file
- `b` → Block file
- `s` → Socket file
- `p` → Named pipe

### inode (Read: eye node)

`**ls -l <name>**`

- An entry in the filesystem table about the location in storage media

### Permission string

![Untitled](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/Untitled%201.png)

### To modify permissions

- Create a folder
    - `mkdir <folder-name>`
    - `chmod g-w <folder-name>` to remove the write permission from the group
    - Similarly, `chmod g-x <folder-name>` to remove the execute permission from the group
    - To add permission, `chmod g+w <folder-name>` to give write permission to the group
- So, a general structure of permission syntax is something like ...
    - `chmod <user-group><plus/minus><r/w/x> <folder-name/file-name>`
        - Where `<user-group>` are ...
            - `u` → User
            - `g` → Group
            - `o` → Others
        - `<plus/minus>` are ...
            - `-` → To remove permission
            - `+` → To add permission
        - `<r/w/x>` are ...
            - `r` → Read
            - `w` → Write
            - `x` → Execute
- We can also use numerical values for permissions
    - `chmod 700 <folder-name>` to give the `rwx` permission to user only

### `touch` command

- Used to modify the timestamp of a file or folder
    - If a file does not exist, it will be created
- `touch <file-name>` to create a new file
    - `chmod 700 <file-name>` to give `rwx` permission to user only

### `cp` command

- `cp <file-name> <new-name>` to copy a file to a new name
    - `cp <file-name> <new-path>` can be used to copy a file to a new path

### `mv` command

- `mv <file-name> <new-path>` to move a file to a new path
    - `mv <file-name> <new-file-name>` can be used to rename a file

***Also, use quotation marks if the file name includes a space***

### `rm` command

- `rm <file-name>` to remove a file
    - **IT WILL NOT ASK FOR YOUR CONFIRMATION**
        - Just straight up delete
            
            ![8748_gigachad.png](Simple%20Commands%20in%20Linux%20-%201%20c123d340378244d18b6456cdf8352eed/8748_gigachad.png)
            
        - This is the default behaviour
    - We can pass `-i` flag for the confirm remove prompt

### Alias

- We can also set an alias for long commands, for example ...
    - `alias ll="ls -altrhF"`

### Know current user

```bash
whoami
```

### Read a text file, page-by-page

```bash
less <file-name>
```

### To know the type of a file

```bash
file <file-name>
```

### Some commands

- `chmod` → Change permissions of a file
- `touch` → Change modified timestamp of a file
- `cp` → Create a copy of a file
- `mv` → Rename/Move a file
- `mkdir` → Create a directory
- `rm` → Remove a file