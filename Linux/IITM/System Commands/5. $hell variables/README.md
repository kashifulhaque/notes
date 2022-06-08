# $hell variables

Date: December 22, 2021
Lecture #: 2
Lecture URL: https://youtu.be/pPRge8Yxbso
Notion URL: https://21f1003586.notion.site/hell-variables-7c2117f90cee4aa7aec3ee410038f32a
Type: 📒 Lecture
Week #: 2

### `echo`

`echo` command prints a string or a environment variable

Example:

`echo $HOME`

`echo Hello, World`

### Frequently used shell variables

- `$USERNAME`
- `$HOME`
- `$HOSTNAME`
- `$PWD`
- `$PATH`

### Special shell variables

- `$0` → Name of the shell
- `$$` → Process ID of the shell
- `$?` → Return code of previously run program
- `$-` → Flags set in the bash shell

### Process control

- Use of `&` to run a job in the background
- `fg`
- `coproc`
- `jobs`
- `top`
- `kill`

### Program exit codes

- 0 → success
- 1 → failure
- 2 → misuse
- 126 → command cannot be executed
- 127 → command not found
- 130 → processes killed using `Ctrl + C`
- 137 → processes killed using `kill -9 <pid>`

### Flags set in `bash`

- `h` → locate and hash commands
- `B` → brace expansion enabled
- `i` → interactive mode
- `m` → job control enabled
- `H` → ! style history substitution enabled
- `s` → commands are read from stdin
- `c` → commands are read from arguments

### `echo`

```bash
echo Hello World
echo "How do you do?"
```

*it's a start*

We can enclose the string in quotes as well

Make sure to match the quotes properly

### Some common `echo` commands

```bash
echo $USERNAME
echo $USER
echo $PWD
echo $HOME
echo $HOSTNAME
echo $PATH
```

We can enclose the shell variable (marked as $) in double quotes, and it'll replace the value

***However, if we use single quote around the shell variable, the shell variable is printed as it is***

We can also escape the shell variable by using a backslash in front of it

**Example →** `echo "User is \$USERNAME"` will display `User is $USERNAME`

### To view all the shell variables

```bash
printenv
env
```

`printenv` prints all or part of the environment

```bash
printenv HOME
```

### `set`

`set` allows you to change the values of shell options and set the positional parameters, or to display the names and values of shell variables. ([Source](https://www.gnu.org/software/bash/manual/html_node/The-Set-Builtin.html))

### To escape any aliases set already

```bash
\<alias>

# Example
\ls
\date
```