# Command Line Environment

Date: December 22, 2021
Lecture #: 2
Lecture URL: https://youtu.be/qrAnlpcMyYc
Notion URL: https://21f1003586.notion.site/Command-Line-Environment-f96a91e782a147a88894028d7848a2c4
Type: 📒 Lecture
Week #: 1

### Why use Command Line environment?

- To use linux at its max potential
- Combine commands to form powerful scripts
    - To automate using these scripts
- *To assert dominance over GUI plebs*

### Terminal in Ubuntu

![VirtualBox_Ubuntu_22_12_2021_01_46_14.png](Command%20Line%20Environment%2079156f5f5f2744c6942acce27163a034/VirtualBox_Ubuntu_22_12_2021_01_46_14.png)

This is what the default terminal looks like in Ubuntu

### To clear the command line

```bash
clear
```

- or you can press `Ctrl + L` to clear the terminal screen

### To check which directory we currently are in

```bash
pwd
```

By default, you are placed in the home directory of the currently logged in user

### To list all the files and folders in the current directory

```bash
ls
```

### To view the currently running processes

```bash
ps
```

### To know the OS, duh

```bash
uname
```

### To exit the shell

```bash
exit
```

- Or you can also press `Ctrl + D` to exit out of the terminal session

### Anatomy of a typical command on the terminal

![anatomy.png](Command%20Line%20Environment%2079156f5f5f2744c6942acce27163a034/anatomy.png)

- To display all the files, press `ls -a`

![VirtualBox_Ubuntu_22_12_2021_02_00_16.png](Command%20Line%20Environment%2079156f5f5f2744c6942acce27163a034/VirtualBox_Ubuntu_22_12_2021_02_00_16.png)

- To display the files in a list, press `ls -l`

![VirtualBox_Ubuntu_22_12_2021_02_00_16.png](Command%20Line%20Environment%2079156f5f5f2744c6942acce27163a034/VirtualBox_Ubuntu_22_12_2021_02_00_16%201.png)

*These two flags are the most commonly used ones, **we can also combine them as one flag***

*like,* `ls -al`

### To get help on any command

```bash
man <command-name>
```

- For example
    
    ```bash
    man ls
    ```
    
    gives us the manual for the command `ls`
    

### Filesystem in Linux

![filesystem.png](Command%20Line%20Environment%2079156f5f5f2744c6942acce27163a034/filesystem.png)

**Traversing the tree**

`/` is the root of the file system

`/` is also the delimiter for sub-directories

`.` is the current directory

`..` is the parent directory

*Path for traversal can be absolute or relative*

### To change directory

```bash
cd <location>
```

**Examples**

- `cd` without any arguments will take us to the home directory of the currently logged in user
- `cd <folder-name>` will change the move us into the `folder-name`
- `cd ..` will takes us to the parent of the current directory
- `cd /` will takes us to the root directory

### What does this *directory* do?

- `/bin` → Essential command binaries
- `/boot` → Static files for the bootloader
- `/dev` → Device files
- `/etc` → Host specific system configuration
- `/lib` → Essential shared libraries and kernel modules
- `/media` → Mount points for removable devices
- `/mnt` → Mount points
- `/opt` → Add on application software packages
- `/run` → Data relevant to running processes
- `/sbin` → Essential system binaries
- `/srv` → Data for services
- `/tmp` → Temporary files
- `/usr` → Secondary hierarchy
- `/var` → Variable data

### `/usr` hierarchy

- `/usr/bin` → User commands
- `/usr/lib` → Libraries
- `/usr/local` → Local hierarchy
- `/usr/sbin` → Non-vital system binaries
- `/usr/share` → Architecture dependent data
- `/usr/include` → Header files included by C programs
- `/usr/src` → Source code

### `/var` hierarchy

- `/var/cache` → Application cache data
- `/var/lib` → Variable state information
- `/var/local` → Variable data for `/usr/local`
- `/var/lock` → Lock files
- `/var/log` → Log files and directories
- `/var/run` → Data relevant to running processes
- `/var/tmp` → Temporary files preserved between reboots

![Untitled](Command%20Line%20Environment%2079156f5f5f2744c6942acce27163a034/Untitled.png)