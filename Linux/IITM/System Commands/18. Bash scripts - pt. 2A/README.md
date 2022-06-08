# Bash scripts - pt. 2A

Date: February 9, 2022
Lecture #: 1
Lecture URL: https://youtu.be/8YmNovNo6NE
Notion URL: https://21f1003586.notion.site/Bash-scripts-pt-2A-f7361a999fa344499488a73d6db381b1
Type: 📒 Lecture
Week #: 6

### Debugging

```bash
set -x
./myscript.sh
```

Prints the command before executing it

Place the `set -x` inside the script

`bash -x ./myscript.sh`

### Combining conditions

`[ $a -gt 3 ] && [ $a -lt 7 ]`

`[ $a -le 3 ] || [ $a -ge 7 ]`

### Shell arithmetic

![Untitled](Bash%20scripts%20-%20pt%202A%20b91ef3e7d7f143b7811e5866a1a48192/Untitled.png)

### `expr` command operators

![Untitled](Bash%20scripts%20-%20pt%202A%20b91ef3e7d7f143b7811e5866a1a48192/Untitled%201.png)

![Untitled](Bash%20scripts%20-%20pt%202A%20b91ef3e7d7f143b7811e5866a1a48192/Untitled%202.png)

```bash
#!/bin/bash

if [ $# -lt 2 ]; then
	echo "Use 2 natural numbers as arguments";
	exit 1;
fi;

regex='^[0-9]+$'
if ! [[ $1 =~ $regex ]]; then
    echo "$1 is not a natural number";
    exit 1;
fi;

if ! [[ $2 =~ $regex ]]; then
    echo "$2 is not a natural number";
    exit 1;
fi;

let a=$1*$2;
echo "Product a is $a";
(( a++ ));
echo "Product a incremented is $a";

let b=$1**$2;
echo "Power is $b";

c=$[ $1 + $2 + 10 ];
echo "sum + 10 is $c";

d=$(expr $1 + $2 + 20);
echo "sum + 20 is $d";

f=$(( $1 * $2 * 2 ));
echo "Product times 2 is $f";
```

```bash
#!/bin/bash
# The following line is for debugging
# set -x;

# Code starts here
a=256;
b=4;
c=3;

ans=$( expr $a + $b );
echo $ans;

ans=$( expr $a - $b );
echo $ans;

ans=$( expr $a \* $b );
echo $ans;

ans=$( expr $a / $b );
echo $ans;

ans=$( expr $a % $c );
echo $ans;

ans=$( expr $a \> $b );
echo $ans;

ans=$( expr $a \>= $b );
echo $ans;

ans=$( expr $a \< $b );
echo $ans;

ans=$( expr $a \<= $b );
echo $ans;

ans=$( expr $a = $b );
echo $ans;

ans=$( expr $a != $b );
echo $ans;

ans=$( expr $a \| $b );
echo $ans;

ans=$( expr $a \& $b );
echo $ans;

str="octavio version as in Jan 2022 is 6.4.0";
reg="[oO]ctav[aeiou]*";
ans=$( expr "$str" : $reg );
echo $ans;

ans=$( expr substr "$str" 1 6 );
echo $ans;

ans=$( expr index "$str" "vw" );
echo $ans;

ans=$( expr length "$str" );
echo $ans;
```

### `heredoc` feature

When writing shell scripts you may be in a situation where you need to pass a multiline block of text or code to an interactive command, such as `tee`, `cat`, or `sftp`

In `bash` and other shells like `zsh`, a Here document (`heredoc`) is a type of redirection that allows you to pass multiple lines of input to a command.

This is what a general syntax looks like

```bash
[COMMAND] <<[-] 'DELIMITER'
  HERE-DOCUMENT
DELIMITER
```

![Untitled](Bash%20scripts%20-%20pt%202A%20b91ef3e7d7f143b7811e5866a1a48192/Untitled%203.png)

*Notice no-indent (left) vs indentation (right) in the above example*

```bash
#!/bin/bash

# set -x;
echo "path is set as $PATH";
i=0;
IFS=:;

for n in $PATH; do
    echo "$i $n";
    (( i++ ));
done;
```