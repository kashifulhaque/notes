# Overview of shell scripts

Date: February 2, 2022
Lecture #: 4
Lecture URL: https://youtu.be/YAddHeVpG7I
Notion URL: https://21f1003586.notion.site/Overview-of-shell-scripts-2d85d6d2542f4122b49db652e3913de8
Type: 📒 Lecture
Week #: 5

![Untitled](Overview%20of%20shell%20scripts%20bd7afcb2d7b94680abe29eb2e632521f/Untitled.png)

![Untitled](Overview%20of%20shell%20scripts%20bd7afcb2d7b94680abe29eb2e632521f/Untitled%201.png)

### Script location

- Use absolute path or relative path while executing the script
- Keep the script in the folder listed in `$PATH`
- Watch out for the sequence of directories in `$PATH`

### bash environment

- When you are already logged in to a system and using the GNOME environment to open a terminal, then the shell we are opening is not asking for a login and is called a **Non-login shell**
- When we ssh into a remote machine, then the shell we are logging into would have checked for the login credentials and then opened up the command line environment for us, therefore that shell is called a **Login shell**

![Untitled](Overview%20of%20shell%20scripts%20bd7afcb2d7b94680abe29eb2e632521f/Untitled%202.png)

### Output from the shell scripts

- `echo`
    - Terminates with a newline if `-n` flag is not given
    - `echo My home is $HOME`
- `printf`
    - Supports format specifiers like in C
    - `printf “My home is %s\n” $HOME`

### Input to shell scripts

- `read var`
    - String read from command line is stored in `$var`

### Shell script arguments

`./myscript.sh -l arg2 -v arg4`

- `$0` → name of the shell program
- `$#` → number of arguments passed
- `$1` or `${1}` → first argument
- `${11}` → eleventh argument
- `$*` or `$@` → all arguments at once
- `“$*”` → all arguments as a single string
- `“$@”` → all arguments as separate strings

### Command substitution

```bash
var=`command`
var=$(command)
```

`command` is executed and the output is substituted

Here, the variable `var` will be assigned with that output

### `for do` loop

```bash
for var in list
do
	commands
done
```

`commands` are executed once for each item in the `list`

space is the field delimiters

set IFS if required

### `case` statement

```bash
case var in
pattern1)
	commands
	;;
pattern2)
	commands
	;;
esac
```

`commands` are executed

each pattern matched

for var in the options

### `if` loop

```bash
if condition
then
	commands
fi
```

```bash
if condition; then
	commands
fi
```

`commands` are executed only if `condition` returns true

### `conditions` in `if`

- `test -e file` or any `text expression`
    - True, if the file exists in the current directory of the shell script
    - else False
- `[ -e file ]` or any `[ expression ]`
    - Same as the above one, just a different syntax
- `[[ expression ]]` like `[[ $ver == 5.* ]]`
    - If we intend to use regex or other complex operations
- `(( expression ))` like `(( $v ** 2 > 10 ))`
    - To perform complex arithmetic operations for the test conditions
- Or just use a `command` like `wc -l file`
    - If the command returns True, i.e. upon successful execution, this means the condition is satisfied
    - else False
- `pipeline` like `who | grep "joy" > /dev/null`
    - A set of commands which can be combined with other commands and redirection of output and combination of logical expressions using the `&&` or `||`
    - These can be put as the condition

For negation, use `!` before the condition

### test numeric comparisons

- `$n1 -eq $n2`
    - Check if n1 is equal to n2
- `$n1 -ge $n2`
    - Check if n1 is greater than or equal to n2
- `$n1 -gt $n2`
    - Check if n1 is greater than n2
- `$n1 -le $n2`
    - Check if n1 is less than or equal to n2
- `$n1 -lt $n2`
    - Check if n1 is less than n2
- `$n1 -ne $n2`
    - Check if n1 is not equal to n2

### test string comparisons

- `$str1 = $str2`
    - Check if str1 is the same as str2
- `$str1 != $str2`
    - Check if str1 is not the same as str2
- `$str1 < $str2`
    - Check if str1 is less than str2
    - Compares based on lexicographical (alphabetical) order
- `$str1 > $str2`
    - Check if str1 is greater than str2
    - Compares based on lexicographical (alphabetical) order
- `-n $str1`
    - Check if str1 has length greater than zero
- `-z $str1`
    - Check if str1 has the length zero

### Unary file comparisons

- `-e file`
    - Check if the file exists
- `-d file`
    - Check if the file exists and is a directory
- `-f file`
    - Check if the file exists and is a file
- `-r file`
    - Check if the file exists and is readable
- `-s file`
    - Check if the file exists and is not empty
- `-w file`
    - Check if the file exists and is writable
- `-x file`
    - Check if the file exists and is executable
- `-O file`
    - Check if the file exists and is owned by the current user
- `-G file`
    - Check if the file exists and the default group is the same as that of the current user

### Binary file comparisons

- `file1 -nt file2`
    - Check if file1 is newer than file2
- `file1 -ot file2`
    - Check if file1 is older than file2

### `while do` loop

```bash
while condition
do
	commands
done
```

`commands` are executed only if the `condition` returns `true`

### `until do` loop

```bash
until condition
do
	commands
done
```

`commands` are executed only if the `condition` returns `false`

### functions

definition

```bash
myfunc()
{
	commands
}
```

call

```bash
myfunc
```

`commands` are executed each time `myfunc` is called

Definitions must be before the calls